---
title: DataSet に対する XPath クエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 6082a171d24c55ea52c153bbd920bb7486be78a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784373"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>DataSet に対する XPath クエリの実行
同期<xref:System.Data.DataSet>されたと<xref:System.Xml.XmlDataDocument>の間のリレーションシップにより、 **XmlDataDocument**にアクセスする xml パス言語 (XPath) クエリなどの xml サービスを使用できるようになり、特定の機能をより簡単に実行できるようになります。**データセット**への直接アクセス。 たとえば<xref:System.Data.DataTable> 、の**Select**メソッドを使用して**データセット**内の他のテーブルとの間でリレーションシップを移動するのではなく、**データセット**と同期されている**XmlDataDocument**に対して XPath クエリを実行することで、の形式の XML 要素のリスト<xref:System.Xml.XmlNodeList>。 ノードとし<xref:System.Xml.XmlElement>てキャストされた**xmlnodelist**のノードを**XmlDataDocument**の**getrowfromelement**メソッドに渡して、同期<xref:System.Data.DataRow> **された内のテーブルの行に一致する参照を返すことができます。データセット**。  
  
 たとえば、次に示すコード サンプルでは孫 XPath クエリが実行されます。 **データセット**には、次の3つのテーブルが格納されます。**顧客**、**注文**、および**OrderDetails**。 このサンプルでは、 **Customers**テーブルと**orders**テーブルの間、および**orders**テーブルと**OrderDetails**テーブルの間に親子関係が最初に作成されます。 次に、XPath クエリが実行されて、孫**OrderDetails**ノードに43という値の**ProductID**ノードがある**Customers**ノードの**xmlnodelist**が返されます。 基本的に、このサンプルでは、XPath クエリを使用して、 **ProductID**が43の製品を発注した顧客を特定します。  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet と XmlDataDocument の同期](dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET の概要](../ado-net-overview.md)

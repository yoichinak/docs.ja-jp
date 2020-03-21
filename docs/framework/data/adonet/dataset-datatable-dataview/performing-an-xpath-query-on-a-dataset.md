---
title: DataSet に対する XPath クエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150832"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>DataSet に対する XPath クエリの実行
同期された<xref:System.Data.DataSet>XML<xref:System.Xml.XmlDataDocument>との間のリレーションシップを使用すると、XML パス言語 (XPath) クエリなど **、XmlDataDocument**にアクセスし、**データセット**に直接アクセスするよりも便利な特定の機能を実行できます。 たとえば<xref:System.Data.DataTable>、 の**Select**メソッドを使用して**DataSet**内の他のテーブルとのリレーションシップを移動するのではなく、 **DataSet**と同期された**XmlDataDocument**に対して XPath クエリを実行して、 の形式で<xref:System.Xml.XmlNodeList>XML 要素の一覧を取得できます。 <xref:System.Xml.XmlElement>ノードとしてキャストされた**XmlNodeList**のノードは、 **XmlDataDocument**の**GetRowFromElement**メソッドに渡され、同期された<xref:System.Data.DataRow>**データセット**内のテーブルの行への一致する参照を返すことができます。  
  
 たとえば、次に示すコード サンプルでは孫 XPath クエリが実行されます。 **データセット**には **、"得意先"** テーブル **、"受注"**、および "**受注明細**" という 3 つのテーブルが格納されます。 サンプルでは、最初に **[得意先]** テーブルと [**受注]** テーブルの間、および **[受注]** テーブルと [**受注明細**] テーブルの間に親子関係が作成されます。 次に、XPath クエリを実行して、孫**の OrderDetails**ノードに値が 43 の**ProductID**ノードがある**顧客**ノードの**XmlNodeList**を返します。 基本的に、サンプルでは XPath クエリを使用して、**製品 ID**が 43 の製品を注文した顧客を特定しています。  
  
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

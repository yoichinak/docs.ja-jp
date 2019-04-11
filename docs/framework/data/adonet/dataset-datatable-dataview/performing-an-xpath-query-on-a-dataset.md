---
title: DataSet に対する XPath クエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 29d1e5ae494b2fff4e13886159bb937041152382
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209477"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>DataSet に対する XPath クエリの実行
同期済みの間のリレーションシップ<xref:System.Data.DataSet>と<xref:System.Xml.XmlDataDocument>XML を使用するのには、アクセス、XML Path Language (XPath) クエリなどのサービス、 **XmlDataDocument**特定の機能を実行できます簡単にアクセスするよりも、**データセット**直接します。 使用してではなく、たとえば、**選択**のメソッド、<xref:System.Data.DataTable>内の他のテーブルにリレーションシップをナビゲートする、**データセット**で XPath クエリを実行することができます、 **XmlDataDocument**と同期される、**データセット**の形式で XML 要素の一覧を取得する、<xref:System.Xml.XmlNodeList>します。 内のノード、 **XmlNodeList**としてキャスト<xref:System.Xml.XmlElement>ノードに渡すことができます、 **GetRowFromElement**のメソッド、 **XmlDataDocument**を一致を返す<xref:System.Data.DataRow>は同期済みテーブルの行への参照**データセット**します。  
  
 たとえば、次に示すコード サンプルでは孫 XPath クエリが実行されます。 **データセット**は 3 つのテーブルで塗りつぶされます。**顧客**、**注文**、および**OrderDetails**します。 サンプルでは、親子関係が最初に作成の間、**顧客**と**注文**テーブル、および、**注文**と**OrderDetails**テーブル。 返す XPath クエリが実行を**XmlNodeList**の**顧客**ノードが、孫**OrderDetails**ノードには、 **ProductID**43 の値を持つノード。 基本的には、サンプルを使用して、XPath クエリを持つ製品を注文した顧客を特定、 **ProductID** 43 の。  
  
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

- [DataSet と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

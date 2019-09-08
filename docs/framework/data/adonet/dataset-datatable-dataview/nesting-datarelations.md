---
title: DataRelation の入れ子化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 971a1bddc40521dc7381ecb2e39709c0fed282ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785987"
---
# <a name="nesting-datarelations"></a>DataRelation の入れ子化
データのリレーショナル表現では、各テーブルに含まれている行が、列または列セットを使用して相互に関連付けられています。 ADO.NET の <xref:System.Data.DataSet> では、テーブル間のリレーションシップは <xref:System.Data.DataRelation> を使用して実装されます。 **DataRelation**を作成する場合、列の親子リレーションシップは、リレーションシップを通じてのみ管理されます。 テーブルと列はそれぞれ別個のエンティティです。 XML のデータ階層表現では、子要素が入れ子の状態で含まれている親要素によって親子のリレーションシップが表現されます。  
  
 **データセット**が<xref:System.Xml.XmlDataDocument>と同期されるとき、または**WriteXml**を使用して XML データとして書き込まれるときに、子オブジェクトの入れ子を容易にするために、 **DataRelation**は**入れ子になっ**たプロパティを公開します。 **DataRelation**の**nested**プロパティを**true**に設定すると、XML データとして書き込まれるとき、または**XmlDataDocument**と同期されるときに、リレーションシップの子行が親列内に入れ子になります。 既定では、 **DataRelation**の**Nested**プロパティは**false**です。  
  
 たとえば、次の**データセット**について考えてみます。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 このデータセットでは、 **DataRelation**オブジェクトの**nested**プロパティは**true**に設定されていない**ため、この** **データセット**が XML データとして表される場合、子オブジェクトは親要素内に入れ子にされません。 入れ子になっていないデータリレーションを含む**データ** **セット**の XML 表現を変換すると、パフォーマンスが低下する可能性があります。 データ リレーションシップは入れ子にすることをお勧めします。 これを行うには、 **Nested**プロパティを**true**に設定します。 次に、トップダウン階層形式の XPath クエリ式を使用してデータを検索、変換するコードを XSLT スタイル シートに記述します。  
  
 次のコード例は、**データセット**で**WriteXml**を呼び出した結果を示しています。  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 **Customers**要素と**Orders**要素は兄弟要素として表示されることに注意してください。 **Orders**要素をそれぞれの親要素の子として表示する場合は、 **DataRelation**の**Nested**プロパティを**true**に設定し、次の値を追加する必要があります。  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 次のコードは、結果として得られる出力を示しています。 **Orders**要素はそれぞれの親要素の中に入れ子になっています。  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataRelation の追加](adding-datarelations.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)

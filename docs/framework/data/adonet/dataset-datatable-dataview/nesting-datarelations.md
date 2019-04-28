---
title: DataRelation の入れ子化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 7975e17bd957a822bf3d60d487eb928cee84bd28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607324"
---
# <a name="nesting-datarelations"></a>DataRelation の入れ子化
データのリレーショナル表現では、各テーブルに含まれている行が、列または列セットを使用して相互に関連付けられています。 ADO.NET の <xref:System.Data.DataSet> では、テーブル間のリレーションシップは <xref:System.Data.DataRelation> を使用して実装されます。 作成するときに、 **DataRelation**列の親子リレーションシップは、リレーションだけをとおして管理されます。 テーブルと列はそれぞれ別個のエンティティです。 XML のデータ階層表現では、子要素が入れ子の状態で含まれている親要素によって親子のリレーションシップが表現されます。  
  
 子オブジェクトの入れ子を実現するときに、**データセット**と同期されて、<xref:System.Xml.XmlDataDocument>またはを使用して XML データとして書き込まれる**WriteXml**、 **DataRelation**公開、**入れ子になった**プロパティ。 設定、**入れ子になった**のプロパティを**DataRelation**に**true**子には、XML データとして書き込まれるときに、親列内で入れ子にするリレーションシップの行を原因または同期されて、 **XmlDataDocument**します。 **入れ子になった**のプロパティ、 **DataRelation**は**false**、既定では。  
  
 たとえば、次**データセット**します。  
  
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
  
 **入れ子になった**のプロパティ、 **DataRelation**オブジェクトに設定されていない**true**この**データセット**、子オブジェクトが入れ子になっていません。親要素内でときにこの**データセット**は XML データとして表されます。 XML 表現に変換する、**データセット**を格納している関連**データセット**に入れ子にされたデータ リレーションシップのパフォーマンスの低下が発生することができます。 データ リレーションシップは入れ子にすることをお勧めします。 これを行うには、設定、**入れ子になった**プロパティを**true**します。 次に、トップダウン階層形式の XPath クエリ式を使用してデータを検索、変換するコードを XSLT スタイル シートに記述します。  
  
 次のコード例は、呼び出しの結果を示しています。 **WriteXml**上、**データセット**します。  
  
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
  
 なお、**顧客**要素と**注文**要素が兄弟要素として表示されます。 場合は、**注文**要素をそれぞれの親要素の子として、**入れ子になった**のプロパティ、 **DataRelation** に設定する必要があります**true**とするには、次を追加します。  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 次のコードは、結果の出力がどのようなで、**注文**要素は、該当する親要素内に入れ子にします。  
  
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

- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataRelation の追加](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

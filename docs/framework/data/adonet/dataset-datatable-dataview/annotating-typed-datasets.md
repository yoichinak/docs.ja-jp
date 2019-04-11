---
title: 型指定された DataSet の注釈
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: d8a1a12a4d8ab5e6f4b0fe6ad6c2a3759aa65aa9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085130"
---
# <a name="annotating-typed-datasets"></a>型指定された DataSet の注釈
注釈を使用すると、基になるスキーマを変更せずに型指定された <xref:System.Data.DataSet> の要素の名前を変更できます。 型指定された、基になるスキーマの要素の名前を変更することになる**データセット**にはない、データ ソースに存在だけでなく、データ ソース内に存在しているオブジェクトへの参照が失われるオブジェクトを参照してください。  
  
 注釈を使用してカスタマイズできますオブジェクトの名前、型指定された**データセット**よりわかりやすい名前を使用するコードが読みやすくし、型指定された**データセット**をそのまま使用するクライアントを簡単に基になるスキーマがそのまま残ります。 次のスキーマ要素の対応など、**顧客**のテーブル、 **Northwind**データベースになる、 **DataRow**のオブジェクト名**CustomersRow**と<xref:System.Data.DataRowCollection>という**顧客**します。  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **DataRowCollection**の名前**顧客**は、クライアント コードで意味を持ちますが、 **DataRow**の名前**CustomersRow**が誤解を招き1 つのオブジェクトであるため、 また、共通のシナリオでは、オブジェクトはせずに参照、**行**識別子代わりに、単として参照されると、**顧客**オブジェクト。 解決するには、スキーマの注釈を付け、新しい名前を指定する、 **DataRow**と**DataRowCollection**オブジェクト。 上記のスキーマに注釈を付けたスキーマを次に示します。  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 指定する、 **typedName**の値**顧客**になります、 **DataRow**オブジェクト名の**顧客**します。 指定する、 **typedPlural**の値**顧客**保持、 **DataRowCollection**の名前**顧客**します。  
  
 使用できる注釈を次の表に示します。  
  
|注釈|説明|  
|----------------|-----------------|  
|**typedName**|オブジェクト名。|  
|**typedPlural**|オブジェクトのコレクション名。|  
|**typedParent**|親のリレーションシップで参照される場合のオブジェクト名。|  
|**typedChildren**|子のリレーションシップからオブジェクトを返すメソッド名。|  
|**nullValue**|値の場合は、基になる値は**DBNull**します。 次の表を参照してください。 **nullValue**注釈。 既定値は **_throw**します。|  
  
 次の表に、値を指定できる、 **nullValue**注釈。  
  
|nullValue の値|説明|  
|---------------------|-----------------|  
|*Replacement Value*|返される値を指定します。 返された値は要素の型と一致する必要があります。 たとえば、整数型フィールドが null の場合に 0 を返すために `nullValue="0"` を使用します。|  
|**_throw**|例外をスローします。 既定値です。|  
|**_null**|プリミティブ型が見つかった場合は、null 参照を返すか、例外をスローします。|  
|**_empty**|文字列を返す**String.Empty**、それ以外の場合、空のコンス トラクターから作成されたオブジェクトを返します。 プリミティブ型が見つかった場合、例外をスローします。|  
  
 次の表は、型指定されたオブジェクトの既定値を示します**データセット**と使用可能な注釈。  
  
|オブジェクト/メソッド/イベント|既定値|注釈|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable**メソッド|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**プロパティ**|PropertyName|typedName|  
|**子**アクセサー|GetChildTableNameRows|typedChildren|  
|**親**アクセサー|TableNameRow|typedParent|  
|**データセット**イベント|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 使用する型指定された**データセット**注釈では、次を含める必要があります**xmlns** XML スキーマ定義言語 (XSD) スキーマで参照します。 データベース テーブルから xsd を作成するを参照してください。<xref:System.Data.DataSet.WriteXmlSchema%2A>または[Visual Studio でのデータセットの操作](/visualstudio/data-tools/dataset-tools-in-visual-studio)します。  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 公開するサンプル注釈付きスキーマを次に、**顧客**のテーブル、 **Northwind**リレーションを持つデータベース、**注文**に含まれるテーブル。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 次のコード例は、厳密に型指定された**データセット**サンプル スキーマから作成します。 1 つを使用して<xref:System.Data.SqlClient.SqlDataAdapter>を設定する、**顧客**テーブル<xref:System.Data.SqlClient.SqlDataAdapter>を設定する、**注文**テーブル。 厳密に型指定された**データセット**定義、 **Datarelation**します。  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

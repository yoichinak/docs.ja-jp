---
title: 型指定された DataSet の注釈
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151521"
---
# <a name="annotating-typed-datasets"></a>型指定された DataSet の注釈
注釈を使用すると、基になるスキーマを変更せずに型指定された <xref:System.Data.DataSet> の要素の名前を変更できます。 基になるスキーマの要素の名前を変更すると、型指定された**DataSet**がデータ ソースに存在しないオブジェクトを参照し、データ ソースに存在するオブジェクトへの参照が失われます。  
  
 注釈を使用すると、より意味のある名前で型指定された**DataSet**内のオブジェクトの名前をカスタマイズできるため、基になるスキーマをそのまま使用しながら、コードを読みやすくし、型指定された**DataSet**をクライアントが使いやすくすることができます。 たとえば、**ノースウィンド**データベースの**Customers**テーブルに対する次のスキーマ要素は **、DataRow**オブジェクト名として **[得意先] と**[<xref:System.Data.DataRowCollection>**得意先]** という名前になります。  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **顧客**の**データ行の名前**は、クライアント コードで意味がありますが、1 つのオブジェクトであるため **、CustomersRow**の**データ行**名は誤解を招く可能性があります。 また、一般的なシナリオでは、オブジェクトは**Row**識別子なしで参照され、代わりに単に**Customer**オブジェクトと呼ばれます。 解決策は、スキーマにア名を付け **、DataRow**オブジェクトと**DataRowCollection**オブジェクトの新しい名前を識別することです。 上記のスキーマに注釈を付けたスキーマを次に示します。  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **型指定された名前**の値を**Customer**に指定すると **、DataRow**オブジェクト名が**Customer**になります。 **型指定された複数の**値を**指定して顧客**の**データRowコレクション**名**を保持します**。  
  
 使用できる注釈を次の表に示します。  
  
|Annotation|説明|  
|----------------|-----------------|  
|**typedName**|オブジェクトの名前。|  
|**typedPlural**|オブジェクトのコレクション名。|  
|**typedParent**|親のリレーションシップで参照される場合のオブジェクト名。|  
|**typedChildren**|子のリレーションシップからオブジェクトを返すメソッド名。|  
|**null値**|基になる値が**DBNull**の場合の値。 **null 値**の注釈については、次の表を参照してください。 デフォルトは **_throw**です。|  
  
 次の表は **、nullValue**アノテーションに指定できる値を示しています。  
  
|nullValue の値|説明|  
|---------------------|-----------------|  
|*置換値*|返される値を指定します。 返された値は要素の型と一致する必要があります。 たとえば、整数型フィールドが null の場合に 0 を返すために `nullValue="0"` を使用します。|  
|**_throw**|例外をスローします。 これは既定値です。|  
|**_null**|プリミティブ型が見つかった場合は、null 参照を返すか、例外をスローします。|  
|**_empty**|文字列の場合は**String.Empty**を返します。 プリミティブ型が見つかった場合、例外をスローします。|  
  
 次の表は、型指定された**DataSet**内のオブジェクトの既定値と使用可能な注釈を示しています。  
  
|オブジェクト/メソッド/イベント|Default|Annotation|  
|---------------------------|-------------|----------------|  
|**Datatable**|TableNameDataTable|typedPlural|  
|**データテーブル**メソッド|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**Datarow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**プロパティ**|PropertyName|typedName|  
|**子供**アクセサー|GetChildTableNameRows|typedChildren|  
|**親**アクセサー|TableNameRow|typedParent|  
|**データセット**イベント|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 型指定された**データセット**の注釈を使用するには、XML スキーマ定義言語 (XSD) スキーマに次の**xmlns**参照を含める必要があります。 データベース テーブルから xsd を作成<xref:System.Data.DataSet.WriteXmlSchema%2A>するには、「 Visual [Studio でデータセットを操作する](/visualstudio/data-tools/dataset-tools-in-visual-studio)」を参照してください。  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 次に示す **、"受注"** テーブルに関係のある**Northwind**データベースの**Customers**テーブルを公開する、サンプルのアノーセット スキーマを示します。  
  
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
  
 サンプル スキーマから作成された厳密に型指定された**データセット**を使用するコード例を次に示します。 このテーブルでは<xref:System.Data.SqlClient.SqlDataAdapter>、1 つを使用して<xref:System.Data.SqlClient.SqlDataAdapter>**[得意先]** テーブルにデータを入力し、もう 1 つを使用して **[受注]** テーブルにデータを入力します。 厳密に型指定された**データセットは**、**データリレーションシップ**を定義します。  
  
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
- [型指定されたデータセット](typed-datasets.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)

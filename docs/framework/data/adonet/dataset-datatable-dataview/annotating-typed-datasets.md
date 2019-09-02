---
title: 型指定された DataSet の注釈
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 8ce7cd859ce0c9a5874751e9928e5bced33593d6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205251"
---
# <a name="annotating-typed-datasets"></a>型指定された DataSet の注釈
注釈を使用すると、基になるスキーマを変更せずに型指定された <xref:System.Data.DataSet> の要素の名前を変更できます。 基になるスキーマの要素の名前を変更すると、型指定されたデータ**セット**は、データソース内に存在しないオブジェクトを参照するだけでなく、データソース内に存在するオブジェクトへの参照も失われます。  
  
 注釈を使用すると、基になるスキーマをそのまま残したまま、型指定された**データセット**内のオブジェクトの名前をわかりやすい名前でカスタマイズし、コードを読みやすくし、型指定された**データセット**をクライアントで簡単に使用できるようにすることができます。 たとえば、 **Northwind**データベースの**customers**テーブルの次の schema 要素では、customers **srow**および<xref:System.Data.DataRowCollection>名前付き**顧客**の**DataRow**オブジェクト名が生成されます。  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **顧客**の**DataRowCollection**名は、クライアントコードでは意味がありますが、1つのオブジェクトであるため、顧客**srow**の**DataRow**名は誤解を招くことがあります。 また、一般的なシナリオでは、オブジェクトは**行**識別子なしで参照され、代わりに**Customer**オブジェクトとして参照されます。 この問題を解決するには、スキーマに注釈を付け、 **DataRow**オブジェクトと**DataRowCollection**オブジェクトの新しい名前を識別します。 上記のスキーマに注釈を付けたスキーマを次に示します。  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **Customer**の**typedName**値を指定すると、 **customer**の**DataRow**オブジェクト名が生成されます。 **顧客**の**typedPlural**値を指定すると、**顧客**の**DataRowCollection**名が保持されます。  
  
 使用できる注釈を次の表に示します。  
  
|注釈|説明|  
|----------------|-----------------|  
|**typedName**|オブジェクト名。|  
|**typedPlural**|オブジェクトのコレクション名。|  
|**typedParent**|親のリレーションシップで参照される場合のオブジェクト名。|  
|**typedChildren**|子のリレーションシップからオブジェクトを返すメソッド名。|  
|**nullValue**|基になる値が**DBNull**の場合の値。 **Nullvalue**の注釈については、次の表を参照してください。 既定値は**throw**です。|  
  
 **Nullvalue**注釈に指定できる値を次の表に示します。  
  
|nullValue の値|説明|  
|---------------------|-----------------|  
|*置換後の値*|返される値を指定します。 返された値は要素の型と一致する必要があります。 たとえば、整数型フィールドが null の場合に 0 を返すために `nullValue="0"` を使用します。|  
|**_throw**|例外をスローします。 既定値です。|  
|**_null**|プリミティブ型が見つかった場合は、null 参照を返すか、例外をスローします。|  
|**_empty**|文字列の場合は、文字列を返し**ます。** それ以外の場合は、空のコンストラクターから作成されたオブジェクトを返します。 プリミティブ型が見つかった場合、例外をスローします。|  
  
 次の表は、型指定された**データセット**内のオブジェクトの既定値と使用可能な注釈を示しています。  
  
|オブジェクト/メソッド/イベント|既定値|注釈|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable**メソッド|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Property**|PropertyName|typedName|  
|**子**Accessor|GetChildTableNameRows|typedChildren|  
|**親**Accessor|TableNameRow|typedParent|  
|**データセット**記録|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 型指定された**データセット**の注釈を使用するには、XML スキーマ定義言語 (XSD) スキーマに次の**xmlns**参照を含める必要があります。 データベーステーブルから xsd を作成するには<xref:System.Data.DataSet.WriteXmlSchema%2A> 、「」または「 [Visual Studio でのデータセットの操作](/visualstudio/data-tools/dataset-tools-in-visual-studio)」を参照してください。  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 次のサンプルの注釈付きスキーマでは、 **Northwind**データベースの**Customers**テーブルが、含まれている**Orders**テーブルとの関係と共に公開されます。  
  
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
  
 次のコード例では、サンプルスキーマから作成した厳密に型指定された**データセット**を使用します。 1つ<xref:System.Data.SqlClient.SqlDataAdapter>のを使用して**Customers**テーブルを<xref:System.Data.SqlClient.SqlDataAdapter>設定し、別のを使用して**Orders**テーブルにデータを設定します。 厳密に型指定された**データセット**は、 **datarelation**を定義します。  
  
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
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

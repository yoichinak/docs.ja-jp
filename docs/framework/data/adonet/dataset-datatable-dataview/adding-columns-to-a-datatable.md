---
title: DataTable への列の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 105537a5fccef6de7266407c78cc915f8c5d8678
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204060"
---
# <a name="adding-columns-to-a-datatable"></a>DataTable への列の追加
に<xref:System.Data.DataTable>は、テーブルの<xref:System.Data.DataColumn> **Columns**プロパティによって参照されるオブジェクトのコレクションが含まれています。 この列のコレクションと制約によって、テーブルのスキーマ (構造) が定義されます。  
  
 テーブル内に**datacolumn**オブジェクトを作成するには、 **datacolumn**コンストラクターを使用するか、テーブル<xref:System.Data.DataColumnCollection>の**Columns**プロパティの**Add**メソッド () を呼び出します。 **Add**メソッドは、オプションの**ColumnName**、 **DataType**、および**Expression**引数を受け取り、コレクションのメンバーとして新しい**DataColumn**を作成します。 また、既存の**datacolumn**オブジェクトを受け取り、それをコレクションに追加し、要求された場合は追加された**datacolumn**への参照を返します。 **DataTable**オブジェクトはどのデータソースにも固有ではないため、 **DataColumn**のデータ型を指定するときに .NET Framework 型が使用されます。  
  
 次の例では、 **DataTable**に4つの列を追加します。  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 この例では、 **CustID**列のプロパティが**DBNull**値を許可しないように設定されていて、値が一意になるように制約されていることに注意してください。 ただし、 **CustID**列をテーブルの主キー列として定義すると、 **allowdbnull**プロパティが自動的に**false**に設定され、 **Unique**プロパティが自動的に**true**に設定されます。 詳細については、「[主キーの定義](defining-primary-keys.md)」を参照してください。  
  
> [!CAUTION]
> 列名が列に指定されていない場合、列には、 **DataColumnCollection**に追加されると、"Column1" で始まる列*N*の増分既定名が指定されます。 列名を指定するときは、"Column*N*" の命名規則を使用しないことをお勧めします。これは、指定した名前が**DataColumnCollection**内の既存の既定の列名と競合する可能性があるためです。 指定した名前が既に存在する場合は、例外がスローされます。  
  
 <xref:System.Xml.Linq.XElement> を、<xref:System.Data.DataColumn.DataType%2A> 内の <xref:System.Data.DataColumn> の <xref:System.Data.DataTable> として使用すると、データを読み取るときに XML シリアル化が機能しません。 たとえば、<xref:System.Xml.XmlDocument> メソッドを使用して `DataTable.WriteXml` を書き込むと、XML へのシリアル化で <xref:System.Xml.Linq.XElement> に親ノードが追加されます。 この問題に対処するには、<xref:System.Data.SqlTypes.SqlXml> の代わりに <xref:System.Xml.Linq.XElement> 型を使用します。 `ReadXml` および `WriteXml` は、<xref:System.Data.SqlTypes.SqlXml> で適切に機能します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable スキーマの定義](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

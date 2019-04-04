---
title: DataTable への列の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 892c0488588e9a5b59650f4a815ba9819493a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538270"
---
# <a name="adding-columns-to-a-datatable"></a>DataTable への列の追加
A<xref:System.Data.DataTable>のコレクションを含む<xref:System.Data.DataColumn>によって参照されるオブジェクト、**列**テーブルのプロパティ。 この列のコレクションと制約によって、テーブルのスキーマ (構造) が定義されます。  
  
 作成する**DataColumn**を使用してテーブル内のオブジェクト、 **DataColumn**コンス トラクター、または呼び出すことによって、**追加**のメソッド、**列**これは、テーブルのプロパティを<xref:System.Data.DataColumnCollection>します。 **追加**メソッドは省略可能な**ColumnName**、 **DataType**、および**式**引数新たに作成および**DataColumn**コレクションのメンバーとして。 既存のも受け付けます**DataColumn**オブジェクトし、コレクションに追加しを追加の参照を返します**DataColumn**要求された場合。 **DataTable**オブジェクトは任意のデータ ソースに固有ではないのデータ型を指定するときに .NET Framework の型が使用される、 **DataColumn**します。  
  
 次の例では、4 つの列に、 **DataTable**します。  
  
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
  
 この例では、プロパティを**CustID**列は許可しないように設定**DBNull**値と一意である値を制限します。 ただし、定義した場合、 **CustID**列、テーブルの主キー列として、 **AllowDBNull**プロパティに自動的に設定する**false**と、 **Unique**プロパティに自動的に設定する**true**します。 詳細については、[主キーを定義する](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)を参照してください。  
  
> [!CAUTION]
>  列の列名が指定されていない場合、列が指定された列のインクリメンタル既定名*N、* "Column1"から始めて、ときに追加されます、 **DataColumnCollection**します。 名前付け規則を回避することをお勧めします。"列*N*"の既存の既定の列名と競合する可能性が名前を指定するために、列名を指定するときに、 **DataColumnCollection**します。 指定した名前が既に存在する場合は、例外がスローされます。  
  
 <xref:System.Xml.Linq.XElement> を、<xref:System.Data.DataColumn.DataType%2A> 内の <xref:System.Data.DataColumn> の <xref:System.Data.DataTable> として使用すると、データを読み取るときに XML シリアル化が機能しません。 たとえば、<xref:System.Xml.XmlDocument> メソッドを使用して `DataTable.WriteXml` を書き込むと、XML へのシリアル化で <xref:System.Xml.Linq.XElement> に親ノードが追加されます。 この問題に対処するには、<xref:System.Data.SqlTypes.SqlXml> の代わりに <xref:System.Xml.Linq.XElement> 型を使用します。 `ReadXml` および `WriteXml` は、<xref:System.Data.SqlTypes.SqlXml> で適切に機能します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: DataTable 内のデータの表示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: fa8749550e10256ee0623714cc95e03a838655c8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364490"
---
# <a name="viewing-data-in-a-datatable"></a>DataTable 内のデータの表示

内容にアクセスすることができます、<xref:System.Data.DataTable>を使用して、**行**と**列**のコレクション、 **DataTable**します。 使用することも、<xref:System.Data.DataTable.Select%2A>内のデータのサブセットを返すメソッドを**DataTable**検索基準などの基準に従って並べ替え順序、および行の状態。 また、使用することができます、<xref:System.Data.DataRowCollection.Find%2A>のメソッド、 **DataRowCollection**主キーの値を使用して特定の行を検索するとき。

**選択**のメソッド、 **DataTable**オブジェクトのセットを返します<xref:System.Data.DataRow>指定した条件に一致するオブジェクト。 **選択**のフィルター式、並べ替え式では、省略可能な引数を受け取ると**DataViewRowState**します。 フィルター式に基づいて返される行を識別する**DataColumn**などの値`LastName = 'Smith'`します。 並べ替え式は、列の並べ替えについての標準 SQL 規則に基づく `LastName ASC, FirstName ASC` などの式です。 式の作成に関する規則は、次を参照してください。、<xref:System.Data.DataColumn.Expression%2A>のプロパティ、 **DataColumn**クラス。

> [!TIP]
> に対する呼び出しの数を実行している場合、**選択**のメソッド、 **DataTable**、最初に作成してパフォーマンスを向上させることができます、<xref:System.Data.DataView>の**DataTable**します。 作成、 **DataView**テーブルの行のインデックスを作成します。 **選択**メソッドを使用し、そのインデックス、クエリの結果を生成する時間を大幅に削減します。 作成する方法については、 **DataView**の**DataTable**を参照してください[Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)します。

**選択**メソッドを表示または操作する行のバージョンに基づいて判断します、<xref:System.Data.DataViewRowState>します。 次の表に、考えられる**DataViewRowState**列挙値。

|DataViewRowState の値|説明|
|----------------------------|-----------------|
|**CurrentRows**|変更されていない行、追加された行、および変更された行を含む現在の行。|
|**削除**|削除された行。|
|**ModifiedCurrent**|元のデータを変更した後のバージョンである、現在のバージョン。 (を参照してください**ModifiedOriginal**)。|
|**ModifiedOriginal**|変更されたすべての行の元のバージョン。 現在のバージョンが利用可能なを使用して**ModifiedCurrent**します。|
|**追加**|新しい行。|
|**None**|なし。|
|**OriginalRows**|変更されていない行および削除された行を含む元の行。|
|**変更なし**|変更されていない行。|

次の例では、**データセット**だけを操作できる行を持つようにオブジェクトをフィルター処理**DataViewRowState**に設定されている**CurrentRows**します。

```vb
Dim column As DataColumn
Dim row As DataRow

Dim currentRows() As DataRow = _
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)

If (currentRows.Length < 1 ) Then
  Console.WriteLine("No Current Rows Found")
Else
  For Each column in workTable.Columns
    Console.Write(vbTab & column.ColumnName)
  Next

  Console.WriteLine(vbTab & "RowState")

  For Each row In currentRows
    For Each column In workTable.Columns
      Console.Write(vbTab & row(column).ToString())
    Next

    Dim rowState As String = _
        System.Enum.GetName(row.RowState.GetType(), row.RowState)
    Console.WriteLine(vbTab & rowState)
  Next
End If
```

```csharp
DataRow[] currentRows = workTable.Select(
    null, null, DataViewRowState.CurrentRows);

if (currentRows.Length < 1 )
  Console.WriteLine("No Current Rows Found");
else
{
  foreach (DataColumn column in workTable.Columns)
    Console.Write("\t{0}", column.ColumnName);

  Console.WriteLine("\tRowState");

  foreach (DataRow row in currentRows)
  {
    foreach (DataColumn column in workTable.Columns)
      Console.Write("\t{0}", row[column]);

    Console.WriteLine("\t" + row.RowState);
  }
}
```

**選択**メソッドを使用して、異なる行を返す**RowState**値またはフィールド値。 次の例を返します、 **DataRow**が削除されてを返す他のすべての行を参照する配列**DataRow**によって順序付けられた、すべての行を参照する配列**CustLName**、場所、 **CustID**列が 5 より大きい。 内の情報を表示する方法については、 **Deleted**行を参照してください[行の状態と行バージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。

```vb
' Retrieve all deleted rows.
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)

' Retrieve rows where CustID > 5, and order by CustLName.
Dim custRows() As DataRow = workTable.Select( _
    "CustID > 5", "CustLName ASC")
```

```csharp
// Retrieve all deleted rows.
DataRow[] deletedRows = workTable.Select(
    null, null, DataViewRowState.Deleted);

// Retrieve rows where CustID > 5, and order by CustLName.
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");
```

## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

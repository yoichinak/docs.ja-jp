---
title: DataTable 内のデータの表示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ea92b8a5e46bdaa8e94756cd28a3fbcb2789d7b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204390"
---
# <a name="viewing-data-in-a-datatable"></a>DataTable 内のデータの表示

の<xref:System.Data.DataTable>内容にアクセスするには、 **DataTable**の**Rows**コレクションと**Columns**コレクションを使用します。 また、 <xref:System.Data.DataTable.Select%2A>メソッドを使用して、検索条件、並べ替え順序、および行の状態などの条件に基づいて、 **DataTable**内のデータのサブセットを返すこともできます。 また、主キーの値<xref:System.Data.DataRowCollection.Find%2A>を使用して特定の行を検索するときに、 **DataRowCollection**のメソッドを使用することもできます。

**DataTable**オブジェクトの**Select**メソッドは、指定された<xref:System.Data.DataRow>条件に一致するオブジェクトのセットを返します。 **Select**は、フィルター式、並べ替え式、および**DataViewRowState**の省略可能な引数を受け取ります。 フィルター式は、 **DataColumn**値 (など) に基づいて`LastName = 'Smith'`返される行を識別します。 並べ替え式は、列の並べ替えについての標準 SQL 規則に基づく `LastName ASC, FirstName ASC` などの式です。 式の記述に関する規則につい<xref:System.Data.DataColumn.Expression%2A>ては、 **DataColumn**クラスのプロパティを参照してください。

> [!TIP]
> Datatable の**Select**メソッドに対して多数の呼び出しを実行している場合は、最初に<xref:System.Data.DataView> **datatable**のを作成することによってパフォーマンスを向上させることができます。 **DataView**を作成すると、テーブルの行にインデックスが作成されます。 次に、 **Select**メソッドはそのインデックスを使用して、クエリ結果の生成にかかる時間を大幅に短縮します。 **DataTable**の**DataView**の作成の詳細については、「 [dataviews](dataviews.md)」を参照してください。

**Select**メソッドは、 <xref:System.Data.DataViewRowState>に基づいて表示または操作する行のバージョンを決定します。 次の表では、使用可能な**DataViewRowState**列挙値について説明します。

|DataViewRowState の値|説明|
|----------------------------|-----------------|
|**CurrentRows**|変更されていない行、追加された行、および変更された行を含む現在の行。|
|**削除**|削除された行。|
|**ModifiedCurrent**|元のデータを変更した後のバージョンである、現在のバージョン。 (「 **ModifiedOriginal**」を参照してください)。|
|**ModifiedOriginal**|変更されたすべての行の元のバージョン。 現在のバージョンは、 **ModifiedCurrent**を使用して入手できます。|
|**れ**|新しい行。|
|**None**|なし。|
|**OriginalRows**|変更されていない行および削除された行を含む元の行。|
|**Unchanged**|変更されていない行。|

次の例では、**データセット**オブジェクトをフィルター処理して、 **DataViewRowState**が**currentrows**に設定されている行のみを処理するようにしています。

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

**Select**メソッドを使用して、異なる**RowState**値またはフィールド値を持つ行を返すことができます。 次の例では、削除されたすべての行を参照する**datarow**配列を返し、 **custlname**によって並べ替えられた、 **CustID**列が5より大きいすべての行を参照する別の**datarow**配列を返します。 **削除さ**れた行の情報を表示する方法の詳細については、「[行の状態と行のバージョン](row-states-and-row-versions.md)」を参照してください。

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
- [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)
- [行の状態とバージョン](row-states-and-row-versions.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

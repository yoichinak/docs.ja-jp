---
title: '方法: ジェネリック型 T が DataRow ではない CopyToDataTable<T> を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 27df5e88b93914d317f0f59c704382bde67534d2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794990"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>方法: ジェネリック型 T が\<DataRow ではない copytodatatable T > を実装します。
データ バインドには、しばしば <xref:System.Data.DataTable> オブジェクトが使用されます。 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、クエリの結果を受け取り、そのデータを <xref:System.Data.DataTable> にコピーします。これをデータ バインディングに利用できます。 ただし、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、ジェネリック パラメーター <xref:System.Collections.Generic.IEnumerable%601> が `T` 型である <xref:System.Data.DataRow> ソースに対してのみ作用します。 有用ではありますが、一連のスカラー型、匿名型を射影するクエリ、またはテーブルの結合を実行するクエリからは、テーブルを作成できません。  
  
 このトピックでは、`CopyToDataTable<T>` 型以外のジェネリック パラメーター `T` を受け取る 2 つのカスタム <xref:System.Data.DataRow> 拡張メソッドを実装する方法について説明します。 <xref:System.Data.DataTable> ソースから <xref:System.Collections.Generic.IEnumerable%601> を作成するロジックは、`ObjectShredder<T>` クラスに存在し、オーバーロードされた 2 つの `CopyToDataTable<T>` 拡張メソッドにラップされています。 `Shred` クラスの `ObjectShredder<T>` メソッドは、データが格納された <xref:System.Data.DataTable> を返し、<xref:System.Collections.Generic.IEnumerable%601> ソース、<xref:System.Data.DataTable>、および <xref:System.Data.LoadOption> 列挙型の 3 つの入力パラメーターを受け取ります。 返される <xref:System.Data.DataTable> の最初のスキーマは、`T` 型のスキーマに基づきます。 既存のテーブルを入力として指定する場合は、そのスキーマが、`T` 型のスキーマと矛盾がないようにする必要があります。 返されたテーブルでは、`T` 型のパブリック プロパティおよびパブリック フィールドが、それぞれ <xref:System.Data.DataColumn> に変換されます。 `T` から派生した型がソース シーケンスに含まれている場合は、返されるテーブルのスキーマが、あらゆる追加パブリック プロパティまたは追加パブリック フィールドに展開されます。  
  
 カスタム `CopyToDataTable<T>` メソッドの使用例については、[クエリから DataTable を作成する](creating-a-datatable-from-a-query-linq-to-dataset.md)方法に関するページを参照してください。  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>カスタム CopyToDataTable\<T> メソッドをアプリケーションに実装するには  
  
1. `ObjectShredder<T>` クラスを実装して、<xref:System.Data.DataTable> ソースから <xref:System.Collections.Generic.IEnumerable%601> を作成します。  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    上記の例は、`DataColumn` のプロパティが null 許容型ではないことを前提としています。 null 許容型のプロパティを処理するには、次のコードを使用します。

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. カスタム `CopyToDataTable<T>` 拡張メソッドをクラスに実装します。  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. `ObjectShredder<T>` クラスおよび `CopyToDataTable<T>` 拡張メソッドをアプリケーションに追加します。  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a>関連項目

- [クエリによる DataTable の作成](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [プログラミング ガイド](programming-guide-linq-to-dataset.md)

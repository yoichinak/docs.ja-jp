---
title: バルク コピー操作の単一実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 05e3cf25352e731d320061001f08a835cd520b15
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780930"
---
# <a name="single-bulk-copy-operations"></a>バルク コピー操作の単一実行

SQL Server のバルク コピー操作を実行する簡単な方法は、データベースに対して単一操作を実行することです。 既定では、バルク コピー操作は分離された操作として実行されます。このコピー操作は非トランザクション方式で処理され、ロールバックできません。

> [!NOTE]
> エラーの発生時に、バルク コピー処理の全部または一部をロールバックする必要がある場合は、<xref:System.Data.SqlClient.SqlBulkCopy> が管理するトランザクションを使用するか、または既存のトランザクション内でバルク コピー操作を実行できます。 また、 **SqlBulkCopy**は、 <xref:System.Transactions>接続が (暗黙的または明示的に) system.object トランザクションに参加している場合にも使用でき**ます。**
>
> 詳細については、「[トランザクションと一括コピーの操作](transaction-and-bulk-copy-operations.md)」を参照してください。

通常、バルク コピー操作の実行手順は次のようになります。

1. コピー元のサーバーに接続し、コピーするデータを取得します。 <xref:System.Data.IDataReader> オブジェクトまたは <xref:System.Data.DataTable> オブジェクトからデータを取得できる場合は、他のソースからデータを取得して利用することもできます。

2. 移行先サーバーに接続します ( **SqlBulkCopy**が接続を確立する必要がない場合)。

3. <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを作成し、必要なプロパティを設定します。

4. **Destinationtablename**プロパティを設定して、一括挿入操作の対象テーブルを指定します。

5. **WriteToServer**メソッドのいずれかを呼び出します。

6. 必要に応じて、プロパティを更新し、必要に応じて**WriteToServer**を再度呼び出します。

7. <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> を呼び出すか、または `Using` ステートメント内にバルク コピー操作をラップします。

> [!CAUTION]
> コピー元とコピー先の列のデータ型を一致させることをお勧めします。 データ型が一致しない場合、 **SqlBulkCopy**は、によって<xref:System.Data.SqlClient.SqlParameter.Value%2A>採用されているルールを使用して、各ソース値をターゲットデータ型に変換しようとします。 この変換はパフォーマンスに影響を及ぼし、予期しないエラーが発生することもあります。 たとえば、`Double` データ型は、多くの場合 `Decimal` データ型に変換されますが、常にというわけではありません。

## <a name="example"></a>例

次のコンソール アプリケーションでは、<xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用してデータを読み込む方法について示しています。 この例では、 <xref:System.Data.SqlClient.SqlDataReader> SQL Server **AdventureWorks**データベースの**Production**テーブルから、同じデータベース内の同様のテーブルにデータをコピーするために、が使用されています。

> [!IMPORTANT]
> このサンプルは、「[一括コピーの例のセットアップ](bulk-copy-example-setup.md)」で説明されているように作業テーブルを作成しない限り、実行されません。 このコードは、 **SqlBulkCopy**のみを使用する構文を示すために用意されています。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Transact-SQL および Command クラスを使用したバルク コピー操作の実行

次の例では、BULK INSERT ステートメントを実行する <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> メソッドの使用方法を説明します。

> [!NOTE]
> データ ソースのファイル パスはサーバーに対する相対パスです。 サーバー プロセスがこのパスにアクセスできないと、バルク コピー操作は失敗します。

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a>関連項目

- [SQL Server でのバルク コピー操作](bulk-copy-operations-in-sql-server.md)
- [ADO.NET の概要](../ado-net-overview.md)

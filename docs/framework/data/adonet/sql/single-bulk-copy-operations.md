---
title: バルク コピー操作の単一実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: b2783779965505d09f73c7203770c19ccaa78d26
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323370"
---
# <a name="single-bulk-copy-operations"></a>バルク コピー操作の単一実行
SQL Server のバルク コピー操作を実行する簡単な方法は、データベースに対して単一操作を実行することです。 既定では、バルク コピー操作は分離された操作として実行されます。このコピー操作は非トランザクション方式で処理され、ロールバックできません。  
  
> [!NOTE]
>  エラーの発生時に、バルク コピー処理の全部または一部をロールバックする必要がある場合は、<xref:System.Data.SqlClient.SqlBulkCopy> が管理するトランザクションを使用するか、または既存のトランザクション内でバルク コピー操作を実行できます。 **SqlBulkCopy**はでも動作<xref:System.Transactions>かどうか、接続が参加している (暗黙的または明示的に) に、 **System.Transactions**トランザクション。  
>   
>  詳細については、次を参照してください。[トランザクションとバルク コピー操作](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)します。  
  
 通常、バルク コピー操作の実行手順は次のようになります。  
  
1. コピー元のサーバーに接続し、コピーするデータを取得します。 <xref:System.Data.IDataReader> オブジェクトまたは <xref:System.Data.DataTable> オブジェクトからデータを取得できる場合は、他のソースからデータを取得して利用することもできます。  
  
2. 移行先サーバーに接続 (する場合を除き、 **SqlBulkCopy**の接続を確立するために)。  
  
3. <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを作成し、必要なプロパティを設定します。  
  
4. 設定、 **DestinationTableName**を一括の対象テーブルを示すプロパティが操作を挿入します。  
  
5. 1 つを呼び出して、 **WriteToServer**メソッド。  
  
6. プロパティと呼び出しを必要に応じて、更新**WriteToServer**必要に応じて、もう一度です。  
  
7. <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> を呼び出すか、または `Using` ステートメント内にバルク コピー操作をラップします。  
  
> [!CAUTION]
>  コピー元とコピー先の列のデータ型を一致させることをお勧めします。 データ型が一致しない場合**SqlBulkCopy**で採用されている規則を使用して、対象のデータ型への各ソース値の変換を試みます<xref:System.Data.SqlClient.SqlParameter.Value%2A>します。 この変換はパフォーマンスに影響を及ぼし、予期しないエラーが発生することもあります。 たとえば、`Double` データ型は、多くの場合 `Decimal` データ型に変換されますが、常にというわけではありません。  
  
## <a name="example"></a>例  
 次のコンソール アプリケーションでは、<xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用してデータを読み込む方法について示しています。 この例で、<xref:System.Data.SqlClient.SqlDataReader>からデータをコピーするために使用、 **Production.Product** SQL Server のテーブル**AdventureWorks**データベースを同じデータベース内の同等のテーブル。  
  
> [!IMPORTANT]
>  このサンプルでは」の説明に従って、作業テーブルを作成していない限りは実行されません[バルク コピー サンプルのセットアップ](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)します。 使用する構文を示すためにこのコードが提供される**SqlBulkCopy**のみです。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Transact-SQL および Command クラスを使用したバルク コピー操作の実行  
 次の例では、BULK INSERT ステートメントを実行する <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> メソッドの使用方法を説明します。  
  
> [!NOTE]
>  データ ソースのファイル パスはサーバーに対する相対パスです。 サーバー プロセスがこのパスにアクセスできないと、バルク コピー操作は失敗します。  
  
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

- [SQL Server でのバルク コピー操作](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

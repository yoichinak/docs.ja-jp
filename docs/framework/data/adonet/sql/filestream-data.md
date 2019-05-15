---
title: FILESTREAM データ
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: f8521a9de3037ae759b0b0ea5bcbe84830f8629e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582707"
---
# <a name="filestream-data"></a>FILESTREAM データ

FILESTREAM ストレージ属性は、varbinary(max) 列に格納されるバイナリ (BLOB) データに対応しています。 FILESTREAM の導入前は、バイナリ データの格納するために特別な処理が必要でした。 テキスト ドキュメント、イメージ、ビデオなどの非構造化データはデータベース外に保存されることが多く、そのために管理が困難でした。

> [!NOTE]
> SqlClient を使用して FILESTREAM データを操作するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。

varbinary(max) 列に FILESTREAM 属性を指定すると、SQL Server ではデータはデータベース ファイルではなくローカルの NTFS ファイル システムに保存されます。 データは個別に保存されますが、データベースに保存されている varbinary(max) データの操作のためにサポートされているのと同じ [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ステートメントを使用できます。

## <a name="sqlclient-support-for-filestream"></a>FILESTREAM の SqlClient サポート

SQL server、.NET Framework Data Provider <xref:System.Data.SqlClient>、読み取りと書き込みを使用して FILESTREAM データをサポートしています、<xref:System.Data.SqlTypes.SqlFileStream>クラスで定義されている、<xref:System.Data.SqlTypes>名前空間。 `SqlFileStream` は <xref:System.IO.Stream> クラスを継承します。このクラスは、データのストリームへの読み込みと書き込みを行うためのメソッドを提供します。 ストリームからデータを読み取ると、データはストリームからバイトの配列などのデータ構造に転送されます。 書き込みを行うと、データはデータ構造からストリームに転送されます。

### <a name="creating-the-sql-server-table"></a>SQL Server テーブルの作成

次の [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ステートメントでは、従業員の名前の付いたテーブルを作成し、データ行を挿入します。 FILESTREAM ストレージを有効にすると、このテーブルを次のようなコード例と共に使用できます。 SQL Server オンライン ブックのリソースへのリンクは、このトピックの最後にあります。

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>例:FILESTREAM データを挿入し、読み取り、上書き、

次のサンプルでは、FILESTREAM からデータを読み取る方法を示します。 コードはファイルへの論理パスを取得し、`FileAccess` を `Read` に、`FileOptions` を `SequentialScan` に設定します。 次に、コードは SqlFileStream からバイトをバッファーに読み取ります。 バイトはコンソール ウィンドウに書き込まれます。

また、このサンプルでは、すべての既存のデータを上書きする FILESTREAM にデータを書き込む方法も示します。 コードはファイルへの論理パスを取得し、`SqlFileStream` を作成し、`FileAccess` を `Write` に、`FileOptions` を `SequentialScan` に設定します。 1 バイトが `SqlFileStream` に書き込まれ、ファイルのデータは置換されます。

このサンプルでは、Seek メソッドを使用してファイルの末尾にデータを追加することによって、データを FILESTREAM に書き込む方法も示します。 コードはファイルへの論理パスを取得し、`SqlFileStream` を作成し、`FileAccess` を `ReadWrite` に、`FileOptions` を `SequentialScan` に設定します。 コードは Seek メソッドを使用してファイルの末尾をシークし、1 バイトを既存のファイルに追加します。

```csharp
using System;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

別のサンプルを参照してください。[保存し、ファイル ストリーム列にバイナリ データをフェッチする方法](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)します。

## <a name="resources-in-sql-server-books-online"></a>SQL Server オンライン ブックの関連トピック

FILESTREAM の詳細なドキュメントについては、SQL Server オンライン ブックの次のセクションにあります。

|トピック|説明|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](/sql/relational-databases/blob/filestream-sql-server)|FILESTREAM ストレージを使用するタイミング、および SQL Server データベース エンジンと NTFS ファイル システムを統合する方法について説明します。|
|[FILESTREAM データ用のクライアント アプリケーションを作成します。](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|FILESTREAM データを操作するための Windows API 関数について説明します。|
|[FILESTREAM と他の SQL Server 機能](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|FILESTREAM データを SQL Server の他の機能と共に使用する際の注意事項、ガイドライン、および制限事項について説明します。|

## <a name="see-also"></a>関連項目

- [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [コード アクセス セキュリティと ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)
- [SQL Server のバイナリ データと大きな値のデータ](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET の概要](../../../../../docs/framework/data/adonet/ado-net-overview.md)

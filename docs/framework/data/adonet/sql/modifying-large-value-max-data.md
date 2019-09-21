---
title: ADO.NET での大きい値 (max) データの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 0f029c81dd6ba5cd5202e6e59f33edd7cf8c0b90
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894446"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET での大きい値 (max) データの変更
ラージ オブジェクト (LOB) データ型は、最大行サイズが 8 KB を超えるデータ型です。 SQL Server では、`max`、`varchar`、および `nvarchar` の各データ型に `varbinary` 指定子が用意されており、2^32 バイトの値を格納できます。 テーブル列および Transact-SQL 変数により、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` データ型を指定できます。 ADO.NET では、`max` データ型は、`DataReader` によってフェッチすることができ、特殊な処理を行うことなく入力パラメーターと出力パラメーター両方の値として指定することもできます。 サイズの大きい `varchar` データ型の場合は、データを段階的に取得および更新できます。  
  
 `max` データ型は、Transact-SQL 変数として比較に使用したり、連結に使用したりできます。 これらは SELECT ステートメントの DISTINCT 句、ORDER BY 句、GROUP BY 句で使用できるほか、集約、結合、サブクエリでも使用できます。  
  
 次の表は、SQL Server オンライン ブックのドキュメントへのリンクを提供します。  
  
 **SQL Server オンライン ブック**  
  
1. [大きな値のデータ型の使用](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>大きい値型の制限事項  
 `max` データ型には、小さいデータ型にはない、次の制限事項が適用されます。  
  
- `sql_variant` に大きい `varchar` データ型を含めることはできません。  
  
- 大きい `varchar` 列はインデックス内のキー列として指定することはできません。 非クラスター化インデックスに含まれる列で使用できます。  
  
- 大きい `varchar` 列はパーティション分割のキー列として使用できません。  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL での大きい値型の使用  
 Transact-SQL の `OPENROWSET` 関数は、リモート データへの接続およびアクセスに 1 回だけ使用できます。 この関数には、OLE DB データ ソースからリモート データにアクセスするために必要な、すべての接続情報が含まれています。 `OPENROWSET` は、クエリの FROM 句でテーブル名と同様に参照できます。 OLE DB プロバイダーの機能に従って、INSERT、UPDATE、または DELETE ステートメントのターゲット テーブルとして参照することもできます。  
  
 `OPENROWSET` 関数には、`BULK` 行セット プロバイダーが含まれており、データをターゲット テーブルに読み込むことなく、ファイルから直接読み取ることができます。 これにより、`OPENROWSET` を単純な INSERT SELECT ステートメントで使用できます。  
  
 オプション`OPENROWSET BULK`の引数を使用すると、データの読み取りを開始および終了する場所、エラーを処理する方法、およびデータを解釈する方法を大幅に制御できます。 たとえば、データ ファイルを 1 行として、あるいは `varbinary`、`varchar`、または `nvarchar` 型の 1 列の行セットとして読み取るように指定できます。 完全な構文とオプションについては、SQL Server オンライン ブックを参照してください。  
  
 次の例では、AdventureWorks サンプル データベースの ProductPhoto テーブルに写真を挿入しています。 `BULK OPENROWSET`プロバイダーを使用する場合は、すべての列に値を挿入しない場合でも、列の名前付きリストを指定する必要があります。 この場合の主キーは ID 列として定義され、列リストから省略することもできます。 ただし、`OPENROWSET` ステートメントの最後に相関関係名 (この場合は ThumbnailPhoto) を指定する必要があります。 これにより、ファイルが読み込まれる `ProductPhoto` テーブルの列との相関関係が定義されます。  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>UPDATE .WRITE を使用したデータの更新  
 Transact-SQL の UPDATE ステートメントでは、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` 列の内容を変更するための、新しい WRITE 構文を使用できます。 これにより、データの部分的な更新が可能になります。 次に UPDATE .WRITE 構文を省略形で示します。  
  
 UPDATE  
  
 { *\<object>* }  
  
 SET  
  
 { *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }  
  
 WRITE メソッドは、 *column_name*の値のセクションが変更されることを指定します。 式は、 *column_name* `@Offset`にコピーされる値です。は式が`@Length`書き込まれる開始位置であり、引数は列のセクションの長さを示しています。  
  
|If|Then|  
|--------|----------|  
|expression が NULL|`@Length`は無視され、 *column_name*の値は指定した`@Offset`で切り捨てられます。|  
|`@Offset`NULL である|更新操作では、既存の*column_name*値`@Length`の末尾に式が追加され、無視されます。|  
|`@Offset` が column_name の値の長さより長い|SQL Server からエラーが返されます。|  
|`@Length`NULL である|更新操作により `@Offset` の値の `column_name` から最後までのすべてのデータが削除されます。|  
  
> [!NOTE]
> `@Offset` または `@Length` のいずれにも負数を指定することはできません。  
  
## <a name="example"></a>例  
 この Transact-SQL の例では、AdventureWorks データベースの Document テーブルの `nvarchar(max)` 列である DocumentSummary の値の一部が更新されます。 置換後の単語、置換する単語の既存データ内での開始位置 (オフセット)、置換する文字数 (長さ) を指定することで、'components' という単語が 'features' という単語に置換されます。 この例では、結果を比較するために、UPDATE ステートメントの前後に SELECT ステートメントを指定しています。  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>ADO.NET での大きい値型の使用  
 ADO.NET で大きな値の型を使用するに<xref:System.Data.SqlClient.SqlParameter>は、 <xref:System.Data.SqlClient.SqlDataReader>大きな値の型を内のオブジェクトとして指定して結果セット<xref:System.Data.SqlClient.SqlDataAdapter>を返すか`DataSet`、を/ `DataTable`使用してにデータを格納します。 大きい値型と、関連する小さい値型の使用方法に違いはありません。  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>GetSqlBytes を使用したデータの取得  
 `GetSqlBytes` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varbinary(max)` 列の内容を取得できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `varbinary(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBytes> として取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>GetSqlChars を使用したデータの取得  
 `GetSqlChars` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varchar(max)` または `nvarchar(max)` 列の内容を取得できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `nvarchar(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>GetSqlBinary を使用したデータの取得  
 `GetSqlBinary` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varbinary(max)` 列の内容を取得できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `varbinary(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBinary> ストリームとして取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>GetBytes を使用したデータの取得  
 `GetBytes` の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、指定された配列のオフセットから開始するバイト配列に、指定された列のオフセットからバイトのストリームが読み込まれます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってバイトがバイト配列に読み込まれることが想定されています。 ただし `GetSqlBytes` とは異なり、`GetBytes` では配列バッファーのサイズを指定する必要があります。  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>GetValue を使用したデータの取得  
 `GetValue` の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、指定した列オフセットから値が配列に読み込まれます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによって、最初の列のオフセットからバイナリ データが取得され、2 番目の列のオフセットから文字列データが取得されることが想定されています。  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>大きい値型から CLR 型への変換  
 `varchar(max)` などの任意の文字列変換メソッドを使用して、`nvarchar(max)` または `ToString` 列の内容を変換できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが取得されることが想定されています。  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>例  
 次のコードでは、`LargePhoto` データベースの `ProductPhoto` テーブルから名前と `AdventureWorks` オブジェクトが取得され、ファイルに保存されます。 このアセンブリは、<xref:System.Drawing> 名前空間への参照を指定してコンパイルする必要があります。  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、<xref:System.Data.SqlTypes.SqlBytes> プロパティを公開する `Stream` オブジェクトが返されます。 このコードでは、これを使用`Bitmap`して新しいオブジェクトを作成し、Gif `ImageFormat`に保存します。  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>大きな値型パラメーターの使用  
 大きい値型は、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内の小さい値型と同じ方法で、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内で使用できます。 次の例に示すように<xref:System.Data.SqlClient.SqlParameter> 、大きな値の型は値として取得できます。 このコードでは、次の GetDocumentSummary ストアド プロシージャが、AdventureWorks サンプル データベースに存在することが想定されています。 ストアドプロシージャは、という名前@DocumentIDの入力パラメーターを受け取り、 @DocumentSummary出力パラメーターの documentsummary 列の内容を返します。  
  
```sql
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>例  
 ADO.NET コードにより、<xref:System.Data.SqlClient.SqlConnection> および <xref:System.Data.SqlClient.SqlCommand> オブジェクトが作成され、GetDocumentSummary ストアド プロシージャが実行されることで、ドキュメントの概要が取得され、大きい値型として格納されます。 このコードは、 @DocumentID入力パラメーターの値を渡し、コンソールウィンドウの@DocumentSummary出力パラメーターに返される結果を表示します。  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [SQL Server のバイナリ データと大きな値のデータ](sql-server-binary-and-large-value-data.md)
- [SQL Server データ型のマッピング](../sql-server-data-type-mappings.md)
- [ADO.NET における SQL Server データ操作](sql-server-data-operations.md)
- [ADO.NET の概要](../ado-net-overview.md)

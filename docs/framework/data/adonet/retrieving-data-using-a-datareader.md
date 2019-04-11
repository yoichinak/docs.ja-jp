---
title: DataReader によるデータの取得
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 8063f239123ec1a2f2650adf9d76f7ceaaa50673
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128688"
---
# <a name="retrieve-data-using-a-datareader"></a>DataReader によるデータを取得します。
使用してデータを取得する、 **DataReader**のインスタンスを作成、**コマンド**オブジェクト、し、作成、 **DataReader**呼び出して**Command.ExecuteReader**データ ソースから行を取得します。 **DataReader**は手続き型のロジックを効率的にデータ ソースからの結果を順番に処理を可能にするデータのバッファリングされていないストリームを提供します。 **DataReader**データがメモリにキャッシュされていないために、大量のデータを取得しているときをお勧めします。

次の例を使用して、 **DataReader**ここで、`reader`は有効な datareader と`command`有効な Command オブジェクトを表します。  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

使用して、 **DataReader.Read**クエリ結果から行を取得します。 返された行の各列をアクセスするには、名前または列の序数を渡すことによって、 **DataReader**します。 ただし、最高のパフォーマンスについて、 **DataReader**一連のネイティブ データ型の列の値にアクセスできるようにするメソッドを提供します (**GetDateTime**、 **GetDouble**、 **GetGuid**、 **GetInt32**など)。 データ プロバイダーに固有の型指定されたアクセサー メソッドの一覧については**DataReaders**を参照してください<xref:System.Data.OleDb.OleDbDataReader>と<xref:System.Data.SqlClient.SqlDataReader>します。 型は、基になるデータがわかっている場合は、型指定されたアクセサー メソッドを使用して、列の値を取得するときに必要な型変換の量を減らします。  
  
 次の例を反復処理を**DataReader**オブジェクトを各行から 2 つの列を返します。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>DataReader の終了  
 常に呼び出し、**閉じる**メソッドを使用してが完了したら、 **DataReader**オブジェクト。  
  
 場合、**コマンド**の出力を含むパラメーターまたは戻り値の場合は、これらの値をまでご利用いただけません、 **DataReader**が閉じられました。  
  
 中に、 **DataReader**が開いて、**接続**によって排他的に使用されて**DataReader**します。 任意のコマンドを実行することはできません、**接続**、もう 1 つ作成を含む**DataReader**、まで、元の**DataReader**が閉じられました。  
  
> [!NOTE]
>  呼び出さないでください**閉じる**または**Dispose**上、**接続**、 **DataReader**、またはその他のマネージ オブジェクトで、 **Finalize**クラスのメソッド。 終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。 クラスがアンマネージ リソースを所有していない場合は含まれません、 **Finalize**メソッド、クラス定義にします。 詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)します。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult による複数の結果を取得する設定します。  
 場合、 **DataReader**呼び出し、複数の結果セットを返す、 **NextResult**結果を反復処理するメソッドが順番に設定します。 
  <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> の例を次に示します。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader からスキーマ情報の取得  
 中に、 **DataReader**は開くことができますを取得する設定を使用して現在の結果に関するスキーマ情報、 **GetSchemaTable**メソッド。 **GetSchemaTable**を返します、<xref:System.Data.DataTable>行と、現在の結果セットのスキーマ情報を含む列を含むオブジェクト。 **DataTable**結果セットの列ごとに 1 つの行が含まれています。 スキーマ テーブルの各列に返される列のプロパティにマップ、結果の行セットを**ColumnName**プロパティの名前であり、列の値は、プロパティの値。 次の例のスキーマ情報を書き込みます**DataReader**します。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB のチャプターの使用  
 階層的な行セット、つまりチャプター (OLE DB 型**DBTYPE_HCHAPTER**、ADO 型**adChapter**) を使用して取得できます、<xref:System.Data.OleDb.OleDbDataReader>します。 チャプターを含むクエリとして返される場合、 **DataReader**、章を内の列として返されます**DataReader**として公開されると、 **DataReader**オブジェクト。  
  
 ADO.NET**データセット**テーブル間の親子リレーションシップを使用して階層的な行セットを表すためも使用できます。 詳細については、次を参照してください。 [Dataset、Datatable、および Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)します。  
  
 MSDataShape プロバイダーを使用して、顧客リストの顧客別オーダーのチャプター列を生成するコード サンプルを次に示します。  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF Cursor による結果の取得  
 .NET Framework Data Provider for Oracle は、クエリ結果を返すために、Oracle REF CURSOR の使用をサポートしています。 Oracle REF CURSOR は <xref:System.Data.OracleClient.OracleDataReader> として返されます。  
  
 取得することができます、<xref:System.Data.OracleClient.OracleDataReader>を使用して Oracle REF CURSOR を表すオブジェクトを<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>メソッド。 指定することも、<xref:System.Data.OracleClient.OracleCommand>として 1 つまたは複数の Oracle REF Cursor を返す、 **SelectCommand**の<xref:System.Data.OracleClient.OracleDataAdapter>塗りつぶしに使用される、 <xref:System.Data.DataSet>。  
  
 Oracle データ ソースから返された REF CURSOR にアクセスするには、作成、 <xref:System.Data.OracleClient.OracleCommand> 、クエリの REF CURSOR を参照する出力パラメーターを追加し、<xref:System.Data.OracleClient.OracleCommand.Parameters>のコレクション、<xref:System.Data.OracleClient.OracleCommand>します。 パラメーターの名前は、クエリの REF CURSOR パラメーターの名前と一致させる必要があります。 設定するパラメーターの型<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>します。 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>のメソッド、<xref:System.Data.OracleClient.OracleCommand>を返します、 <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR の。  
  
 場合、<xref:System.Data.OracleClient.OracleCommand>複数の REF CURSOR を返す複数の出力パラメーターを追加します。 それぞれの REF Cursor を呼び出すことによってアクセスできる、<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>メソッド。 呼び出し<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>を返します、<xref:System.Data.OracleClient.OracleDataReader>最初の REF CURSOR を参照します。 呼び出して、<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>後続の REF Cursor にアクセスするメソッド。 では、パラメーター、<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>コレクションの一致、REF CURSOR 出力パラメーターを名前で、<xref:System.Data.OracleClient.OracleDataReader>に追加された順番にアクセスして、<xref:System.Data.OracleClient.OracleCommand.Parameters>コレクション。  
  
 たとえば、次のような Oracle パッケージとパッケージ本体があるとします。  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 次のコード作成、<xref:System.Data.OracleClient.OracleCommand>型の 2 つのパラメーターを追加することで、前のバージョンの Oracle パッケージから REF Cursor を返す<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>を<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>コレクション。  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 次のコードを使用して前のコマンドの結果を返します、<xref:System.Data.OracleClient.OracleDataReader.Read>と<xref:System.Data.OracleClient.OracleDataReader.NextResult>のメソッド、<xref:System.Data.OracleClient.OracleDataReader>します。 REF CURSOR パラメーターは順番に返されます。  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 次の例では、前のコマンドを使用して、事前設定、 <xref:System.Data.DataSet> Oracle パッケージの結果。  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```

> [!NOTE]
>  回避するために、 **OverflowException**、有効な .NET Framework 型に値を格納する前に、Oracle の NUMBER 型から変換を処理することをお勧め、 <xref:System.Data.DataRow>。 使用することができます、<xref:System.Data.Common.DataAdapter.FillError>イベントかどうかを**OverflowException**が発生しました。 詳細については、<xref:System.Data.Common.DataAdapter.FillError>イベントを参照してください[DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)します。  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

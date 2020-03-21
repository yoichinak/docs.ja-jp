---
title: DataReader によるデータの取得
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149025"
---
# <a name="retrieve-data-using-a-datareader"></a>データ リーダーを使用してデータを取得する
**DataReader**を使用してデータを取得するには、**コマンド**オブジェクトのインスタンスを作成し **、Command.ExecuteReader**を呼び出してデータ ソースから行を取得して**DataReader**を作成します。 **DataReader**は、データ ソースからの結果を効率的に処理する手続きロジックを可能にするデータのバッファリングされていないストリームを提供します。 **データリーダー**は、大量のデータがメモリにキャッシュされないために、大量のデータを取得する場合に適しています。

次の例では、有効な**DataReader**`reader`を表し、`command`有効なコマンド オブジェクトを表す DataReader を使用する方法を示します。  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

クエリ結果から行を取得するには **、DataReader.Read**メソッドを使用します。 返された行の各列にアクセスするには、列の名前または序数を**DataReader**に渡します。 ただし、最高のパフォーマンスを得るために **、DataReader**には、ネイティブ データ型 **(GetDateTime** **、GetDouble、GetGuid** **、GetInt32**など) の列値にアクセスできる一連のメソッドが用意されています。 **GetGuid** データ プロバイダ固有の**DataReader**の型指定されたアクセサー<xref:System.Data.OleDb.OleDbDataReader>メソッド<xref:System.Data.SqlClient.SqlDataReader>の一覧については、および を参照してください。 基になるデータ型がわかっている場合に型指定されたアクセサー メソッドを使用すると、列値を取得するときに必要な型変換の量が減少します。  
  
 次の例では **、DataReader**オブジェクトを反復処理し、各行から 2 つの列を返します。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>DataReader の終了  
 **DataReader**オブジェクトの使用が完了したら、必ず**Close**メソッドを呼び出してください。  
  
 **コマンド**に出力パラメータまたは戻り値が含まれている場合 **、DataReader**を閉じるまでこれらの値は使用できません。  
  
 データ**リーダー**が開いている間、**接続**はその**DataReader**によって排他的に使用されます。 元の**DataReader**を閉じるまでは、別の**DataReader**を作成するなど、**接続**に対してコマンドを実行することはできません。  
  
> [!NOTE]
> クラスの**Finalize**メソッドで、**接続** **、DataReader、** またはその他のマネージ オブジェクトで**Close**または**Dispose**を呼び出す必要はありません。 終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。 クラスがアンマネージ リソースを所有していない場合は、クラス定義に**Finalize**メソッドを含めないでください。 詳細については、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」を参照してください。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult を使用して複数の結果セットを取得する  
 **DataReader**が複数の結果セットを返す場合は **、NextResult**メソッドを呼び出して結果セットを順番に反復処理します。 <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> の例を次に示します。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>データ リーダーからのスキーマ情報の取得  
 データ**リーダー**が開いている間は **、GetSchemaTable**メソッドを使用して、現在の結果セットに関するスキーマ情報を取得できます。 **GetSchemaTable**は<xref:System.Data.DataTable>、現在の結果セットのスキーマ情報を含む行と列が設定されたオブジェクトを返します。 **DataTable には**、結果セットの各列に対して 1 行が含まれます。 スキーマ テーブルの各列は、結果セットの行に返される列のプロパティにマップされます。 **ColumnName** 次の例では **、DataReader**のスキーマ情報を書き出します。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB の章の使用  
 階層行セットまたは章 ( OLE DB の種類**DBTYPE_HCHAPTER**、 ADO の種類<xref:System.Data.OleDb.OleDbDataReader>**adChapter**) は、 を使用して取得できます。 章を含むクエリが**DataReader**として返されると、そのチャプターはその**DataReader**の列として返され **、DataReader**オブジェクトとして公開されます。  
  
 ADO.NET **DataSet**は、テーブル間の親子リレーションシップを使用して階層行セットを表すためにも使用できます。 詳細については、「[データセット、データ テーブル、およびデータ ビュー](./dataset-datatable-dataview/index.md)」を参照してください。  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>オラクル REF の CURSORS で結果を返す  
 .NET Framework Data Provider for Oracle は、クエリ結果を返すために、Oracle REF CURSOR の使用をサポートしています。 Oracle REF CURSOR は <xref:System.Data.OracleClient.OracleDataReader> として返されます。  
  
 メソッドを使用して<xref:System.Data.OracleClient.OracleDataReader>、Oracle REF CURSOR を表す<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>オブジェクトを取得できます。 また、 を<xref:System.Data.OracleClient.OracleCommand>埋めるために<xref:System.Data.OracleClient.OracleDataAdapter>使用されるコマンドの**選択コマンド**として 1 つ以上の Oracle REF の<xref:System.Data.DataSet>CUROR を返す を指定することもできます。  
  
 Oracle データ ソースから返された REF CURSOR に<xref:System.Data.OracleClient.OracleCommand>アクセスするには、クエリ用の を作成し、REF CURSOR<xref:System.Data.OracleClient.OracleCommand.Parameters>を参照する<xref:System.Data.OracleClient.OracleCommand>出力パラメータを. パラメーターの名前は、クエリの REF CURSOR パラメーターの名前と一致させる必要があります。 パラメータの型を<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>に設定します。 REF<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType><xref:System.Data.OracleClient.OracleCommand>カーソルのメソッドは<xref:System.Data.OracleClient.OracleDataReader>、を返します。  
  
 複数の<xref:System.Data.OracleClient.OracleCommand>REF CURSORS を返す場合は、複数の出力パラメーターを追加します。 メソッドを呼び出すことによって、異なる REF <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> CURSORs にアクセスできます。 呼び出<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>しは<xref:System.Data.OracleClient.OracleDataReader>、参照元の最初の REF カーソルを返します。 その後、このメソッド<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>を呼び出して、後続の REF CURSOR にアクセスできます。 <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>コレクション内のパラメーターは REF CURSOR 出力パラメーターを名前で一<xref:System.Data.OracleClient.OracleDataReader>致させますが、パラメーターはコレクションに追加された順序でアクセス<xref:System.Data.OracleClient.OracleCommand.Parameters>します。  
  
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
  
 次のコードでは、<xref:System.Data.OracleClient.OracleCommand><xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>前の Oracle パッケージから REF CURSORs を返すを<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>作成します。  
  
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
  
 次のコードは、 の<xref:System.Data.OracleClient.OracleDataReader.Read>メソッドと<xref:System.Data.OracleClient.OracleDataReader.NextResult>メソッドを使用して、<xref:System.Data.OracleClient.OracleDataReader>前のコマンドの結果を返します。 REF CURSOR パラメーターは順番に返されます。  
  
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
  
 次の例では、前のコマンドを使用<xref:System.Data.DataSet>して、Oracle パッケージの結果を a に入力します。  
  
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
> **OverflowException**を避けるには、値を に格納する前に、Oracle NUMBER 型から有効な .NET Framework 型<xref:System.Data.DataRow>への変換も処理することをお勧めします。 イベントを<xref:System.Data.Common.DataAdapter.FillError>使用して **、OverflowException**が発生したかどうかを判断できます。 イベントの<xref:System.Data.Common.DataAdapter.FillError>詳細については、「 [DataAdapter イベントの処理](handling-dataadapter-events.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [コマンドおよびパラメーター](commands-and-parameters.md)
- [データベース スキーマ情報の取得](retrieving-database-schema-information.md)
- [ADO.NET の概要](ado-net-overview.md)

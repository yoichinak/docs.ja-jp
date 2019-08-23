---
title: DataReader によるデータの取得
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 561ebd7ac6948fa42f73ebb4f1eb97c574e6d7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963184"
---
# <a name="retrieve-data-using-a-datareader"></a>DataReader を使用してデータを取得する
**Datareader**を使用してデータを取得するには、 **command**オブジェクトのインスタンスを作成した後、 **ExecuteReader**を呼び出してデータソースから行を取得し、 **datareader**を作成します。 **DataReader**は、バッファリングされていないデータストリームを提供します。これにより、手続き型のロジックによって、データソースからの結果を順番に効率的に処理できます。 データがメモリにキャッシュされないため、大量のデータを取得する場合は、 **DataReader**を使用することをお勧めします。

`command` Datareader`reader`を使用する例を次に示します。は有効な datareader を表し、は有効な Command オブジェクトを表します。  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

クエリ結果から行を取得するには、 **DataReader. Read**メソッドを使用します。 返された行の各列には、列の名前または序数を**DataReader**に渡すことによってアクセスできます。 ただし、最適なパフォーマンスを得るために、 **DataReader**には、ネイティブデータ型 (**getdatetime**、 **getdatetime**、 **getdatetime**、 **GetInt32**など) の列値にアクセスできる一連のメソッドが用意されています。 データプロバイダー固有の**datareader**の型指定されたアクセサーメソッドの一覧<xref:System.Data.OleDb.OleDbDataReader>については、「」および<xref:System.Data.SqlClient.SqlDataReader>「」を参照してください。 基になるデータ型がわかっている場合は、型指定されたアクセサーメソッドを使用して、列の値を取得するときに必要な型変換の量を減らします。  
  
 次の例では、 **DataReader**オブジェクトを反復処理し、各行から2つの列を返します。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>DataReader の終了  
 **DataReader**オブジェクトの使用が終了したら、常に**Close**メソッドを呼び出します。  
  
 **コマンド**に出力パラメーターまたは戻り値が含まれている場合、これらの値は**DataReader**が閉じられるまで使用できません。  
  
 **Datareader**が開いている間は、その**datareader**によって**接続**が排他的に使用されています。 元の**datareader**が閉じられるまで、**接続**のコマンド (別の**datareader**の作成を含む) を実行することはできません。  
  
> [!NOTE]
> クラスの**Finalize**メソッドで、**接続**、 **DataReader**、またはその他のマネージオブジェクトに対して**Close**または**Dispose**を呼び出さないでください。 終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。 クラスがアンマネージリソースを所有していない場合は、クラス定義に**Finalize**メソッドを含めないでください。 詳細については、「[ガベージコレクション](../../../standard/garbage-collection/index.md)」を参照してください。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult を使用して複数の結果セットを取得する  
 **DataReader**から複数の結果セットが返された場合は、 **nextresult**メソッドを呼び出して、結果セットを順番に反復処理します。 <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> の例を次に示します。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader からのスキーマ情報の取得  
 **DataReader**が開いている間は、 **getschematable**メソッドを使用して、現在の結果セットに関するスキーマ情報を取得できます。 **Getschematable**は、 <xref:System.Data.DataTable>現在の結果セットのスキーマ情報を含む行と列を含むオブジェクトを返します。 DataTable には、結果セットの列ごとに1行の**データ**が格納されます。 スキーマテーブルの各列は、結果セットの行で返される列のプロパティにマップされます。ここで、 **ColumnName**はプロパティの名前、列の値はプロパティの値です。 次の例では、 **DataReader**のスキーマ情報を書き込みます。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB の章を操作する  
 階層型の行セット、つまりチャプター (OLE DB type **DBTYPE_HCHAPTER**、ADO 型**adchapter**) は、 <xref:System.Data.OleDb.OleDbDataReader>を使用して取得できます。 チャプターを含むクエリが**datareader**として返された場合、チャプターはその**datareader**の列として返され、 **datareader**オブジェクトとして公開されます。  
  
 ADO.NET**データセット**を使用すると、テーブル間の親子リレーションシップを使用して、階層的な行セットを表すこともできます。 詳細については、「[データセット、datatable、および DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)」を参照してください。  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF cursor を使用して結果を返す  
 .NET Framework Data Provider for Oracle は、クエリ結果を返すために、Oracle REF CURSOR の使用をサポートしています。 Oracle REF CURSOR は <xref:System.Data.OracleClient.OracleDataReader> として返されます。  
  
 Oracle REF カーソルを<xref:System.Data.OracleClient.OracleDataReader>表すオブジェクトを取得するには、 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>メソッドを使用します。 にデータを格納<xref:System.Data.OracleClient.OracleCommand> するため<xref:System.Data.OracleClient.OracleDataAdapter>に使用されるの**SelectCommand**として1つ以上の Oracle REF cursor を返すを指定することもできます。<xref:System.Data.DataSet>  
  
 Oracle データソースから返された ref カーソルにアクセスするには<xref:System.Data.OracleClient.OracleCommand> 、クエリのを作成し、ref カーソル<xref:System.Data.OracleClient.OracleCommand.Parameters>を参照する出力パラメーターをの<xref:System.Data.OracleClient.OracleCommand>コレクションに追加します。 パラメーターの名前は、クエリの REF CURSOR パラメーターの名前と一致させる必要があります。 パラメーターの型をに<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>設定します。 のメソッドは<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> 、REF カーソル<xref:System.Data.OracleClient.OracleDataReader>のを返します。<xref:System.Data.OracleClient.OracleCommand>  
  
 が複数の REF cursorを返す場合は、複数の出力パラメーターを追加します。<xref:System.Data.OracleClient.OracleCommand> 異なる REF カーソルにアクセスするには、 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>メソッドを呼び出します。 の呼び出し<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>は、最初<xref:System.Data.OracleClient.OracleDataReader>の REF カーソルを参照するを返します。 その後、メソッドを<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>呼び出して、後続の REF カーソルにアクセスできます。 <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>コレクション内のパラメーターは、REF CURSOR 出力パラメーターと名前で一致します<xref:System.Data.OracleClient.OracleDataReader>が、は<xref:System.Data.OracleClient.OracleCommand.Parameters>コレクションに追加された順序でこれらのパラメーターにアクセスします。  
  
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
  
 次のコードは、 <xref:System.Data.OracleClient.OracleCommand>型<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>の2つのパラメーターを<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>コレクションに追加することによって、以前の Oracle パッケージから参照カーソルを返すを作成します。  
  
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
  
 次のコードは、 <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader>のメソッドと<xref:System.Data.OracleClient.OracleDataReader.NextResult>メソッドを使用して、前のコマンドの結果を返します。 REF CURSOR パラメーターは順番に返されます。  
  
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
  
 次の例では、前のコマンドを<xref:System.Data.DataSet>使用して、Oracle パッケージの結果をに設定します。  
  
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
> **OverflowException**を回避するには、に値<xref:System.Data.DataRow>を格納する前に、Oracle の数値型から有効な .NET Framework 型への変換も処理することをお勧めします。 イベントを使用し<xref:System.Data.Common.DataAdapter.FillError>て、 **OverflowException**が発生したかどうかを判断できます。 <xref:System.Data.Common.DataAdapter.FillError>イベントの詳細については、「 [DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

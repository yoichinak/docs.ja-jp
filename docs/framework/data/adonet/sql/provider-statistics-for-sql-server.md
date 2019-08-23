---
title: SQL Server のプロバイダー統計情報
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: e13c4df87909629a45830e3b7950551434ed5ab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946584"
---
# <a name="provider-statistics-for-sql-server"></a>SQL Server のプロバイダー統計情報
.NET Framework version 2.0 以降では、.NET Framework Data Provider for SQL Server によって実行時の統計がサポートされています。 統計情報を有効にするには、有効な接続オブジェクトを作成した後で、<xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを `True` に設定する必要があります。 統計情報が有効にされると、<xref:System.Collections.IDictionary> オブジェクトの <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> メソッドを通じて <xref:System.Data.SqlClient.SqlConnection> 参照を取得することにより、"時間単位のスナップショット" として統計情報を確認できます。 名前と値がペアになったディクショナリ エントリのセットとして、一覧を列挙します。 これらの名前と値のペアは順序付けられていません。 いつでも <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> メソッドを呼び出して、カウンターをリセットすることができます。 統計情報収集が有効になっていない場合、例外は生成されません。 また、<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> が最初に呼び出されるずに <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> が呼び出されると、取得される値は各エントリの初期値になります。 統計情報を有効にしてからアプリケーションをしばらく実行した後で統計情報を無効にした場合、取得される値には、統計情報が無効にされた時点までに収集された値が含まれます。 すべての統計情報の値は、接続ごとに収集されます。  
  
## <a name="statistical-values-available"></a>使用できる統計情報の値  
 現在、Microsoft SQL Server プロバイダーから使用できる項目は 18 種類あります。 使用できる項目の数には、によって返される<xref:System.Collections.IDictionary>インターフェイス参照の Count プロパティ<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>を使用してアクセスできます。 プロバイダー統計のすべてのカウンターは、共通言語ランタイム<xref:System.Int64>型 (**long** in C#と Visual Basic) を使用します。これは64ビット幅です。 Int64 で定義されている**int64**データ型の最大値 **。MaxValue**フィールド、は ((2 ^ 63)-1)) です。 カウンターの値がこの最大値に達すると、これ以降カウンターは正確ではないと見なされます。 これは、int64 であることを意味**します。MaxValue**-1 ((2 ^ 63)-2) は、事実上、任意の統計の有効な最大値です。  
  
> [!NOTE]
> プロバイダーの統計情報を返すためにディクショナリが使用されているのは、返される統計情報の数値、名前、および順序が今後変更される可能性があるためです。 アプリケーションでは、ディクショナリ内で見つかった特定の値に依存する必要はありませんが、値が存在するかどうかや、この値に応じて分岐させるかどうかを確認する必要があります。  
  
 次の表では、使用可能な現在の統計情報の値が説明されています。 個々の値のキー名は、Microsoft .NET Framework の地域別バージョン全体でローカライズされているわけではないことに注意してください。  
  
|キー名|説明|  
|--------------|-----------------|  
|`BuffersReceived`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーが SQL Server から受け取る、表形式のデータ ストリーム (TDS) パケットの数を返します。|  
|`BuffersSent`|統計情報が有効になった後に、プロバイダーにより SQL Server に送信された TDS パケットの数を返します。 大量の処理を伴うコマンドでは、複数のバッファーが必要になります。 たとえば、大きなコマンドがサーバーに送信され、6 つのパケットが必要になる場合は、`ServerRoundtrips` は 1 だけインクリメントされ、`BuffersSent` は 6 だけインクリメントされます。|  
|`BytesReceived`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーが SQL Server から受け取る、TDS パケット内のデータのバイト数を返します。|  
|`BytesSent`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に TDS パケット内の SQL Server に送信される、データのバイト数を返します。|  
|`ConnectionTime`|統計情報が有効になった後に接続が開かれている時間 (ミリ秒) を示します (接続が開かれる前に統計情報が有効になっていた場合は、合計接続時間を示します)。|  
|`CursorOpens`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて行われた、カーソルが開かれた回数を返します。<br /><br /> SELECT ステートメントにより返される読み取り専用/前方参照専用の結果は、カーソルが考慮されないため、このカウンターには影響しません。|  
|`ExecutionTime`|統計情報が有効になってから、プロバイダーが処理に費やした累計時間 (ミリ秒) を返します。この時間には、サーバーからの応答を待つために費やされた時間と、プロバイダー自体がコードを実行するために費やした時間が含まれます。<br /><br /> タイミング コードが含まれるクラスは次のとおりです。<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> パフォーマンスが重視されるメンバーをできるだけ小規模に保つため、次のメンバーは時刻指定されません。<br /><br /> SqlDataReader<br /><br /> this[] operator (all overloads)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された、INSERT、DELETE、および UPDATE ステートメントの合計数を返します。|  
|`IduRows`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された INSERT、DELETE、および UPDATE ステートメントにより影響を受けた、行の合計数を返します。|  
|`NetworkServerTime`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーがサーバーからの応答を待つために費やした累計時間 (ミリ秒) を返します。|  
|`PreparedExecs`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された、準備コマンドの数を返します。|  
|`Prepares`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて準備された、ステートメントの数を返します。|  
|`SelectCount`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された、SELECT ステートメントの数を返します。 これには、カーソルから行を取得するための FETCH ステートメントが含まれます。SELECT ステートメントのカウントは、<xref:System.Data.SqlClient.SqlDataReader> の末尾に達すると更新されます。|  
|`SelectRows`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に選択された、行の数を返します。 このカウンターは、実際には呼び出し元により使用されなかった行を含め、SQL ステートメントにより生成されたすべての行を反映します。 たとえば、結果セット全体を読み取る前にデータ リーダーを閉じても、カウントには影響しません。 これには、FETCH ステートメントを通じてカーソルから取得された行が含まれます。|  
|`ServerRoundtrips`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に発生した、接続がサーバーにコマンドを送信して応答を受け取った回数を返します。|  
|`SumResultSets`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に使用された、結果セットの数を返します。 たとえば、これにはクライアントに返されるすべての結果セットが含まれます。 カーソルについては、それぞれのフェッチ操作やブロック フェッチ操作は、単独の結果セットと見なされます。|  
|`Transactions`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に開始された、ユーザー トランザクションの数を返します。これにはロールバックが含まれます。 自動コミットがオンの状態で接続が実行されている場合、各コマンドはトランザクションと見なされます。<br /><br /> このカウンターは、トランザクションがコミットされるかどうか、または後にロール バックされるかどうかに関係なく、BEGIN TRAN ステートメントが実行された直後に、トランザクション カウントをインクリメントします。|  
|`UnpreparedExecs`|アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて準備解除された、ステートメントの数を返します。|  
  
### <a name="retrieving-a-value"></a>値の取得  
 次のコンソール アプリケーションは、接続で統計情報を有効にして、4 つの各統計情報の値を取得し、コンソール ウィンドウに出力する方法を示します。  
  
> [!NOTE]
> 次の例では、SQL Server に含まれるサンプルの**AdventureWorks**データベースを使用します。 サンプル コードの接続文字列は、データベースがローカルのコンピューターにインストールされて利用可能な状態になっていることを前提としています。 必要に応じて、お使いの環境に合わせて接続文字列を変更してください。  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>すべての値の取得  
 次のコンソール アプリケーションは、接続で統計情報を有効にし、使用可能なすべての統計情報の値を列挙子を使って取得して、コンソール ウィンドウに出力する方法を示します。  
  
> [!NOTE]
> 次の例では、SQL Server に含まれるサンプルの**AdventureWorks**データベースを使用します。 サンプル コードの接続文字列は、データベースがローカルのコンピューターにインストールされて利用可能な状態になっていることを前提としています。 必要に応じて、お使いの環境に合わせて接続文字列を変更してください。  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)

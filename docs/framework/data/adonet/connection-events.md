---
title: 接続イベント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: e958c96e304962dace72e90b9266b57943f01ac9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785736"
---
# <a name="connection-events"></a>接続イベント
すべての .NET Framework データプロバイダーには、データソースから情報メッセージを取得したり、**接続**の状態が変更されたかどうかを確認したりするために使用できる、2つのイベントを持つ**接続**オブジェクトがあります。 次の表では、**接続**オブジェクトのイベントについて説明します。  
  
|イベント|説明|  
|-----------|-----------------|  
|**InfoMessage**|データ ソースから情報メッセージが返されたときに発生します。 情報メッセージはデータ ソースからのメッセージであり、例外はスローされません。|  
|**StateChange**|**接続**の状態が変化したときに発生します。|  
  
## <a name="working-with-the-infomessage-event"></a>InfoMessage イベントの使用  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> イベントを使用して、SQL Server データ ソースから警告や情報メッセージを取得できます。 重大度レベルが 11 から 16 のエラーがデータ ソースから返されると、例外がスローされます。 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを使用して、エラーに関連付けられていないメッセージをデータ ソースから取得することもできます。 Microsoft SQL Server の場合は、重大度レベルが 10 以下のエラーは情報メッセージと見なされ、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントでキャプチャされます。 詳細については、[データベースエンジンエラーの重大度](/sql/relational-databases/errors-events/database-engine-error-severities)に関する記事を参照してください。
  
 イベント<xref:System.Data.SqlClient.SqlConnection.InfoMessage>は、その<xref:System.Data.SqlClient.SqlInfoMessageEventArgs> **Errors**プロパティに、データソースからのメッセージのコレクションを含むオブジェクトを受け取ります。 エラー番号とメッセージテキスト、およびエラーの原因については、このコレクション内の**error**オブジェクトに対してクエリを実行できます。 .NET Framework Data Provider for SQL Server には、データベースの詳細情報、ストアド プロシージャ、およびメッセージ送信元の行番号も含まれます。  
  
### <a name="example"></a>例  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントのイベント ハンドラーを追加する方法を次のコード サンプルに示します。  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>InfoMessages としてのエラー処理  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントは通常、サーバーが情報メッセージまたは警告メッセージを送信した場合に限り発生します。 ただし、実際のエラーが発生すると、サーバー操作を開始した**ExecuteNonQuery**または**ExecuteReader**メソッドの実行が停止し、例外がスローされます。  
  
 サーバーでエラーが発生してもコマンド内の残りのステートメントの処理を続行する場合は、<xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> の <xref:System.Data.SqlClient.SqlConnection> プロパティを `true` に設定します。 このように設定すると、エラーが発生したとき、接続は例外をスローして処理を中断する代わりに、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを発生させます。 クライアント アプリケーションは、このイベントを処理し、エラーに応答できます。  
  
> [!NOTE]
> 重大度レベルが 17 以上のエラーが発生すると、サーバーのコマンド処理が停止します。このエラーは、例外として処理する必要があります。 この場合、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントによるエラー処理の方法にかかわらず例外がスローされます。  
  
## <a name="working-with-the-statechange-event"></a>StateChange イベントの使用  
 **StateChange**イベントは、**接続**の状態が変化したときに発生します。 **StateChange**イベントは、 <xref:System.Data.StateChangeEventArgs> **originalstate** **プロパティと**設定されたプロパティを使用して、**接続**の状態の変化を確認できるようにを受け取ります。 **Originalstate**プロパティは、変更<xref:System.Data.ConnectionState>前の**接続**の状態を示す列挙体です。 "状態 **" は、** 変更後の<xref:System.Data.ConnectionState> **接続**の状態を示す列挙体です。  
  
 次のコード例では、 **StateChange**イベントを使用して、**接続**の状態が変化したときにコンソールにメッセージを書き込みます。  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>関連項目

- [データ ソースへの接続](connecting-to-a-data-source.md)
- [ADO.NET の概要](ado-net-overview.md)

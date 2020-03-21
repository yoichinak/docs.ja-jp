---
title: 複数のアクティブな結果セットの有効化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 72125be835298218e5445fe1915d6a17f5008bb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148726"
---
# <a name="enabling-multiple-active-result-sets"></a>複数のアクティブな結果セットの有効化
複数のアクティブな結果セット (MARS : Multiple Active Result Set) は、SQL Server で動作する機能であり、複数のバッチを単一の接続で実行することができます。 SQL Server で使用できるように MARS が有効になっているときは、使用中の各コマンド オブジェクトは接続にセッションを追加します。  
  
> [!NOTE]
> 1 つの MARS セッションは、MARS が使用する 1 つの論理接続を開いた後、アクティブなコマンドごとに 1 つの論理接続を開きます。  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>接続文字列で MARS を有効または無効にする  
  
> [!NOTE]
> 次の接続文字列では、SQL Server に含まれるサンプルの **AdventureWorks** データベースを使用します。 指定されている接続文字列は、データベースが MSSQL1 という名前のサーバーにインストールされているものとします。 実際の環境の必要に応じて接続文字列を変更してください。  
  
 MARS 機能は、既定では無効化されています。 これは、接続文字列に "MultipleActiveResultSets=True" キーワード ペアを追加することによって有効にできます。 "True" は、MARS を有効にするための唯一の有効な値です。 次の例は、SQL Server のインスタンスに接続する方法、および MARS を有効にすることを指定する方法を示しています。  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 MARS は、接続文字列に "MultipleActiveResultSets=False" キーワード ペアを追加することによって無効にできます。 "False" は、MARS を無効にするための唯一の有効な値です。 次の接続文字列は、MARS を無効にする方法を示しています。  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>MARS の使用に関する特記事項  
 一般に、MARS が有効な接続を使用するために既存のアプリケーションを変更する必要はありません。 ただし、アプリケーションで MARS 機能を使用する場合は、次の特別な考慮事項を理解しておく必要があります。  
  
### <a name="statement-interleaving"></a>ステートメント インタリーブ  
 MARS 操作は、サーバー上で同期的に実行されます。 SELECT および BULK INSERT ステートメントのステートメントのインターリーブが許可されます。 ただし、データ操作言語 (DML) およびデータ定義言語 (DDL) ステートメントはアトミックに実行されます。 アトミック バッチの実行中にステートメントを実行しようとすると、すべてブロックされます。 サーバーでの並列実行は MARS 機能ではありません。  
  
 MARS 接続のもとで 2 つのバッチが送信され、そのうちの 1 つに SELECT ステートメントが含まれ、もう一方に DML ステートメントが含まれている場合は、SELECT ステートメントの実行内で DML の実行を開始できます。 ただし、SELECT ステートメントが先に進むには、DML ステートメントが実行を完了する必要があります。 両方のステートメントが同じトランザクションのもとで実行されている場合、SELECT ステートメントが実行を開始した後で DML ステートメントが行ったすべての変更は読み取り操作に表示されません。  
  
 SELECT ステートメント内の WAITFOR ステートメントは、待機中、つまり最初の行が生成されるまではトランザクションを生成しません。 これは、WAITFOR ステートメントが待機中の場合、同じ接続内では他のどのバッチも実行できないことを示しています。  
  
### <a name="mars-session-cache"></a>MARS セッションのキャッシュ  
 MARS が有効な状態で接続が開かれている場合は、論理セッションが作成され、それによってオーバーヘッドが追加されます。 オーバーヘッドを最小化してパフォーマンスを向上させるため、**SqlClient** は接続内の MARS セッションをキャッシュします。 このキャッシュには、最大で 10 個の MARS セッションが含まれます。 この値をユーザーが調整することはできません。 セッションの制限に達した場合は、新しいセッションが作成され、エラーは生成されません。 キャッシュとそこに含まれているセッションは接続ごとに保持され、接続間では共有されません。 セッションが解放されると、プールの上限に達していない限り、そのセッションはプールに返されます。 キャッシュ プールがいっぱいになると、セッションは閉じられます。 MARS セッションに有効期限はありません。 これらは、接続オブジェクトが破棄された場合にのみクリーンアップされます。 MARS セッションのキャッシュは事前には読み込まれません。 これは、アプリケーションでさらに多くのセッションが必要になったときに読み込まれます。  
  
### <a name="thread-safety"></a>スレッド セーフ  
 MARS 操作はスレッドセーフではありません。  
  
### <a name="connection-pooling"></a>接続のプール  
 MARS が有効な接続は、他のすべての接続と同様にプールされます。 アプリケーションが MARS が有効な接続と MARS が無効な接続の 2 つの接続を開いた場合、これらの 2 つの接続は別のプールに入れられます。 詳細については、「[SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md)」(SQL Server の接続プーリング (ADO.NET)) をご覧ください。  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server のバッチ実行環境  
 接続が開かれると、既定の環境が定義されます。 その後、この環境が論理 MARS セッションにコピーされます。  
  
 バッチ実行環境には、次のコンポーネントが含まれています。  
  
- Set オプション (ANSI_NULLS、DATE_FORMAT、LANGUAGE、TEXTSIZE など)  
  
- セキュリティ コンテキスト (ユーザー/アプリケーション ロール)  
  
- データベース コンテキスト (現在のデータベース)  
  
- 実行状態変数 (@@ERROR、@@ROWCOUNT、@@FETCH_STATUS @@IDENTITY など)  
  
- 最上位レベルの一時テーブル  
  
 MARS では、既定の実行環境が接続に関連付けられています。 特定の接続の下で実行を開始するすべての新しいバッチは、既定の環境のコピーを受け取ります。 特定のバッチのもとでコードが実行された場合は、常に環境に加えられたすべての変更がその特定のバッチにスコープ指定されます。 実行が完了すると、実行設定が既定の環境にコピーされます。 同じトランザクションで順に実行される複数のコマンドを 1 つのバッチが発行している場合、セマンティクスは、以前のクライアントまたはサーバーに関連した接続によって公開されるものと同じです。  
  
### <a name="parallel-execution"></a>並列実行  
 MARS は、1 つのアプリケーション内の複数の接続に関するすべての要件を削除するようには設計されていません。 あるアプリケーションで、サーバーに対するコマンドの真の並列実行が必要な場合は、複数の接続を使用する必要があります。  
  
 たとえば、次のシナリオについて考えてみましょう。 結果セットを処理するためのコマンド オブジェクトと、データを更新するための別のコマンド オブジェクトの 2 つが作成されます。これらは、MARS 経由で共通の接続を共有します。 最初のコマンド オブジェクトの結果をすべて読み取るまで、`Transaction`.`Commit` による 更新に失敗し、次の例外が発生します。  
  
 メッセージ: トランザクション コンテキストを他のセッションが使用中です。  
  
 ソース: .NET Sql クライアント データ プロバイダー  
  
 期待値: (null)  
  
 受信: System.Data.SqlClient.SqlException  
  
 このシナリオを処理するためのオプションとして、次の 3 つがあります。  
  
1. リーダーが作成された後にトランザクションを開始し、それがトランザクションの一部にならないようにします。 それにより、すべての更新が独自のトランザクションになります。  
  
2. リーダーが終了した後ですべての作業をコミットします。 この場合は、大量の更新バッチが生成される可能性があります。  
  
3. MARS は使用しません。代わりに、MARS の前に行っていたように、コマンド オブジェクトごとに個別の接続を使用します。  
  
### <a name="detecting-mars-support"></a>MARS サポートの検出  
 アプリケーションは、`SqlConnection.ServerVersion` 値を読み取ることによって MARS のサポートを確認します。 メジャー番号は、SQL Server 2005 の場合は 9、SQL Server 2008 の場合は 10 です。  
  
## <a name="see-also"></a>関連項目

- [複数のアクティブな結果セット (MARS)](multiple-active-result-sets-mars.md)
- [ADO.NET の概要](../ado-net-overview.md)

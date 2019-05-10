---
title: サービス トランザクションの動作
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 63d7fed125396e809eb2cba89663db73a56f7cec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753037"
---
# <a name="service-transaction-behavior"></a>サービス トランザクションの動作

このサンプルでは、クライアント調整トランザクションの使用方法と、サービス トランザクションの動作を制御する ServiceBehaviorAttribute と OperationBehaviorAttribute の設定方法について説明します。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスの実装が、データベース テーブルと合計電卓操作を実行しているステートフルに実行された操作のサーバー ログを保持するように拡張します。 サーバー ログ テーブルへの書き込みを保存するかどうかは、クライアント調整トランザクションの結果によって異なります。クライアント トランザクションが完了しない場合は、Web サービス トランザクションにより、データベースへの更新はコミットされません。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

サービスのコントラクトでは、すべての操作でトランザクションを要求に応じてフローする必要があることを、次のように定義します。

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",
                    SessionMode = SessionMode.Required)]
public interface ICalculator
{
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Add(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Subtract(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Multiply(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Divide(double n);
}
```

受信トランザクション フローを有効にするには、transactionFlow 属性が `true` に設定されているシステム指定の wsHttpBinding を使用して、サービスを構成します。 このバインディングは、相互操作可能な WSAtomicTransactionOctober2004 プロトコルを使用します。

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

サービスへの接続とトランザクションの起動後、クライアントは次のようにそのトランザクションのスコープに含まれるいくつかのサービス処理にアクセスして、そのトランザクションを完了して接続を終了します。

```csharp
// Create a client
CalculatorClient client = new CalculatorClient();

// Create a transaction scope with the default isolation level of Serializable
using (TransactionScope tx = new TransactionScope())
{
    Console.WriteLine("Starting transaction");

    // Call the Add service operation.
    double value = 100.00D;
    Console.WriteLine("  Adding {0}, running total={1}",
                                        value, client.Add(value));

    // Call the Subtract service operation.
    value = 45.00D;
    Console.WriteLine("  Subtracting {0}, running total={1}",
                                        value, client.Subtract(value));

    // Call the Multiply service operation.
    value = 9.00D;
    Console.WriteLine("  Multiplying by {0}, running total={1}",
                                        value, client.Multiply(value));

    // Call the Divide service operation.
    value = 15.00D;
    Console.WriteLine("  Dividing by {0}, running total={1}",
                                        value, client.Divide(value));

    Console.WriteLine("  Completing transaction");
    tx.Complete();
}

Console.WriteLine("Transaction committed");

// Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

サービス側には、次のようにサービス トランザクションの動作に影響を及ぼす 3 つの属性があります。

- `ServiceBehaviorAttribute` :

  - `TransactionTimeout` プロパティは、トランザクションが完了する必要のある期間を指定します。 このサンプルでは、30 秒に設定されています。

  - `TransactionIsolationLevel` プロパティは、サービスがサポートする分離レベルを指定します。 クライアントの分離レベルと一致する必要があります。

  - `ReleaseServiceInstanceOnTransactionComplete` プロパティは、トランザクションが完了したときにサービス インスタンスを再利用するかどうかを指定します。 `false` に設定すると、サービスは操作要求全体で同じサービス インスタンスを保持します。 この設定は、現在高を保持するために必要です。 `true` に設定すると、各アクションが完了するたびに新しいインスタンスが生成されます。

  - `TransactionAutoCompleteOnSessionClose` プロパティは、セッションの終了時に未解決のトランザクションを完了するかどうかを指定します。 設定することで`false`、個別の操作で設定するか、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType>プロパティを`true`への呼び出しを明示的に要求するか、<xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType>メソッドがトランザクションを完了します。 このサンプルでは、両方の方法を示します。

- `ServiceContractAttribute` :

  - `SessionMode` プロパティは、適切な要求を相互に関連付けて論理セッションに格納するかどうかを指定します。 このサービスには、OperationBehaviorAttribute TransactionAutoComplete プロパティが `false` に設定されている操作 (乗算および除算) が含まれているため、`SessionMode.Required` を指定する必要があります。 たとえば、乗算操作ではトランザクションは完了せず、後で呼び出される除算操作により、`SetTransactionComplete` メソッドを使用して完了します。したがってこのサービスでは、これらの操作が同じセッション内で発生するかどうかを決定できる必要があります。

- `OperationBehaviorAttribute` :

  - `TransactionScopeRequired` プロパティは、操作のアクションをトランザクション スコープ内で実行する必要があるかどうかを指定します。 このプロパティは、このサンプルのすべての操作で `true` に設定されています。クライアントはそのトランザクションをすべての操作にフローするため、アクションはクライアント トランザクションのスコープ内で発生します。

  - `TransactionAutoComplete` プロパティは、未処理の例外が発生しなかった場合にメソッドが実行中のトランザクションが自動的に完了するかどうかを指定します。 前述のように、このプロパティは加算操作および減算操作では `true` に設定されていますが、乗算操作および除算操作では `false` に設定されています。 加算操作と減算操作は、これらのアクションを自動的に完了し、除算操作は、`SetTransactionComplete` メソッドを明示的に呼び出すことによってアクションを完了します。乗算操作はアクションを完了せず、アクションを完了するために除算などを後で呼び出す必要があり、この呼び出しに依存しています。

属性サービスの実装は、次のとおりです。

```csharp
[ServiceBehavior(
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,
    TransactionTimeout = "00:00:30",
    ReleaseServiceInstanceOnTransactionComplete = false,
    TransactionAutoCompleteOnSessionClose = false)]
public class CalculatorService : ICalculator
{
    double runningTotal;

    public CalculatorService()
    {
        Console.WriteLine("Creating new service instance...");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Add(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));
        runningTotal = runningTotal + n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Subtract(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));
        runningTotal = runningTotal - n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Multiply(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));
        runningTotal = runningTotal * n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Divide(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));
        runningTotal = runningTotal / n;
        OperationContext.Current.SetTransactionComplete();
        return runningTotal;
    }

    // Logging method ommitted for brevity
}
```

このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。

```console
Starting transaction
Performing calculations...
  Adding 100, running total=100
  Subtracting 45, running total=55
  Multiplying by 9, running total=495
  Dividing by 15, running total=33
  Completing transaction
Transaction committed
Press <ENTER> to terminate client.
```

サービス操作要求のログ記録は、サービスのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

サービスは計算の現在高を保持することに加え、インスタンス (このサンプルでは 1 つのインスタンス) の作成を報告し、データベースのログに操作要求を記録します。 すべての要求はクライアント トランザクションをフローするため、トランザクションの完了に失敗した場合、すべてのデータベース操作がロールバックされます。 これについては、次のようないくつかの方法で示すことができます。

- クライアントの `tx.Complete`() への呼び出しをコメント化して再実行します。これによってクライアントは、トランザクションを完了せずにトランザクション スコープを終了します。

- 除算サービス操作への呼び出しをコメント化します。これによって、乗算操作により初期化されたアクションの完了が回避され、したがって、クライアントのトランザクションの完了も最終的に失敗します。

- 未処理の例外を、クライアントのトランザクション スコープ内の任意の場所にスローします。これによってクライアントのトランザクションの完了が同様に回避されます。

これらの結果、スコープ内で実行される操作はコミットされず、データベースに保持されている行数はインクリメントしません。

> [!NOTE]
> ビルド プロセスの一貫として、データベース ファイルが bin フォルダにコピーされます。 このデータベース ファイルのコピーを調べ、Visual Studio プロジェクトに格納されているファイルではなく、ログに保存されている行を監視する必要があります。

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. SQL Server 2005 Express Edition または SQL Server 2005 がインストールされていることを確認してください。 サービスの App.config ファイルでは、データベース接続文字列が `connectionString` に指定されているか、または `usingSql` に設定された appSettings `false` 値によりデータベースとの対話が無効になっています。

2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。

3. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。

マシン間で、サンプルを実行する場合は、Microsoft 分散トランザクション コーディネーター (MSDTC) ネットワーク トランザクション フローを有効にし、WsatConfig.exe ツールを使用して、Windows Communication Foundation (WCF) のトランザクションのネットワークを有効にするを構成する必要があります。サポート。

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>分散トランザクション コーディネータ (MSDTC) を構成してサンプルを別のコンピュータで実行できるようにするには

1. サービス コンピューターで、受信ネットワーク トランザクションを許可するように MSDTC を構成します。

    1. **開始** メニューに移動します**コントロール パネル**、し**管理ツール**、し**コンポーネント サービス**します。

    2. 右クリック**マイ コンピューター**選択**プロパティ**します。

    3. **MSDTC** ] タブで [**セキュリティ構成**します。

    4. 確認**ネットワーク DTC アクセス**と**を許可する受信**します。

    5. をクリックして**はい**MS DTC サービスを再起動し **[ok]**。

    6. **[OK]** をクリックしてダイアログ ボックスを閉じます。

2. サービス コンピューターおよびクライアント コンピューターで、Windows ファイアウォールを構成します。例外アプリケーションのリストに、Microsoft 分散トランザクション コーディネーター (MSDTC) を追加します。

    1. Windows ファイアウォール アプリケーションをコントロール パネルから実行します。

    2. **例外**] タブで [**プログラムの追加**します。

    3. C:\WINDOWS\System32 フォルダーに移動します。

    4. Msdtc.exe を選択し、クリックして**オープン**します。

    5. をクリックして**ok**を閉じる、**プログラムの追加** ダイアログ ボックスをクリックします**OK** Windows ファイアウォール アプレットを閉じます。

3. クライアント コンピューターで、送信ネットワーク トランザクションを許可するよう MSDTC を構成します。

    1. **開始** メニューに移動します**コントロール パネル**、し**管理ツール**、し**コンポーネント サービス**します。

    2. 右クリック**マイ コンピューター**選択**プロパティ**します。

    3. **MSDTC** ] タブで [**セキュリティ構成**します。

    4. 確認**ネットワーク DTC アクセス**と**送信を許可する**します。

    5. をクリックして**はい**MS DTC サービスを再起動し **[ok]**。

    6. **[OK]** をクリックしてダイアログ ボックスを閉じます。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`

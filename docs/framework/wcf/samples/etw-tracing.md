---
title: ETW トレース
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: b445606677fba23ec81e896cce564330cedd6a19
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300685"
---
# <a name="etw-tracing"></a>ETW トレース
このサンプルでは、Event Tracing for Windows (ETW) と、このサンプルに用意されている `ETWTraceListener` を使用して、エンドツーエンド (E2E) のトレースを実装する方法を示します。 サンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) ETW トレースが含まれています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルに精通していることを前提としています。[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)します。  
  
 <xref:System.Diagnostics> トレース モデル内の各トレース ソースでは、データのトレース場所とトレース方法を決定するトレース リスナーを複数設定できます。 リスナの種類では、トレース データの記録形式が定義されます。 リスナを構成に追加する方法を、次のコード サンプルに示します。  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"   
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 このリスナを使用する前に、ETW トレース セッションを開始する必要があります。 このセッションは、Logman.exe または Tracelog.exe を使用して開始できます。 このサンプルには、ETW トレース セッションをセットアップするための SetupETW.bat ファイルと、セッションを閉じてログ ファイルを完了するための CleanupETW.bat ファイルが含まれています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。 これらのツールの詳細については、次を参照してください。 [https://go.microsoft.com/fwlink/?LinkId=56580](https://go.microsoft.com/fwlink/?LinkId=56580)  
  
 ETWTraceListener を使用する場合、トレースはバイナリの .etl ファイルにログ記録されます。 ServiceModel トレースが有効な場合、生成されるすべてのトレースは同じファイルに表示されます。 使用[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .etl および .svclog ログ ファイルを表示するためです。 このビューアでは、メッセージを送信側から受信側や使用地点までトレースできる、システムのエンドツーエンドのビューが作成されます。  
  
 ETW トレース リスナは、循環ログをサポートします。 この機能を有効にするには**開始**、**実行**と種類`cmd`コマンド コンソールを起動します。 次のコマンドでは、`<logfilename>` パラメータを使用するログ ファイル名に置き換えます。  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` スイッチと `-max` スイッチは省略できます。 これらのスイッチでは、それぞれバイナリの循環形式と 1000 MB の最大ログ サイズが指定されます。 `-p` スイッチは、トレース プロバイダーを指定する際に使用します。 この例では、`"{411a0819-c24b-428c-83e2-26b41091702e}"` は "XML ETW サンプル プロバイダー" の GUID です。  
  
 セッションを開始するには、次のコマンドを入力します。  
  
```  
Logman start Wcf  
```  
  
 ログ記録を完了したら、次のコマンドを使用してセッションを停止できます。  
  
```  
Logman stop Wcf  
```  
  
 このプロセスの任意のツールで処理できるバイナリの循環ログの生成を含む[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)または Tracerpt します。  
  
 確認することも、[循環トレース](../../../../docs/framework/wcf/samples/circular-tracing.md)循環ログ記録を実行する代替リスナの詳細についてはサンプルです。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行済みであるかどうかを必ず、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションをビルドする手順については、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
    > [!NOTE]
    >  RegisterProvider.bat、SetupETW.bat、および CleanupETW.bat コマンドを使用するには、ローカル管理者アカウントで実行する必要があります。 [!INCLUDE[wv](../../../../includes/wv-md.md)] 以降を使用している場合は、コマンド プロンプトも管理者権限で実行する必要があります。 これを行うには、コマンド プロンプトのアイコンを右クリックし、をクリックして**管理者として実行**します。  
  
3. サンプルを実行する前に、クライアントとサーバーで RegisterProvider.bat を実行します。 この結果、トレースを生成する ETWTracingSampleLog.etl ファイルがセットアップされます。このトレースはサービス トレース ビューアで読み取ることができます。 このファイルは、C:\logs フォルダにあります。 このフォルダーが存在しない場合はフォルダーを作成する必要があります。作成しない場合、トレースは生成されません。 次に、クライアント コンピューターとサーバー コンピューターで SetupETW.bat を実行し、ETW トレース セッションを開始します。 SetupETW.bat ファイルは、CS\Client フォルダーの下にあります。  
  
4. 1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
5. サンプルの使用が終わったら、CleanupETW.bat を実行して ETWTracingSampleLog.etl ファイルの作成を完了します。  
  
6. サービス トレース ビューア内で ETWTracingSampleLog.etl ファイルを開きます。 このバイナリ形式のファイルを .svclog ファイルとして保存するかどうかを尋ねるメッセージが表示されます。  
  
7. 新しく作成された .svclog ファイルをサービス トレース ビューアー内で開き、ETW トレースと ServiceModel トレースを表示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)

---
title: ETW トレース
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183699"
---
# <a name="etw-tracing"></a>ETW トレース
このサンプルでは、Event Tracing for Windows (ETW) と、このサンプルに用意されている `ETWTraceListener` を使用して、エンドツーエンド (E2E) のトレースを実装する方法を示します。 サンプルは[、作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいており、ETW トレースが含まれています。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)に精通していることを前提としています。  
  
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
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。 これらのツールの詳細については、<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 ETWTraceListener を使用する場合、トレースはバイナリの .etl ファイルにログ記録されます。 ServiceModel トレースが有効な場合、生成されるすべてのトレースは同じファイルに表示されます。 [サービス トレース ビューアー ツール (SvcTraceViewer.exe) を](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)使用して、.etl および .svclog ログ ファイルを表示します。 このビューアでは、メッセージを送信側から受信側や使用地点までトレースできる、システムのエンドツーエンドのビューが作成されます。  
  
 ETW トレース リスナは、循環ログをサポートします。 この機能を有効にするには、[**スタート**] メニューの [**ファイル名を指定して実行**] をクリックし、コマンド コンソールを起動`cmd`します。 次のコマンドでは、`<logfilename>` パラメータを使用するログ ファイル名に置き換えます。  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` スイッチと `-max` スイッチは省略できます。 これらのスイッチでは、それぞれバイナリの循環形式と 1000 MB の最大ログ サイズが指定されます。 `-p` スイッチは、トレース プロバイダーを指定する際に使用します。 この例では、`"{411a0819-c24b-428c-83e2-26b41091702e}"` は "XML ETW サンプル プロバイダー" の GUID です。  
  
 セッションを開始するには、次のコマンドを入力します。  
  
```console  
logman start Wcf  
```  
  
 ログ記録を完了したら、次のコマンドを使用してセッションを停止できます。  
  
```console  
logman stop Wcf  
```  
  
 このプロセスは、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)または Tracerpt を含む、選択したツールで処理できるバイナリ循環ログを生成します。  
  
 循環ログを実行する代替リスナーの詳細については、[循環トレース](../../../../docs/framework/wcf/samples/circular-tracing.md)のサンプルを確認することもできます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーション ファウンデーション サンプルの 1 回限りのセットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行していることを確認します。  
  
2. ソリューションをビルドするには、「 [Windows コミュニケーション ファウンデーション のサンプルの構築](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
    > [!NOTE]
    > RegisterProvider.bat、SetupETW.bat、および CleanupETW.bat コマンドを使用するには、ローカル管理者アカウントで実行する必要があります。 Windows Vista 以降を使用している場合は、管理者特権を使用してコマンド プロンプトも実行する必要があります。 これを行うには、コマンド プロンプト アイコンを右クリックし、[**管理者として実行**] をクリックします。  
  
3. サンプルを実行する前に、クライアントとサーバーで RegisterProvider.bat を実行します。 この結果、トレースを生成する ETWTracingSampleLog.etl ファイルがセットアップされます。このトレースはサービス トレース ビューアで読み取ることができます。 このファイルは、C:\logs フォルダにあります。 このフォルダーが存在しない場合はフォルダーを作成する必要があります。作成しない場合、トレースは生成されません。 次に、クライアント コンピューターとサーバー コンピューターで SetupETW.bat を実行し、ETW トレース セッションを開始します。 SetupETW.bat ファイルは、CS\Client フォルダーの下にあります。  
  
4. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには、「 [Windows コミュニケーション ファウンデーション サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
5. サンプルの使用が終わったら、CleanupETW.bat を実行して ETWTracingSampleLog.etl ファイルの作成を完了します。  
  
6. サービス トレース ビューア内で ETWTracingSampleLog.etl ファイルを開きます。 このバイナリ形式のファイルを .svclog ファイルとして保存するかどうかを尋ねるメッセージが表示されます。  
  
7. 新しく作成された .svclog ファイルをサービス トレース ビューアー内で開き、ETW トレースと ServiceModel トレースを表示します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

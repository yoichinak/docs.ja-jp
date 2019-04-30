---
title: 循環トレース
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: cd1a0c85dd42a7f064e75c7efdacb9ea46ef445d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002409"
---
# <a name="circular-tracing"></a>循環トレース
このサンプルでは、循環バッファ トレース リスナの実装を示します。 製品版サービスの一般的なシナリオは、長期間使用できるサービスを持つことと、トレース ログを低レベルで有効にすることです。 こうしたサービスは、大量のディスク領域を消費します。 サービスのトラブルシューティングを行う場合、問題の解決に関連するのはトレース ログの最新データです。 このサンプルで示す循環バッファ トレース リスナの実装では、設定可能なデータ量を上限とする最新のトレースのみがディスク上に保持されます。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)カスタム トレース リスナーが含まれています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルに精通していることを前提としています、[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)サンプルし、指定されたドキュメントを読んでいる、[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)サンプル。  
  
## <a name="circular-buffer-trace-listener"></a>循環バッファ トレース リスナ  
 循環バッファ トレース リスナの実装の概念とは、2 つのファイルを使って、必要なトレース ログ データの全体量の半分を上限としたデータをそれぞれに保存することです。 リスナは 1 つのファイルを作成して、データ サイズの半分という限界に到達するまでデータを書き込みます。この限界に到達した時点で、2 番目のファイルに切り替わります。 2 番目のファイルの限界に到達したら、リスナは最初のファイルを新しいトレースで上書きします。  
  
 このリスナーがから派生した、 `XmlWriteTraceListener` 、ログを表示することができ、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)します。 ログの表示を試みる際に、サービス トレース ビューア ツールで 2 つのログ ファイルを両方同時に開くと、これらのファイルを簡単に再結合することができます。 サービス トレース ビューア ツールは、トレースが正しい順序で表示されるように自動的にトレースの並べ替えを管理します。  
  
## <a name="configuration"></a>構成  
 サービスは、リスナとソースの要素に対して次のコードを追加することによって、循環バッファ トレース リスナを使用するように構成できます。 ファイルの最大サイズは、循環トレース リスナの構成の `maxFileSizeKB` 属性を設定することによって指定します。 このコードを次に示します。  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行済みであるかどうかを必ず、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)

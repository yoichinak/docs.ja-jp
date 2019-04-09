---
title: トレースとメッセージ ログ
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: ba4428bad6662928ddc1830c8998dd5f5b6b9bbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186577"
---
# <a name="tracing-and-message-logging"></a>トレースとメッセージ ログ
このサンプルでは、トレースとメッセージ ログを有効にする方法を示します。 結果のトレースとメッセージ ログを使用して表示、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)します。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="tracing"></a>トレース  
 Windows Communication Foundation (WCF) で定義されているトレース機構を使用して、<xref:System.Diagnostics>名前空間。 このトレース モデルのトレース データは、アプリケーションが実装するトレース ソースによって作成されます。 各ソースは、名前によって識別されます。 トレース コンシューマでは、情報を取得するトレース ソースのトレース リスナが作成されます。 トレース データを受け取るには、トレース ソースのリスナを作成する必要があります。 WCF では、これを行うサービス モデルのトレース ソースを設定して、サービスまたはクライアントの構成ファイルに次のコードを追加`switchValue`:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 トレース ソースの詳細については、トレース ソース」セクションを参照してください、[トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)トピック。  
  
## <a name="activity-tracing-and-propagation"></a>アクティビティのトレースと伝達  
 ある`ActivityTracing`有効になっていると`propagateActivity`に設定`true`で、`system.ServiceModel`クライアントとサービスの両方のトレース ソースは、エンドポイント (内のアクティビティ間 (アクティビティ) の処理の論理単位内でのトレースの相関関係を提供アクティビティ転送の場合) と (アクティビティ ID の伝達) を通じて複数のエンドポイントにわたるアクティビティ間。  
  
 3 つの機構 (アクティビティ、転送、および伝達) により、サービス トレース ビューア ツールを使用してエラーの根本原因をより迅速に見つけることができます。 詳細については、次を参照してください。[相関トレースの表示とトラブルシューティングのサービス トレース ビューアーを使用して](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)します。  
  
 ユーザー定義のアクティビティ トレースを作成することにより、サービス モデルによって提供されるトレースを拡張することができます。 ユーザー定義のアクティビティ トレースによって、次の操作を可能にするトレース アクティビティを作成できます。  
  
-   複数のトレースを作業の論理単位ごとにグループ化します。  
  
-   転送や伝達を利用してアクティビティを相互に関連付けます。  
  
-   (たとえば、ログ ファイルのディスク領域のコスト) WCF トレースのパフォーマンス コストを軽減します。  
  
 ユーザー定義のアクティビティ トレースの詳細についてを参照してください、[トレース拡張](../../../../docs/framework/wcf/samples/extending-tracing.md)サンプル。  
  
## <a name="message-logging"></a>メッセージ ログ  
 クライアントと WCF アプリケーションのサービスの両方で、メッセージ ログを有効にすることができます。 メッセージ ログを有効にするには、クライアントとサービスのどちらかに次のコードを追加する必要があります。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 メッセージが記録されるときのトレースの種類は、そのメッセージがクライアントでトレースされるか、またはサーバーでトレースされるかによって異なります。 たとえば、クライアントに送信される "Add" メッセージは、クライアントでは "TransportWrite" カテゴリの下でトレースされるのに対し、サービスでは同じメッセージが "TransportRead" カテゴリの下でトレースされます。  
  
 クライアントの App.config ファイルまたはサービスの Web.config ファイルの <xref:System.Diagnostics> セクションに次のコードを追加して、トレース リスナを構成します。  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 メッセージは、構成ファイルで指定された対象ディレクトリ内に XML 形式で記録されます。  
  
> [!NOTE]
>  最初にログ ディレクトリが作成されていないと、トレース ファイルは作成されません。 ディレクトリ C:\logs\ が存在することを確認するか、またはリスナの構成でログ記録用の代替ディレクトリを指定します。 詳細については、このドキュメントの最後にある初期セットアップ手順を参照してください。  
  
 メッセージ ログの詳細については、次を参照してください。、[メッセージ ログの構成](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)トピック。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  トレースとメッセージ ログのサンプルを実行する前に、サービスによって .svclog ファイルが書き込まれるディレクトリ C:\logs\ を作成します。 このディレクトリ名は、トレースとメッセージがログ記録されるパスとして、構成ファイル内で定義されます。この名前は変更可能です。 ユーザー Network Service に、そのログ ディレクトリへの書き込みアクセスを与えます。  
  
3.  ソリューションの c#、C++、または Visual Basic .NET 版をビルドする手順については、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
4.  1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)

---
title: Windows サービス ホスト
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 85d089813a455784fde679e9200a9b29b956af8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006405"
---
# <a name="windows-service-host"></a>Windows サービス ホスト
このサンプルでは、マネージ Windows サービスでホストされる Windows Communication Foundation (WCF) サービスを使用します。 Windows サービスのサービス アプレットを使用して、制御 **コントロール パネルの** システムの再起動後に自動的に起動するように構成できます。 このサンプルは、クライアント プログラムと Windows サービス プログラムで構成されています。 サービスは .exe プログラムとして実装され、独自のホスティング コードが指定されます。 Windows プロセス アクティブ化サービス (WAS) やインターネット インフォメーション サービス (IIS) などの他のホスト環境では、ホスティング コードを記述する必要はありません。

> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 このサービスをビルドしたら、他の Windows サービスと同様、Installutil.exe ユーティリティを使用してインストールする必要があります。 サービスを変更する場合は、`installutil /u` を使用して、まずそのサービスをアンインストールする必要があります。 このサンプルに含まれている Setup.bat ファイルは Windows Service をインストールして起動するコマンド ファイルです。同様にこのサンプルに含まれている Cleanup.bat ファイルは、Windows サービスをシャットダウンしてアンインストールするコマンド ファイルです。 WCF サービスは、Windows サービスが実行されている場合にのみクライアントに応答できます。 サービス アプレットを使用して Windows サービスを停止するかどうかは**コントロール パネルの **クライアントを実行し、<xref:System.ServiceModel.EndpointNotFoundException>例外は、クライアントがサービスにアクセスしようとしたときに発生します。 Windows サービスを再起動してクライアントを再実行した場合は、通信が正常に行われます。  
  
 サービス コードには、インストーラー クラス、WCF サービス実装クラス、ICalculator コントラクトを実装して、ランタイム ホストとして機能する Windows サービス クラスが含まれています。 インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを NT サービスとしてインストールできます。 サービス実装クラスで、`WcfCalculatorService`は基本的なサービス コントラクトを実装する WCF サービスです。 この WCF サービスと呼ばれる Windows サービス クラス内でホストされる`WindowsCalculatorService`します。 Windows サービスとして限定するため、このクラスは <xref:System.ServiceProcess.ServiceBase> を継承し、<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドを実装しています。 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> では、<xref:System.ServiceModel.ServiceHost> 型の `WcfCalculatorService` オブジェクトが作成され、開かれます。 <xref:System.ServiceProcess.ServiceBase.OnStop> では、<xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> オブジェクトの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されて ServiceHost が閉じられます。 使用して、ホストのベース アドレスを構成、 [\<追加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)子である要素の[ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)の子である、 [ \<ホスト >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)子である要素の[\<サービス >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)要素。  
  
 定義されているエンドポイントのベース アドレスを使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)します。 ベース アドレスの構成と CalculatorService を公開するエンドポイントのサンプルを次に示します。  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. ソリューションがビルドされたら、Installutil.exe ツールを使用して Windows サービスをインストールする管理者特権での Visual Studio 2012 コマンド プロンプトから Setup.bat を実行します。 このサービスは、[サービス] に表示されます。  
  
4. 1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
## <a name="see-also"></a>関連項目

- [AppFabric のホストおよび永続化のサンプル](https://go.microsoft.com/fwlink/?LinkId=193961)

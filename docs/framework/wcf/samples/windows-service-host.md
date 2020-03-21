---
title: Windows サービス ホスト
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143526"
---
# <a name="windows-service-host"></a>Windows サービス ホスト
このサンプルでは、マネージ Windows サービスでホストされている Windows 通信基盤 (WCF) サービスを示します。 Windows サービスは **、コントロール パネル**の [サービス] アプレットを使用して制御され、システムの再起動後に自動的に起動するように構成できます。 このサンプルは、クライアント プログラムと Windows サービス プログラムで構成されています。 サービスは .exe プログラムとして実装され、独自のホスティング コードが指定されます。 Windows プロセス アクティブ化サービス (WAS) やインターネット インフォメーション サービス (IIS) などの他のホスト環境では、ホスティング コードを記述する必要はありません。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 このサービスをビルドしたら、他の Windows サービスと同様、Installutil.exe ユーティリティを使用してインストールする必要があります。 サービスを変更する場合は、`installutil /u` を使用して、まずそのサービスをアンインストールする必要があります。 このサンプルに含まれている Setup.bat ファイルは Windows Service をインストールして起動するコマンド ファイルです。同様にこのサンプルに含まれている Cleanup.bat ファイルは、Windows サービスをシャットダウンしてアンインストールするコマンド ファイルです。 WCF サービスは、Windows サービスが実行されている場合にのみクライアントに応答できます。 **コントロール パネル**の [サービス] アプレットを使用して Windows サービスを停止<xref:System.ServiceModel.EndpointNotFoundException>し、クライアントを実行すると、クライアントがサービスにアクセスしようとすると例外が発生します。 Windows サービスを再起動してクライアントを再実行した場合は、通信が正常に行われます。  
  
 サービス コードには、インストーラー クラス、ICalculator コントラクトを実装する WCF サービス実装クラス、およびランタイム ホストとして機能する Windows サービス クラスが含まれています。 インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを NT サービスとしてインストールできます。 サービス実装クラス は`WcfCalculatorService`、基本的なサービス コントラクトを実装する WCF サービスです。 この WCF サービスは、 という Windows`WindowsCalculatorService`サービス クラス内でホストされます。 Windows サービスとして限定するため、このクラスは <xref:System.ServiceProcess.ServiceBase> を継承し、<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドを実装しています。 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> では、<xref:System.ServiceModel.ServiceHost> 型の `WcfCalculatorService` オブジェクトが作成され、開かれます。 <xref:System.ServiceProcess.ServiceBase.OnStop> では、<xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> オブジェクトの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されて ServiceHost が閉じられます。 ホストのベース アドレスは、[\<ホスト](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)>要素の子である[\<ホスト>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)要素の[\<](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)子である baseAddresses>の子である add>[\<要素を使用](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)して構成されます。  
  
 定義されたエンドポイントは、ベース アドレスと[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用します。 ベース アドレスの構成と CalculatorService を公開するエンドポイントのサンプルを次に示します。  
  
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
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. ソリューションがビルドされたら、管理者特権での Visual Studio 2012 コマンド プロンプトから Setup.bat を実行して、Installutil.exe ツールを使用して Windows サービスをインストールします。 このサービスは、[サービス] に表示されます。  
  
4. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには、「 [Windows コミュニケーション ファウンデーション サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## <a name="see-also"></a>関連項目

- [AppFabric のホストおよび永続化のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))

---
title: '方法: マネージド Windows サービスで WCF サービスをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: c63b249cf16100f0b18d622fdecd7cd375df83d8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297760"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>方法: マネージド Windows サービスで WCF サービスをホストする

このトピックでは、Windows サービスによってホストされている Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順について説明します。 シナリオは、ホスト オプションがアクティブ化メッセージをセキュリティで保護された環境でインターネット インフォメーション サービス (IIS) の外部でホストされている実行時間の長い WCF サービスでは、マネージ Windows サービスで有効です。 サービスの有効期限は代わりにオペレーティング システムによって制御されます。 このホスト オプションは Windows のすべてのバージョンで使用できます。

Windows サービスは、Microsoft 管理コンソール (MMC) の Microsoft.ManagementConsole.SnapIn を使用して管理し、システムのブート時に自動的に起動するように構成できます。 このホスト オプションは、サービスのプロセス有効期間は Windows サービスのサービス コントロール マネージャー (SCM) によって、制御できるようにマネージ Windows サービスとして WCF サービスをホストするアプリケーション ドメイン (AppDomain) の登録で構成されます。

サービス コードには、サービス コントラクトのサービス実装、Windows サービス クラス、およびインストーラー クラスが含まれています。 サービス実装クラスで、`CalculatorService`は、WCF サービスです。 一方、`CalculatorWindowsService` は Windows サービスです。 Windows サービスとして限定するため、このクラスは `ServiceBase` を継承し、`OnStart` メソッドと `OnStop` メソッドを実装しています。 `OnStart` では、<xref:System.ServiceModel.ServiceHost> 型の `CalculatorService` が作成され、開かれます。 `OnStop` では、このサービスが停止され、破棄されます。 ホストはベース アドレスをサービス ホストに提供する必要もあります。サービス ホストは、アプリケーション設定で構成されます。 インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを Windows サービスとしてインストールできます。

## <a name="construct-the-service-and-provide-the-hosting-code"></a> サービスを構築してホスティング コードを提供する

1. 作成する新しい Visual Studio**コンソール アプリ**という名前のプロジェクト**サービス**します。

2. Program.cs を Service.cs に変更します。

3. 名前空間を変更`Microsoft.ServiceModel.Samples`します。

4. 次のアセンブリへの参照を追加します。

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5. 次の using ステートメントを Service.cs に追加します。

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. 次のコードに示すように、`ICalculator` サービス コントラクトを定義します。

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. 次のコードに示すように、`CalculatorService` というクラスにサービス コントラクトを実装します。

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. `CalculatorWindowsService` クラスから継承する <xref:System.ServiceProcess.ServiceBase> という新しいクラスを作成します。 `serviceHost` というローカル変数を追加して、<xref:System.ServiceModel.ServiceHost> インスタンスを参照します。 定義、`Main`メソッドを呼び出す `ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. 次のコードに示すように、新しい <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> インスタンスを作成して開くことによって <xref:System.ServiceModel.ServiceHost> メソッドをオーバーライドします。

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. 次のコードに示すように、<xref:System.ServiceProcess.ServiceBase.OnStop%2A> を閉じて <xref:System.ServiceModel.ServiceHost> メソッドをオーバーライドします。

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. `ProjectInstaller` から継承し、<xref:System.Configuration.Install.Installer> に設定された <xref:System.ComponentModel.RunInstallerAttribute> でマークされた `true` という新しいクラスを作成します。 これで、Installutil.exe ツールで Windows サービスをインストールできるようになります。

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. プロジェクトを作成したときに生成された `Service` クラスを削除します。

13. アプリケーション構成ファイルをプロジェクトに追加します。 ファイルの内容を次の構成 XML に置き換えます。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     App.config ファイルを右クリックして、**ソリューション エクスプ ローラー**選択**プロパティ**します。 **出力ディレクトリにコピー**選択**新しい場合はコピー**します。

     この例では、構成ファイルにエンドポイントを明示的に指定します。 エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。 この例では、サービスには <xref:System.ServiceModel.Description.ServiceMetadataBehavior> に設定された `true` があるので、サービスで公開メタデータも有効化されています。 既定のエンドポイントについては、「[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。

## <a name="install-and-run-the-service"></a>サービスをインストールして実行する

1. ソリューションをビルドして `Service.exe` 実行可能ファイルを作成します。

2. For Visual Studio 開発者コマンド プロンプトを開き、プロジェクト ディレクトリに移動します。 コマンド プロンプトで「`installutil bin\service.exe`」と入力して、Windows サービスをインストールします 

     コマンド プロンプトで「`services.msc`」と入力してサービス コントロール マネージャー (SCM) にアクセスします。 Windows サービスは、[Services] に "WCFWindowsServiceSample" として表示されます。 WCF サービスは、Windows サービスが実行されている場合にのみクライアントに応答できます。 サービスを開始する、SCM"Start"、または選択の種類で右**net start WCFWindowsServiceSample**コマンド プロンプトでします。

3. サービスを変更する場合は、まずそのサービスを停止してからアンインストールする必要があります。 サービスを停止し、SCM でそのサービスを右クリックし、"Stop"を選択または**型 net stop WCFWindowsServiceSample**コマンド プロンプトでします。 Windows サービスを停止してクライアントを実行すると、クライアントがこのサービスにアクセスしようとしたときに <xref:System.ServiceModel.EndpointNotFoundException> 例外が発生することに注意してください。 Windows サービスの種類をアンインストールする**installutil/u bin\service.exe**コマンド プロンプトでします。

## <a name="example"></a>例

このトピックで使用されるコードの完全な一覧を次に示します。

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

"自己ホスト" オプションと同様、Windows サービス ホスト環境では、ホスト コードをアプリケーションの一部として記述する必要があります。 サービスはコンソール アプリケーションとして実装され、独自のホスティング コードが指定されます。 インターネット インフォメーション サービス (IIS) でホストされる Windows プロセス アクティブ化サービス (WAS) など、他のホスト環境ではホスティング コードを記述する必要はありません。

## <a name="see-also"></a>関連項目

- [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)
- [マネージド アプリケーションのホスト](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
- [AppFabric のホスティング機能](https://go.microsoft.com/fwlink/?LinkId=201276)
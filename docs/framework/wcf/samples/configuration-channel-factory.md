---
title: 構成チャネル ファクトリ
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 5bee4c7cc2c2e64c6e0d8d0ec2634f9500cd9d51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975872"
---
# <a name="configuration-channel-factory"></a>構成チャネル ファクトリ
このサンプルでは、<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> の使用方法を示します。 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF クライアントの構成サーバーの全体を管理できます。 これは、アプリケーション ドメインによる読み込みの後に構成が選択または変更される場合にも役立ちます。

## <a name="demonstrates"></a>使用例
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>説明
 このサンプルでは、既定のアプリケーション構成ファイルを使用することなく、<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> を使用して、クライアント アプリケーションに特定の構成ファイルを追加する方法を示します。

 このサンプルは、2 つのプロジェクトで構成されます。 最初のプロジェクトは、クライアントから送信されるメッセージに応答するために実行される単純なサービスです。 2 番目のプロジェクトは、Test.config 構成ファイルの <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> を使用して、2 つの <xref:System.Configuration.ExeConfigurationFileMap> オブジェクトを作成し、サービスとの通信にそれらのオブジェクトを使用するクライアント アプリケーションです。 どちらのクライアントも Test.config で指定された構成を使用してサービスと通信します。

 次のコードでは、カスタム構成ファイルをクライアント アプリケーションに追加します。

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. 管理者特権で Visual Studio 2012 を開きます。

2. ConfigurationChannelFactory ソリューション (2 プロジェクト) を右クリックし、**プロパティ**します。

3. **共通プロパティ**を選択します**スタートアップ プロジェクト**、 をクリックし、**マルチ スタートアップ プロジェクト**します。

4. 移動、**サービス**でプロジェクトは、リストの先頭を**アクション 'Start'**、し、移動、**クライアント**プロジェクトの後に、**サービス**プロジェクトでも、**アクション 'Start'** であり、**クライアント**プロジェクトを実行した後、**サービス**プロジェクト。

5. をクリックして**OK**、し、f5 キーを押して (または ctrl キーを押しながら f5 キー)、サンプルを実行するキーを押します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`

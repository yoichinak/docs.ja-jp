---
title: WCF サービスの簡略化された構成
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183350"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF サービスの簡略化された構成
このサンプルでは、実装し、Windows 通信基盤 (WCF) を使用して、一般的なサービスとクライアントを構成する方法を示します。 このサンプルは、他のすべての基本的な技術サンプルの基礎になります。  
  
 このサービスは、サービスと通信するためのエンドポイントを公開しますが、.NET Framework 4 の簡略化された構成を使用します。 .NET Framework 4 より前のエンドポイントは、通常、次の構成コードの例に示すように、構成ファイル (Web.config) で定義されています。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 .NET Framework 4`<service>`では、要素は省略可能です。 サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。 このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。 次のコード例は、簡略化された構成ファイルを示しています。 構成されているとおり、同じコンピューター上の`http://localhost/servicemodelsamples/service.svc`クライアントが サービスにアクセスできます。 リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。 既定では、サービスはメタデータを公開しません。 そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションをビルドするには、「 [Windows コミュニケーション ファウンデーション のサンプルの構築](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 次の手順に従ってサンプルを実行します。  
  
    1. **サービス**プロジェクトを右クリックし、[**スタートアップ プロジェクトとして設定]** を選択し **、Ctrl キーを押しながら F5 キー**を押します。  
  
    2. コンソール出力でサービスが動作していることが確認されるまで待機します。  
  
    3. **クライアント**プロジェクトを右クリックし、[**スタートアップ プロジェクトとして設定]** を選択し **、Ctrl キーを押しながら F5 キー**を押します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の管理のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)

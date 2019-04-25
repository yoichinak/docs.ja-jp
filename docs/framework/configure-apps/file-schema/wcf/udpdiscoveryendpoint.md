---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 180763404ee9070e9ed6e5476d4568a0a018dcb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203367"
---
# <a name="udpdiscoveryendpoint"></a>\<udpDiscoveryEndpoint>
この構成要素は、UDP マルチキャスト バインディングを使用した探索操作用に事前に構成される標準エンドポイントを定義します。 このエンドポイントには固定コントラクトがあり、WS-Discovery プロトコルの 2 つのバージョンをサポートします。 また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。  
  
 \<system.ServiceModel >  
\<standardEndpoints>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|discoveryMode|探索プロトコルのモードを示す文字列。 有効な値は"Adhoc"と"Managed です"。 マネージド モードでは、プロトコルは Discoverable サービスのリポジトリとして機能する Discovery Proxy に依存します。 アドホック モードでは、プロトコルは UDP マルチキャスト メカニズムを使用して利用可能なサービスを探索する必要があります。 この値は、<xref:System.ServiceModel.Discovery.ServiceDiscoveryMode> 型です。|  
|discoveryVersion|WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。 有効値は WSDiscovery11 と WSDiscoveryApril2005 です。 この値は、<xref:System.ServiceModel.Discovery.DiscoveryVersion> 型です。|  
|maxResponseDelay|Discovery プロトコルが Probe Match や Resolve Match などのメッセージを送信するまでの待機時間の最大値を指定する Timespan 値。<br /><br /> すべての ProbeMatch が同時に送信されると、ネットワーク ストームが発生することがあります。 これを防ぐために、各 ProbeMatch はランダムな時間だけ待機して送信されます。 ランダムな待機時間は、0 からこの属性に設定された値の範囲内で設定されます。 この属性を 0 に設定すると、ProbeMatch メッセージは待機せずに短いループで送信されます。 それ以外の場合は、ProbeMatch メッセージはランダムな時間だけ待機して送信されます。すべての ProbeMatch メッセージの送信にかかる合計時間が maxResponseDelay を超えることはありません。 この値はサービスのみに関連するもので、クライアントが使用するものではありません。|  
|multicastAddress|探索メッセージの送受信に使用するマルチキャスト アドレスを指定する URI。 既定値は、プロトコル仕様に準じたマルチキャスト アドレスです。|  
|`name`|標準エンドポイントの構成名を指定する文字列。 この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<udpTransportSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|UDP エンドポイントの UDP トランスポートを構成できる設定のコレクション。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。|  
  
## <a name="example"></a>例  
 UDP マルチキャスト トランスポート経由で探索メッセージをリッスンするサービスの例を次に示します。  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

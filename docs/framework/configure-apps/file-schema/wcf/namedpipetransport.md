---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: fd7dc38e229b6135f91fc159596ed1669d43701a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772360"
---
# <a name="namedpipetransport"></a>\<namedPipeTransport>
チャネルがカスタム バインドに含まれているときに名前付きパイプを使用してメッセージを転送するトランスポートを定義します。  
  
\<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<namePipeTransport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpopint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|ChannelInitializationTimeout|取得または設定します、<xref:System.TimeSpan>チャネルができるの初期化ステータス切断されるまで最大時間を決定します。|  
|ConnectionBufferSize|クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズを取得または設定します。|  
|hostNameComparisonMode|URI で一致する場合にサービスに到達するためにホスト名を使用するかどうかを示す値を取得または設定します。|  
|manualAddressing|メッセージの手動アドレス指定が必要かどうかを示す値を取得または設定します。|  
|maxBufferPoolSize|取得またはトランスポートで使用するバッファー プールのバイト単位で最大のサイズを設定します。|  
|maxBufferSize|使用するバッファーの最大サイズを取得または設定します。 ストリーム メッセージの場合、この値は少なくともメッセージ ヘッダーで使用できる最大サイズにする必要があります。これは、バッファー モードで読み取られます。|  
|maxOutputDelay|メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間を取得または設定します。|  
|maxPendingAccepts|取得またはサービスは、サービスへの着信接続を処理するためのリスナーで待機できるチャネルの最大数を設定します。|  
|maxPendingConnections|サービスでディスパッチを待機している最大接続数を取得または設定します。|  
|maxReceivedMessageSize|取得し、受信できるをバイト単位で、メッセージの最大サイズを設定します。|  
|transferMode|接続指向のトランスポートでメッセージをバッファーするか、ストリーム配信するかを示す値を取得または設定します。|  
|[\<connectionPoolSettings > の\<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|名前付きパイプ バインディングの追加の接続プール設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>Remarks  
このトランスポートは、"net.pipe://hostname/path" の形式の URI を使用します。 他の URI コンポーネントは省略可能です。  
  
`namedPipeTransport` 要素は、名前付きパイプ トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。 このトランスポートは、コンピューター上での WCF (Windows Communication Foundation) 間の通信に使用されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)
- [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

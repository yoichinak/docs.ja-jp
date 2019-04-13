---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226873"
---
# <a name="websocketsettings"></a>\<webSocketSettings >
Web ソケット設定を指定するために使用される構成要素。  
  
\<system.ServiceModel >  
\<bindings>  
\<netHttpBinding>  
  
## <a name="syntax"></a>構文  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|createNotificationOnConnection|通知を接続時に送信するかどうかを指定します。|  
|disablePayloadMasking|Web ソケットのマスクが無効であるかどうかを指定します。|  
|keepAliveInterval|接続維持の間隔を指定します。|  
|maxPendingConnections|サービスでのディスパッチを待機している接続の最大数を指定します。|  
|receiveBufferSize|受信バッファーのサイズを指定します。|  
|sendBufferSize|送信バッファーのサイズを指定します。|  
|subProtocol|Web ソケットのサブプロトコルを指定します。|  
|transportUsage|Web ソケットを使用するタイミングを指定します。|  
  
## <a name="transportusage-attribute"></a>transportUsage 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|WhenDuplex|コントラクトが双方向の場合に、Web ソケット プロトコルを使用します。|  
|Always|コントラクトにかかわらず、常にWeb ソケット プロトコルを使用します。|  
|Never|Web ソケット プロトコルを使用しません。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|\<netHttpBinding>|NetHttpBinding を指定します。|  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、 \<webSocketSettings > 要素。  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)

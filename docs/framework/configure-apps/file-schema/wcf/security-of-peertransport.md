---
title: <security> の <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936639"
---
# <a name="security-of-peertransport"></a>\<peertransport > \<のセキュリティ >
ピア チャネルに関連付けられたセキュリティ設定を格納します。使用される認証の種類とメッセージ トランスポートで使用されるセキュリティを含みます。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<peerTransport >  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`mode`|適用するセキュリティの種類を指定します。 既定値は Message です。 この属性は <xref:System.ServiceModel.SecurityMode> 型です。|  
  
## <a name="mode-attribute"></a>mode 属性  
  
|値|説明|  
|-----------|-----------------|  
|`None`|セキュリティを無効にします。|  
|`Transport`|セキュリティは、HTTPS を使用して確保されます。|  
|`Message`|SOAP セキュリティにより、認証、整合性、および機密性が実現します。|  
|`TransportWithMessageCredential`|HTTPS により、認証および機密性が実現します。 SOAP メッセージには、豊富な資格情報の種類が用意されています。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|カスタム バインドのピア トランスポートを定義します。 この要素には、サービスと対話するときに使用される資格情報を指定する `clientCredentialType` 属性があります。 この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。<br /><br /> この要素は <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<peerTransport >](peertransport.md)|カスタム バインドのピア トランスポートを定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート セキュリティ](../../../wcf/feature-details/transport-security.md)
- [トランスポート](../../../wcf/feature-details/transports.md)
- [トランスポートの選択](../../../wcf/feature-details/choosing-a-transport.md)
- [バインディング](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

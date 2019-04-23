---
title: <security> の <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 1aff79bf5867a3a1ebe05e3f812475dac4b413e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116864"
---
# <a name="security-of-peertransport"></a>\<セキュリティ > の\<peerTransport >
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
  
|[値]|説明|  
|-----------|-----------------|  
|`None`|セキュリティを無効にします。|  
|`Transport`|セキュリティは、HTTPS を使用して確保されます。|  
|`Message`|SOAP セキュリティにより、認証、整合性、および機密性が実現します。|  
|`TransportWithMessageCredential`|HTTPS により、認証および機密性が実現します。 SOAP メッセージには、豊富な資格情報の種類が用意されています。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|カスタム バインドのピア トランスポートを定義します。 この要素には、サービスと対話するときに使用される資格情報を指定する `clientCredentialType` 属性があります。 この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。<br /><br /> この要素は <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<peerTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|カスタム バインドのピア トランスポートを定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート セキュリティ](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)
- [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

---
title: <transport> (行中)  <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 9b6f548515afbba5068659bd5c6f7f2b33f80cda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076004"
---
# <a name="transport-of-peertransport"></a>\<トランスポート > の\<peerTransport >
このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<peerTransport >  
\<セキュリティ >  
\<transport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|credentialType|任意。 ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。 この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。|  
  
## <a name="credentialtype-attribute"></a>credentialType 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|証明書|ピア チャネル トランスポートの認証には X 509 証明書が必要です。|  
|[Password]|ピア チャネル トランスポートの認証には正しいパスワードが必要です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|ピア トランスポートのセキュリティ設定を定義します。|  
  
## <a name="remarks"></a>Remarks  
 場合にのみこの要素は、設定の mode 属性[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)に設定されている`Transport`または`TransportWithMessageCredential`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート セキュリティ](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)
- [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

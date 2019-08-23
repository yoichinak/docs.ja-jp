---
title: <peer> の <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933784"
---
# <a name="peer-of-servicecredentials"></a>\<serviceCredentials > の\<ピア >
ピア ノードの現在の資格情報を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<ピア >  
  
## <a name="syntax"></a>構文  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|ピアツーピア サービスのメッセージの署名と暗号化に使用する X.509 証明書を指定します。 .|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|メッセージ送信者の認証オプションを指定します。|  
|[\<peerAuthentication>](peerauthentication.md)|ピア サービスの認証オプションを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [ピアツーピア ネットワーク](../../../wcf/feature-details/peer-to-peer-networking.md)
- [ピアチャネルメッセージの認証](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [ピアチャネルのカスタム認証](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [セキュリティによるピア チャネル アプリケーションの保護](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)

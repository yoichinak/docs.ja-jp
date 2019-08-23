---
title: <security> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936684"
---
# <a name="security-of-netmsmqbinding"></a>\<netmsmqbinding \<> のセキュリティ >
MSMQ バインディングのセキュリティ設定を定義します。 トランスポートまたは SOAP セキュリティが有効であるかどうか、および有効である場合は、どの認証モードと保護レベルを使用するかを指定します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<netMsmqBinding>  
\<binding>  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|モード|整合性、機密性、および認証を制御するセキュリティの種類を指定します。 有効な値は次のとおりです。<br /><br /> 存在これにより、セキュリティが無効になります。<br />トランスポート保護と認証はトランスポートによって提供されます。 これは、2 つのキュー マネージャー間のメッセージ セキュリティに適用されます。 アプリケーションとキュー マネージャーとの間にセキュリティは提供されません。 既存の Msmq アプリケーションは、この種類のセキュリティ モードと機能的に等価です。<br />メッセージエンドツーエンドアプリケーションのセキュリティを指定します。 トランスポート層で提供されるセキュリティありません。 これは、他の標準バインディングによって提供されたセキュリティと同様です。<br />・は、トランスポートと SOAP メッセージング層の両方でセキュリティを提供します。 同じ資格情報が、両方のレベルで要求されます。<br /><br /> 既定値は、Transport です。 この属性は <xref:System.ServiceModel.NetMsmqSecurityMode> 型です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|SOAP メッセージのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> 型です。|  
|[\<transport>](transport-of-netmsmqbinding.md)|MSMQ トランスポートのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|バインド|[ \<Netmsmqbinding のバインド要素 >](netmsmqbinding.md)|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
- [WCF のキュー](../../../wcf/feature-details/queues-in-wcf.md)

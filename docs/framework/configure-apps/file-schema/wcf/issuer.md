---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929372"
---
# <a name="issuer"></a>\<発行者の >
セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。  
  
 \<system.serviceModel>  
\<bindings>  
\<wsFederationHttpBinding >  
\<binding>  
\<セキュリティ >  
\<message>  
\<発行者の >  
  
## <a name="syntax"></a>構文  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|address|必須の文字列。 STS の URL です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。|  
|[\<identity>](identity.md)|発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|WsFederationHttpBinding > 要素の[ \<](wsfederationhttpbinding.md)メッセージレベルセキュリティの設定を定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [カスタム バインドを使用したセキュリティ機能](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)

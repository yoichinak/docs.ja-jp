---
title: <transport> の <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 98cdaa86441f91552c7133d8e5694f88019a6dbf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399279"
---
# <a name="transport-of-webhttpbinding"></a>\<webHttpBinding の\<トランスポート > >
HTTP 要求を受信するように構成されたサービス エンドポイントのトランスポート レベルのセキュリティ設定を定義します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<バインド >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<バインド >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<セキュリティ >** ](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<トランスポート >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a>型  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`clientCredentialType`|サービスに対するクライアントの認証に使用される資格情報を指定します。 この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。|  
|`proxyCredentialType`|ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。 この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。|  
|`realm`|ダイジェストまたは基本認証の認証レルムを指定する文字列。 既定値は空の文字列です。<br /><br /> 認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。 アクセス権のあるユーザーのコレクションも指定できます。 ユーザーは、認証レルムを照会して、複数のユーザー名およびパスワードの候補のうち、どれを使用できるかを確認することができます。|  
|`policyEnforcement`|この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。<br /><br /> 1. Never – ポリシーが適用されることはありません (拡張保護は無効になります)。<br />2. WhenSupported – ポリシーが適用されるのは、クライアントが拡張保護をサポートしている場合のみです。<br />3.Always – ポリシーは常に適用されます。 拡張保護をサポートしていないクライアントは認証に失敗します。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|`None`|セキュリティを無効にします。|  
|`Basic`|基本認証を使用します。|  
|`Certificate`|X.509 証明書を使用して、クライアントを認証します。|  
|`Digest`|ダイジェスト認証を使用します。|  
|`Ntlm`|Windows ドメインのフォールバックとして NTLM 認証を使用します。|  
|`Windows`|統合 Windows 認証を使用します。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|`None`|セキュリティを無効にします。|  
|`Basic`|基本認証を使用します。|  
|`Digest`|ダイジェスト認証を使用します。|  
|`Ntlm`|Windows ドメインのフォールバックとして NTLM を使用します。|  
|`Windows`|統合 Windows 認証を使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|WsHttpBinding > 要素の[ \<](wshttpbinding.md)セキュリティ機能を表します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
- [WCF Web HTTP プログラミング モデル](../../../wcf/feature-details/wcf-web-http-programming-model.md)

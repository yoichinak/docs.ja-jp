---
title: <transport> の <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 3d305c90233e4af7dde2a0b80e79e2adbe85c356
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360011"
---
# <a name="transport-of-basichttpbinding"></a>\<トランスポート > の\<basicHttpBinding >
HTTP トランスポートの認証パラメーターを制御するプロパティを定義します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<basicHttpBinding>  
\<binding>  
\<セキュリティ >  
\<transport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|clientCredentialType|-HTTP 認証を使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。  既定値は `None` です。 この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。|  
|proxyCredentialType|-HTTP 経由でプロキシを使用してドメイン内からクライアント認証を実行するときに使用される資格情報の種類を指定します。 この属性は、親 `mode` 要素の `security` 属性が `Transport` または `TransportCredentialsOnly` の場合にだけ適用されます。 この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。|  
|realm|ダイジェストまたは基本認証の HTTP 認証方式によって使用されるレルムを指定する文字列。 既定値は空の文字列です。|  
|policyEnforcement|この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。<br /><br /> 1.Never – ポリシーが適用されることはありません (拡張保護は無効になります)。<br />2.WhenSupported – ポリシーが適用されるのは、クライアントが拡張保護をサポートしている場合のみです。<br />3.Always – ポリシーは常に適用されます。 拡張保護をサポートしていないクライアントは認証に失敗します。|  
|protectionScenario|この列挙体は、ポリシーによって適用される保護シナリオを指定します。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|メッセージは、転送中はセキュリティで保護されません。|  
|Basic|基本認証を指定します。|  
|Digest|ダイジェスト認証を指定します。|  
|Ntlm|Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。|  
|Windows|Windows 統合認証を指定します。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|メッセージの数は、転送中にセキュリティ保護されません。|  
|Basic|RFC 2617 – HTTP Authentication で定義されている基本認証を指定します。基本認証とダイジェスト認証です。|  
|Digest|RFC 2617 – HTTP Authentication で定義されている、ダイジェスト認証を指定します。基本認証とダイジェスト認証です。|  
|Ntlm|Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。|  
|Windows|Windows 統合認証を指定します。|  
|証明書|証明書を使用したクライアント認証を実行します。 このオプションは、親要素の `Mode` の `security` 属性が Transport に設定されている場合のみ機能し、TransportCredentialOnly に設定されている場合は機能しません。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|セキュリティ機能を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)します。|  
  
## <a name="example"></a>例  
 基本的なバインディングを使用した SSL トランスポート セキュリティの使用例を次に示します。 既定で、基本的なバインディングは HTTP 通信をサポートします。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)

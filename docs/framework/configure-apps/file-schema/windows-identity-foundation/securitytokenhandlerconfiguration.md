---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 29e18cdda9e18addef4f0f32fd30e9abf6af78fc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360408"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration>
トークン ハンドラーのコレクションの構成を提供します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|saveBootstrapContext|セッション トークンにブートス トラップ トークンを含める必要があるかどうかを指定します。 設定して、値がトークン ハンドラー コレクションに設定することも可能性があります、`saveBootstrapContext`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスの設定値をオーバーライドします。|  
|maximumClockSkew|A<xref:System.TimeSpan>許可されている最大のクロック スキューを指定します。 サインイン セッションの有効期限の検証などの時間を区別する操作を実行するときは、最大の許可されている時刻のずれを制御します。 既定値は 5 分間、"00: 継続"。 指定する方法の詳細についての<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)します。 設定して、最大クロック スキューがサービス レベルで設定することも可能性があります、`maximumClockSkew`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスの設定値をオーバーライドします。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<audienceUris>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|この証明書利用者の許容可能な識別子 Uri のセットを指定します。 任意。|  
|[\<caches>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|セッション トークンやトークン リプレイ検出のために使用されるキャッシュを登録します。 サービス レベルまたはセキュリティ トークン ハンドラー コレクションに指定できます。 任意。|  
|[\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|トークン ハンドラーを使用して証明書の検証の設定を制御します。 サービス レベルまたはセキュリティ トークン ハンドラー コレクションに指定できます。 特定のハンドラーが、独自の検証ツールで構成されている場合、これらの設定が上書きされます。 任意。|  
|[\<issuerNameRegistry>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|トークン ハンドラー コレクションのハンドラーによって使用される発行者名レジストリを構成します。 任意。|  
|[\<issuerTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|トークン ハンドラー コレクションのハンドラーによって使用される発行者トークン リゾルバーを登録します。 発行者トークン リゾルバーを使用して、受信トークンおよびメッセージの署名トークンを解決します。 任意。|  
|[\<serviceTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|トークン ハンドラー コレクションのハンドラーによって使用されるサービス トークン リゾルバーを登録します。 サービス トークン リゾルバーを使用して、受信トークンおよびメッセージの暗号化トークンを解決します。 任意。|  
|[\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|トークン リプレイ検出が有効にし、トークンの有効期限を指定します。 サービス レベルまたはセキュリティ トークン ハンドラー コレクションに指定できます。 任意。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>Remarks  
 このセクションのプロパティ値を提供する、<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>オブジェクト。 このセクションで構成した設定は、サービスで構成されているものをオーバーライドします。 これらの設定の一部は、ハンドラーがセキュリティ トークン ハンドラー コレクションに追加されたときに指定されている設定によってさらに、オーバーライドことができます。  
  
## <a name="example"></a>例  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```

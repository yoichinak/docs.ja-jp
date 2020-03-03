---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251887"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration >
トークンハンドラーのコレクションの構成を提供します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<システムの >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<構成 >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**  
  
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
|saveBootstrapContext|ブートストラップトークンをセッショントークンに含める必要があるかどうかを指定します。 また、値は、トークンハンドラーコレクションに対して設定すること`saveBootstrapContext`もできます。これを行うには、identity [ \<configuration >](identityconfiguration.md)要素の属性を設定します。 トークンハンドラーコレクションに設定された値は、サービスで設定された値よりも優先されます。|  
|maximumClockSkew|許容される最大のクロックスキューを指定する。<xref:System.TimeSpan> サインインセッションの有効期限の検証など、時間を区別する操作を実行するときに許容される最大のクロックスキューを制御します。 既定値は5分 "00:05:00" です。 値を指定<xref:System.TimeSpan>する方法の詳細については、「 [Timespan values](../windows-workflow-foundation/index.md)」を参照してください。 また、サービスレベルでは、 `maximumClockSkew` [ \<identity configuration >](identityconfiguration.md)要素の属性を設定することによって、時刻のずれの最大値を設定することもできます。 トークンハンドラーコレクションに設定された値は、サービスで設定された値よりも優先されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|この証明書利用者の許容される識別子である Uri のセットを指定します。 任意。|  
|[\<キャッシュ >](caches.md)|セッショントークンとトークンリプレイ検出に使用されるキャッシュを登録します。 は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。 任意。|  
|[\<certificateValidation >](certificatevalidation.md)|トークンハンドラーが証明書を検証するために使用する設定を制御します。 は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。 特定のハンドラーが独自の検証コントロールを使用して構成されている場合、これらの設定はオーバーライドされます。 任意。|  
|[\<issuerNameRegistry >](issuernameregistry.md)|トークンハンドラーコレクションのハンドラーによって使用される発行者名レジストリを構成します。 任意。|  
|[\<issuerTokenResolver >](issuertokenresolver.md)|トークンハンドラーコレクションのハンドラーによって使用される発行者トークンリゾルバーを登録します。 発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。 任意。|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|トークンハンドラーコレクションのハンドラーによって使用されるサービストークンリゾルバーを登録します。 サービストークンリゾルバーは、受信トークンとメッセージの暗号化トークンを解決するために使用されます。 任意。|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|トークンリプレイ検出を有効にし、トークンの有効期限を指定します。 は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。 任意。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>Remarks  
 このセクションでは、 <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>オブジェクトのプロパティ値を提供します。 このセクションで構成した設定は、サービスで構成されている設定よりも優先されます。 これらの設定の一部は、ハンドラーがセキュリティトークンハンドラーコレクションに追加されたときに指定される設定によってオーバーライドされることがあります。  
  
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

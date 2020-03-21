---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152568"
---
# <a name="securitytokenhandlerconfiguration"></a>\<>を構成します。
トークン ハンドラーのコレクションの構成を提供します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<id構成>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
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
|ブートストラップコンテキストを保存します。|ブートストラップ トークンをセッション トークンに含めるかどうかを指定します。 この値は`saveBootstrapContext`[\<、idConfiguration>](identityconfiguration.md)要素の属性を設定することで、トークン ハンドラー コレクションに設定することもできます。 トークン ハンドラー コレクションに設定された値は、サービスに設定されている値をオーバーライドします。|  
|最大時計の傾斜|許容<xref:System.TimeSpan>される最大クロック スキューを指定する A。 サインイン セッションの有効期限を検証するなど、時間を区別する操作を実行する際に許容される最大クロック スキューを制御します。 デフォルトは 5 分の "00:05:00" です。 値の指定<xref:System.TimeSpan>方法の詳細については、「[タイムスパン値](../windows-workflow-foundation/index.md)」を参照してください。 最大クロック スキューは[\<、identityConfiguration>](identityconfiguration.md)要素の属性を`maximumClockSkew`設定することによって、サービス レベルで設定することもできます。 トークン ハンドラー コレクションに設定された値は、サービスに設定されている値をオーバーライドします。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<聴衆>を尿](audienceuris.md)|この証明書利用者の受け入れ可能な識別子である URI のセットを指定します。 省略可能。|  
|[\<キャッシュ>](caches.md)|セッション トークンおよびトークンの再生検出に使用されるキャッシュを登録します。 サービス レベルまたはセキュリティ トークン ハンドラーコレクションで指定できます。 省略可能。|  
|[\<証明書検証>](certificatevalidation.md)|トークン ハンドラーが証明書の検証に使用する設定を制御します。 サービス レベルまたはセキュリティ トークン ハンドラーコレクションで指定できます。 特定のハンドラーが独自の検証コントロールで構成されている場合、これらの設定はオーバーライドされます。 省略可能。|  
|[\<レジストリ>](issuernameregistry.md)|トークン ハンドラーコレクション内のハンドラーによって使用される発行者名レジストリを構成します。 省略可能。|  
|[\<>](issuertokenresolver.md)|トークン ハンドラー コレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。 発行者トークン リゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。 省略可能。|  
|[\<>](servicetokenresolver.md)|トークン ハンドラー コレクション内のハンドラーによって使用されるサービス トークン リゾルバーを登録します。 サービス トークン リゾルバーは、受信トークンとメッセージの暗号化トークンを解決するために使用されます。 省略可能。|  
|[\<トークンリプレイ検出>](tokenreplaydetection.md)|トークン再生検出を有効にし、トークンの有効期限を指定します。 サービス レベルまたはセキュリティ トークン ハンドラーコレクションで指定できます。 省略可能。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>](securitytokenhandlers.md)|エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>解説  
 このセクションでは、オブジェクトのプロパティ<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>値を提供します。 このセクションで構成した設定は、サービスで構成された設定よりも優先されます。 これらの設定の一部は、セキュリティ トークン ハンドラーのコレクションにハンドラーが追加されるときに指定された設定によってオーバーライドされる場合があります。  
  
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

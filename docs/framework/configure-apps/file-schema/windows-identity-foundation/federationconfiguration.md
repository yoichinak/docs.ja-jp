---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152737"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
WS フェデレーション<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>プロトコルを使用してフェデレーション認証<xref:System.IdentityModel.Services.SessionAuthenticationModule>を使用する場合に、(WSFAM) と (SAM) を構成します。 または クラス<xref:System.Security.Claims.ClaimsAuthorizationManager>を使用してクレーム<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>ベースのアクセス制御を提供する場合に を構成します。 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<サービス>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<フェデレーション構成>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|フェデレーション構成要素の名前。 この属性は、主に将来のプロトコルの拡張ポイントを提供します。 省略可能。|  
|構成名|[ \<identityConfiguration>](identityconfiguration.md)要素で指定されている ID 構成セクションの名前。 この属性を指定しない場合は、デフォルトの ID 構成セクションが使用されます。 省略可能。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<クッキーハンドラー>](cookiehandler.md)|SAM によって使用されるクッキー ハンドラーを構成します。 省略可能。|  
|[\<サービス証明書>](servicecertificate.md)|トークンの暗号化と復号化に使用される証明書を構成します。 省略可能。|  
|[\<ws フェデレーション>](wsfederation.md)|WS フェデレーション認証モジュール (WSFAM) を構成します。 省略可能。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<サービス>](system-identitymodel-services.md)|WS フェデレーション プロトコルを使用した認証の構成セクション。|  
  
## <a name="remarks"></a>解説  
 フェデレーション\<構成>要素は、2 つの異なるシナリオで設定を提供します。  
  
- パッシブ Web アプリケーションで WS フェデレーションを使用する場合、要素には<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) と<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) を構成する設定が含まれています。 また、セキュリティ トークン ハンドラーと証明書の構成に使用する ID 構成、およびクレーム承認マネージャーやクレーム認証マネージャーなどのコンポーネントも参照します。  
  
- <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または クラスを<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>使用してコードでクレーム ベースのアクセス制御を提供する場合、要素は、承認の決定に使用される要求承認マネージャーとポリシーを構成する ID 構成を参照します。 これは、パッシブ Web シナリオではないシナリオでも同様です。たとえば、WCF (Windows 通信財団) アプリケーションや Web ベースではないアプリケーションなどです。 アプリケーションがパッシブ Web アプリケーションでない場合、`<federationConfiguration>`[\<要素](claimsauthorizationmanager.md)によって参照される ID 構成の claimsAuthorizationManager>要素 (およびその子ポリシー要素がある場合) だけが適用されます。 他の属性はすべて無視されます。  
  
 シナリオに関係なく、ランタイムは既定のフェデレーション構成を読み込みます。 動作は次のように定義されます。  
  
1. 要素が存在しない`<federationConfiguration>`場合、ランタイムはフェデレーション構成を作成し、既定値を設定します。 この既定のフェデレーション構成は、既定の ID 構成を参照します。  
  
2. 1 つの`<federationConfiguration>`要素が存在する場合、名前が付いているか名前が付けられていないかにかかわらず、既定のフェデレーション構成になります。 属性が`identityConfiguration`指定されている場合は、名前付き ID 構成が参照されます。それ以外の場合は、既定の ID 構成が参照されます。  
  
3. 名前`<federationConfiguration>`のない要素が存在する場合、その要素は既定のフェデレーション構成です。 属性が`identityConfiguration`指定されている場合は、名前付き ID 構成が参照されます。それ以外の場合は、既定の ID 構成が参照されます。  
  
4. 複数の名前`<federationConfiguration>`付き要素が存在し、`<federationConfiguration>`名前のない要素が存在しない場合は、例外がスローされます。  
  
 通常、1 つの`<federationConfiguration>`セクションのみが定義されます。 このセクションは、既定のフェデレーション構成です。 複数の一意の名前`<federationConfiguration>`の要素を指定できます。ただし、この場合、名前のない構成以外のフェデレーション構成をロードする場合は、 に対してハンドラーを指定する必要があります。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>イベントを設定し<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>、ハンドラー内のプロパティを<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>構成ファイル内の適切な`<federationConfiguration>`要素の値で初期化されたオブジェクトに設定します。  
  
 要素`<federationConfiguration>`は<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>クラスによって表されます。 構成オブジェクト自体は<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>、クラスによって表されます。 プロパティに<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>単一のインスタンスが<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>設定され、アプリケーションのフェデレーション構成が提供されます。  
  
## <a name="example"></a>例  
 次の XML`<federationConfiguration>`は、WSFAM の設定を指定し、既定の Cookie ハンドラー (<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラスのインスタンス) を SAM で使用することを指定する要素を示しています。  
  
> [!WARNING]
> この例では、HTTPS を使用するために Cookie ハンドラーも WSFAM も必要ありません。 これは、要素の`requireHttps`属性と`<wsFederation>`の`requireSsl`属性`<cookieHandlerElement>`が であるためです`false`。 これらの設定は、セキュリティ上のリスクが生じる可能性があるため、ほとんどの運用環境では推奨されません。  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"
      issuer="http://localhost:15839/wsFederationSTS/Issue"
      realm="http://localhost:50969/" reply="http://localhost:50969/"
      requireHttps="false"
      signOutReply="http://localhost:50969/SignedOutPage.html"
      signOutQueryString="Param1=value2&Param2=value2"
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<id構成>](identityconfiguration.md)

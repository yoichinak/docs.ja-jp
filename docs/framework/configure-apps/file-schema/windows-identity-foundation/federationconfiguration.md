---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: c4dbb31bb7961f0d33df9d1faee8fe36ecb520a3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988327"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Ws-federation プロトコル<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>を介してフェデレーション認証を<xref:System.IdentityModel.Services.SessionAuthenticationModule>使用する場合、(wsfam) と (SAM) を構成します。 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>また<xref:System.Security.Claims.ClaimsAuthorizationManager> は<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クラスを使用してクレームベースのアクセス制御を提供するときに、を構成します。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
  
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
|name|このフェデレーション構成要素の名前。 この属性は、主に将来のプロトコルの機能拡張ポイントを提供します。 任意。|  
|identity Configurationname|使用するユーザー [ \<構成 >](identityconfiguration.md)要素で指定されている id 構成セクションの名前。 この属性が指定されていない場合は、既定の id 構成セクションが使用されます。 任意。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler >](cookiehandler.md)|SAM によって使用されるクッキーハンドラーを構成します。 任意。|  
|[\<serviceCertificate >](servicecertificate.md)|トークンの暗号化と復号化に使用される証明書を構成します。 任意。|  
|[\<wsFederation >](wsfederation.md)|WS-FEDERATION 認証モジュール (WSFAM) を構成します。 任意。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|WS-FEDERATION プロトコルを使用した認証の構成セクション。|  
  
## <a name="remarks"></a>Remarks  
 FederationConfiguration \<> 要素は、次の2つの異なるシナリオで設定を提供します。  
  
- パッシブ Web アプリケーションで ws-federation を使用する場合、要素には、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (wsfam) <xref:System.IdentityModel.Services.SessionAuthenticationModule>と (SAM) を構成する設定が含まれます。 また、セキュリティトークンハンドラーと証明書の構成に使用される id 構成と、要求承認マネージャーや要求認証マネージャーなどのコンポーネントも参照しています。  
  
- <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>クラスまたはクラスを使用して、コード内にクレームベースのアクセス制御を提供する場合、要素は、承認を行うために使用される要求承認マネージャーとポリシーを構成する id 構成を参照します。 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>行う. これは、パッシブな Web シナリオではないシナリオでも当てはまります。たとえば、Windows Communication Foundation (WCF) アプリケーションや、Web ベースではないアプリケーションなどです。 アプリケーションがパッシブな Web アプリケーション`<federationConfiguration>` [ \<](claimsauthorizationmanager.md)でない場合は、要素によって参照される id 構成の claimsAuthorizationManager > 要素とその子ポリシー要素 (存在する場合) が唯一の設定になります。適用. 他の属性はすべて無視されます。  
  
 シナリオに関係なく、ランタイムは既定のフェデレーション構成を読み込みます。 動作は次のように定義されています。  
  
1. `<federationConfiguration>`要素が存在しない場合、ランタイムはフェデレーション構成を作成し、既定値を設定します。 この既定のフェデレーション構成では、既定の id 構成が参照されます。  
  
2. 1つ`<federationConfiguration>`の要素が存在する場合は、名前が付けられているか名前が付いていないかに関係なく、既定のフェデレーション構成になります。 `identityConfiguration`属性が指定されている場合は、名前付き id 構成が参照されます。それ以外の場合は、既定の id 構成が参照されます。  
  
3. 名前`<federationConfiguration>`のない要素が存在する場合は、既定のフェデレーション構成になります。 `identityConfiguration`属性が指定されている場合は、名前付き id 構成が参照されます。それ以外の場合は、既定の id 構成が参照されます。  
  
4. 複数の名前`<federationConfiguration>`付き要素が存在し、 `<federationConfiguration>`名前のない要素が存在しない場合は、例外がスローされます。  
  
 通常、1つ`<federationConfiguration>`のセクションのみが定義されます。 このセクションは、既定のフェデレーション構成です。 一意の名前`<federationConfiguration>`を持つ複数の要素を指定することもできます。ただし、この場合は、名前のないフェデレーション構成を読み込む場合は、のハンドラーを指定する必要があります。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>イベントを発生さ<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>せると共に、ハンドラー内のプロパティを、構成ファイル`<federationConfiguration>`内の適切な要素の値で初期化されたオブジェクトに設定します。  
  
 要素は、 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>クラスによって表されます。 `<federationConfiguration>` 構成オブジェクト自体は、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>クラスによって表されます。 1つ<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>のインスタンスが<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティに設定され、アプリケーションのフェデレーション構成が提供されます。  
  
## <a name="example"></a>例  
 次の XML は、 `<federationConfiguration>` wsfam の設定を指定する要素を示し、既定の cookie ハンドラー ( <xref:System.IdentityModel.Services.ChunkedCookieHandler>クラスのインスタンス) が SAM によって使用されることを指定します。  
  
> [!WARNING]
> この例では、cookie ハンドラーも WSFAM も HTTPS を使用する必要はありません。 これは、 `<wsFederation>`要素`requireHttps`の属性と`requireSsl`の`<cookieHandlerElement>`属性が`false`であるためです。 ほとんどの運用環境では、セキュリティ上のリスクが生じる可能性があるため、これらの設定は推奨されません。  
  
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
- [\<identityConfiguration>](identityconfiguration.md)

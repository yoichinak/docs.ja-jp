---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: e1e92fccfad792fc1b9df86a582f0406a87f34e9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195294"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
構成、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) と<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) を使用する場合は、Ws-federation プロトコルを使用した認証をフェデレーションします。 構成、<xref:System.Security.Claims.ClaimsAuthorizationManager>を使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クレーム ベースのアクセス制御を提供するクラス。  
  
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
|name|このフェデレーションの構成要素の名前。 主に、この属性は、将来のプロトコルの機能拡張ポイントを提供します。 任意。|  
|identityConfigurationName|指定されている id の構成セクションの名前、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)を使用する要素。 この属性が指定されていない場合は、既定の id 構成セクションが使用されます。 省略可能です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|SAM で使用されるクッキー ハンドラーを構成します。 任意。|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|暗号化し、トークン暗号化解除に使用される証明書を構成します。 任意。|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Ws-federation 認証モジュール (WSFAM) を構成します。 任意。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Ws-federation プロトコルを使用して認証用の構成セクション。|  
  
## <a name="remarks"></a>Remarks  
 \<FederationConfiguration > 要素が 2 つのシナリオでの設定を提供します。  
  
-   構成設定が要素に含まれる WS フェデレーション パッシブ Web アプリケーションを使用する場合、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) と<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。 セキュリティ トークン ハンドラーと証明書、およびクレーム承認マネージャーやクレーム認証マネージャーなどのコンポーネントの構成に使用する id の構成も参照します。  
  
-   使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コード内のクレーム ベースのアクセス制御を提供するクラス、要素の参照クレーム承認マネージャーおよび承認を使用してポリシーを構成する id の構成決定します。 これが true の場合は受動的な Web シナリオ以外ではないシナリオであってもたとえば、Windows Communication Foundation (WCF) アプリケーションまたはアプリケーションを Web ベースではありません。 アプリケーションが、パッシブの Web アプリケーションではない場合、 [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素 (とその子ポリシー要素、存在する場合) によって参照される id の構成、`<federationConfiguration>`要素唯一の設定が適用されます。 他の属性はすべて無視されます。  
  
 シナリオに関係なく、ランタイムは既定のフェデレーション構成を読み込みます。 動作の定義は次のとおりです。  
  
1.  存在する場合ありません`<federationConfiguration>`要素が存在する、ランタイムは、フェデレーションの構成を作成し、既定値を設定します。 この既定のフェデレーション構成では、既定の id 構成を参照します。  
  
2.  場合、1 つ`<federationConfiguration>`要素が存在する、という名前または名前のないに関係なく、既定のフェデレーション構成になります。 場合その`identityConfiguration`属性を指定すると、名前付きの id 構成の参照。 それ以外の場合、既定の id 構成が参照されています。  
  
3.  場合、名前のない`<federationConfiguration>`要素が存在する、これは既定のフェデレーション構成します。 場合その`identityConfiguration`属性を指定すると、名前付きの id 構成の参照。 それ以外の場合、既定の id 構成が参照されています。  
  
4.  複数の名前の場合`<federationConfiguration>`要素が存在しない名前のない`<federationConfiguration>`要素が存在する、例外がスローされます。  
  
 通常、1 つだけ`<federationConfiguration>`セクションを定義します。 このセクションでは、既定のフェデレーション構成です。 複数の一意な名前を指定することがあります`<federationConfiguration>`要素です。 ただし、この場合、名前のないものと異なるフェデレーションの構成を読み込む場合は、する必要がありますハンドラーを提供の、します。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> イベントとセット、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>するハンドラー内のプロパティを<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトから、適切な値で初期化`<federationConfiguration>`構成ファイル内の要素。  
  
 `<federationConfiguration>`要素が表される、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>クラス。 構成オブジェクト自体がによって表される、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>クラス。 1 つ<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>インスタンスが設定されて、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティと、アプリケーションのフェデレーションの構成を提供します。  
  
## <a name="example"></a>例  
 次の XML に示します、 `<federationConfiguration>` WSFAM の設定を指定することを指定します、既定の cookie ハンドラー (のインスタンス、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス) SAM で使用します。  
  
> [!WARNING]
>  この例では、HTTPS を使用するクッキー ハンドラーも WSFAM が必要です。 これは、ため、`requireHttps`属性を`<wsFederation>`要素と`requireSsl`属性を`<cookieHandlerElement>`は`false`します。 これらの設定は、セキュリティ リスクが存在する場合がほとんどの運用環境の推奨されません。  
  
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
- [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)

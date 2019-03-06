---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 9728f3caee4dba367e4fc4a3e68213b1055cc3d1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362956"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Ws-federation プロトコルを使用して認証用の構成セクション。  
  
 \<system.identityModel.services>  
  
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
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) と<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) HTTP モジュールです。|  
  
### <a name="parent-elements"></a>親要素  
 なし  
  
## <a name="remarks"></a>Remarks  
 追加、 `<system.identityModel.services>` SAM と WSFAM の設定を提供するアプリケーションの構成ファイルにセクション。  
  
> [!IMPORTANT]
>  使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>、コードでは、クレーム承認マネージャーでのクレームに基づくアクセス制御を提供するクラス (<xref:System.Security.Claims.ClaimsAuthorizationManager>) を通じて承認決定を行うために使用するポリシーが構成されていると、 `<identityConfiguration>`暗黙的または明示的に参照される要素を`<federationConfiguration>`このセクションの要素。 詳細については、次を参照してください。、**解説**下、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。  
  
 `<system.identityModel.services>`セクションがによって表される、<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>クラス。 子のコレクション`<federationConfiguration>`のセクションの構成要素として表されます、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>クラス。  
  
## <a name="example"></a>例  
 次の XML を追加する方法を示しています、`<system.identityModel.services>`構成ファイルにセクション。 両方のセクションの宣言を追加する必要があります最初、`<system.identityModel.services>`セクションおよび`<system.identityModel>`セクション。 (追加すると、`<system.identityModel.services>`セクションの宣言も追加する必要があります、`<system.identityModel>`ことに、既定値を確認するセクション`<identityConfiguration>`セクションは、必要な場合、ランタイムによって作成できます)。フェデレーション認証設定を構成できますセクション宣言を追加した後、`<system.identityModel.services>`要素。  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```

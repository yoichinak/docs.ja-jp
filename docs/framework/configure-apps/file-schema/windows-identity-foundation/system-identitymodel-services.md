---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e9488c0681e1a5f0fe94112a36b65ec73bf9fd09
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251806"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
WS-FEDERATION プロトコルを使用した認証の構成セクション。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp; **\<> のシステム**  
  
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
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfam) <xref:System.IdentityModel.Services.SessionAuthenticationModule>および (SAM) HTTP モジュールを構成する設定が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
 なし  
  
## <a name="remarks"></a>Remarks  
 アプリケーションの`<system.identityModel.services>`構成ファイルにセクションを追加して、SAM と wsfam の設定を指定します。  
  
> [!IMPORTANT]
> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> `<identityConfiguration>`クラスまたはクラスを使用して、コード内にクレームベースのアクセス制御を提供する場合、<xref:System.Security.Claims.ClaimsAuthorizationManager>承認の決定に使用される要求承認マネージャー () とポリシーは、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>このセクションの`<federationConfiguration>`要素から暗黙的または明示的に参照される要素。 詳細については、「 [ \<federationConfiguration >](federationconfiguration.md)要素」の「**解説**」を参照してください。  
  
 セクションは、 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>クラスによって表されます。 `<system.identityModel.services>` セクションで構成さ`<federationConfiguration>`れた子要素のコレクションは、 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>クラスによって表されます。  
  
## <a name="example"></a>例  
 次の XML は、構成ファイルに`<system.identityModel.services>`セクションを追加する方法を示しています。 まず、セクション`<system.identityModel.services>` `<system.identityModel>`とセクションの両方にセクション宣言を追加する必要があります。 ( `<system.identityModel.services>`セクションを追加する場合は、必要に応じて、ランタイムが`<system.identityModel>`既定`<identityConfiguration>`のセクションを作成できるように、セクションの宣言も追加する必要があります)。セクション宣言を追加した後、要素の`<system.identityModel.services>`下にフェデレーション認証設定を構成できます。  
  
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

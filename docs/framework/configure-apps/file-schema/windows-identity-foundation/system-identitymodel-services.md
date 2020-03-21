---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152505"
---
# <a name="systemidentitymodelservices"></a>\<サービス>
WS フェデレーション プロトコルを使用した認証の構成セクション。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;**\<サービス>**  
  
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
|[\<フェデレーション構成>](federationconfiguration.md)|(WSFAM)<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>および (SAM) HTTP<xref:System.IdentityModel.Services.SessionAuthenticationModule>モジュールを構成する設定が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
 なし  
  
## <a name="remarks"></a>解説  
 アプリケーションの`<system.identityModel.services>`構成ファイルにセクションを追加して、SAM と WSFAM の設定を提供します。  
  
> [!IMPORTANT]
> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クラスを使用してコード内でクレーム ベースのアクセス制御を提供する場合、承認の<xref:System.Security.Claims.ClaimsAuthorizationManager>決定を行うために使用されるクレーム承認マネージャー ( )`<identityConfiguration>`とポリシーは、このセクションの要素から暗黙的または明示的`<federationConfiguration>`に参照される要素を使用して構成されます。 詳細については、[\<フェデレーション構成>](federationconfiguration.md)要素の**下の解説**を参照してください。  
  
 セクション`<system.identityModel.services>`は<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>クラスによって表されます。 セクションで構成された`<federationConfiguration>`子要素のコレクションは、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>クラスによって表されます。  
  
## <a name="example"></a>例  
 次の XML は、構成`<system.identityModel.services>`ファイルにセクションを追加する方法を示しています。 まず、セクションとセクションの両方にセクション宣言`<system.identityModel.services>`を追加する`<system.identityModel>`必要があります。 (セクションを`<system.identityModel.services>`追加する場合は、必要に応じてランタイムが既定`<system.identityModel>``<identityConfiguration>`のセクションを作成できるように、セクションの宣言も追加する必要があります)。セクション宣言を追加した後、要素の下でフェデレーション認証設定を`<system.identityModel.services>`構成できます。  
  
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

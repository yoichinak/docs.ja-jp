---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 34643d10ef1ed2e87152e5013634e62859e0594e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791769"
---
# <a name="add"></a>\<add>
トークン ハンドラー コレクションには、指定したセキュリティ トークン ハンドラーを追加します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|種類|追加するトークン ハンドラーの CLR 型名。 詳細を指定する方法については、`type`属性は、「[カスタム型の参照](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|構成を提供、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラス。|  
|[\<sessionTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|構成を提供、<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラス。|  
|[\<userNameSecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|構成を提供、<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラス。|  
|[\<x509SecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|オプションの構成を提供します、<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>クラスまたは派生クラス。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>Remarks  
 `<add>`要素がトークン ハンドラーの構成を指定する 1 つの子要素を取得します。 これはを通じてハンドラー クラスを参照するかどうかによって異なります、`type`の属性、`<add>`要素は、この機能のサポートを提供します。 この機能を提供するトークン ハンドラー クラスを受け取るコンス トラクターを公開する必要があります、<xref:System.Xml.XmlElement>オブジェクト。  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 この機能を提供、組み込みのセキュリティ トークン ハンドラー クラスのいくつかの操作を行います。 これらのクラスは<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、および<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>します。  
  
> [!IMPORTANT]
>  トークン ハンドラー コレクションには、任意の型の 1 つのハンドラーのみ含めることができます。 つまり、たとえばから派生したハンドラーを追加する場合、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラスのコレクションを削除する必要あります、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>は既定では、コレクションから存在します。 使用することができます、 [\<削除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)コレクションまたは使用してから、単一のハンドラーを削除する要素、 [\<オフ >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)コレクションからすべてのイベント ハンドラーを削除する要素。  
  
 ハンドラーで指定した設定の下に、トークン ハンドラー コレクションで指定された同等の設定を上書きする、 [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素とその下でサービス レベルで指定されています。[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。  
  
## <a name="example"></a>例  
 次の XML の使用を示しています、`<add>`と`<remove>`に既定のセッション トークン ハンドラーをカスタム セッション トークン ハンドラーに置き換える要素。 XML から取得されますが、`ClaimsAwareWebFarm`サンプル。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 932e8452542ace66824fba1262694c220ce88676
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252183"
---
# <a name="add"></a>\<add>
指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションに追加します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<システムの >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<構成 >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> の追加**  
  
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
|型|追加するトークンハンドラーの CLR 型名。 `type`属性を指定する方法の詳細については、「[カスタム型参照](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|クラス、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>またはこれらのクラスの派生クラスの構成を提供します。|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラスの構成を提供します。|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラスの構成を提供します。|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>クラスまたは派生クラスのオプションの構成を提供します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>Remarks  
 要素`<add>`は、トークンハンドラーの構成を指定する1つの子要素を受け取ることができます。 これは、 `type` `<add>`要素の属性を通じて参照されるハンドラークラスがこの機能をサポートするかどうかによって異なります。 この機能を提供するトークンハンドラークラスは、 <xref:System.Xml.XmlElement>オブジェクトを受け取るコンストラクターを公開する必要があります。  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 いくつかの組み込みセキュリティトークンハンドラークラスは、この機能を提供します。 これらのクラス<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>は<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>、、、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、およびです。  
  
> [!IMPORTANT]
> トークンハンドラーコレクションには、指定された任意の型の1つのハンドラーのみを含めることができます。 これは、たとえば、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラスから派生したハンドラーをコレクションに追加する場合は、最初にコレクションから既定で存在する<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>を削除する必要があることを意味します。 [ \<](clear.md) Remove > 要素を使用[ \<](remove.md)して、コレクションから1つのハンドラーを削除することも、clear > 要素を使用してコレクションからすべてのハンドラーを削除することもできます。  
  
 ハンドラーに対して指定された設定は、 [ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)要素の下にあるトークンハンドラーコレクションで指定された同等の[ \<設定よりも優先されます。>](identityconfiguration.md)要素。  
  
## <a name="example"></a>例  
 次の XML は、 `<add>`および`<remove>`要素を使用して、既定のセッショントークンハンドラーをカスタムセッショントークンハンドラーに置き換える方法を示しています。 XML は、「」の`ClaimsAwareWebFarm`サンプルから抜粋したものです。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

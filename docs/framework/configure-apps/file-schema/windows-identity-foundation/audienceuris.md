---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252169"
---
# <a name="audienceuris"></a>\<audienceUris>
証明書利用者 (RP) の許容される識別子である Uri のセットを指定します。 トークンは、許可されている対象ユーザーの Uri の1つを対象としている場合を除き、受け入れられません。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<システムの >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<構成 >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
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
|モード|対象ユーザーの制限を受信トークンに適用する必要があるかどうかを示す値です。<xref:System.IdentityModel.Selectors.AudienceUriMode> 指定できる値は、"Always"、"Never"、および "BearerKeyOnly" です。 既定値は "Always" です。 任意。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`<add value=xs:string>`|`value`属性によって指定された URI を audienceUris コレクションに追加します。 `value` 属性は必須です。 URI では大文字と小文字が区別されます。|  
|`<clear>`|AudienceUris コレクションをクリアします。 すべての識別子はコレクションから削除されます。|  
|`<remove value=xs:string>`|`value`属性によって指定された URI を audienceUris コレクションから削除します。 `value` 属性は必須です。 URI では大文字と小文字が区別されます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 既定では、コレクションは空です。コレクション`<add>`を`<clear>`変更する`<remove>`には、、、およびの各要素を使用します。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>オブジェクト<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>とオブジェクトは、audience uri コレクションの値を使用して、オブジェクトで<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>許可されている対象ユーザー uri 制限を構成します。  
  
 要素は、 <xref:System.IdentityModel.Configuration.AudienceUriElementCollection>クラスによって表されます。 `<audienceUris>` コレクションに追加された個々の URI は、 <xref:System.IdentityModel.Configuration.AudienceUriElement>クラスによって表されます。  
  
> [!NOTE]
> この`<audienceUris>`要素を、identity [ \<configuration >](identityconfiguration.md)要素の子要素として使用することは非推奨とされましたが、旧バージョンとの互換性のために引き続きサポートされています。 要素の設定`<securityTokenHandlerConfiguration>`は、要素の設定`<identityConfiguration>`よりも優先されます。  
  
## <a name="example"></a>例  
 次の XML は、アプリケーションに対して許容される対象ユーザーの Uri を構成する方法を示しています。 この例では、単一の URI を構成します。 この URI にスコープが設定されているトークンは受け入れられ、それ以外はすべて拒否されます。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```

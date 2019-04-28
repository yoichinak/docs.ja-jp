---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750749"
---
# <a name="audienceuris"></a>\<audienceUris>
利用者 (RP) の許容可能な識別子 Uri のセットを指定します。 許可された対象 Uri のいずれかのスコープがない限り、トークンは受け入れられません。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<audienceUris>  
  
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
|モード|<xref:System.IdentityModel.Selectors.AudienceUriMode>受信トークンに対象者制限を適用するかどうかを指定する値。 使用可能な値は、「常に」、"Never"、"BearerKeyOnly"。 既定では 常にです"。 任意。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`<add value=xs:string>`|指定された URI を追加、 `value` audienceUris のコレクションに属性します。 `value` 属性は必須です。 URI は、大文字小文字を区別します。|  
|`<clear>`|AudienceUris のコレクションをクリアします。 すべての識別子は、コレクションから削除されます。|  
|`<remove value=xs:string>`|指定された URI を削除、 `value` audienceUris のコレクションから属性。 `value` 属性は必須です。 URI は、大文字小文字を区別します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラー コレクションのセキュリティの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 既定では、コレクションが空です。使用して、 `<add>`、 `<clear>`、および`<remove>`コレクションを変更する要素。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>オブジェクトでいずれかを構成する対象ユーザー URI のコレクション内の値が対象ユーザー URI 制限を許可されている使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>オブジェクト。  
  
 `<audienceUris>`要素が表される、<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>クラス。 によって表されるコレクションに追加された個々 の URI、<xref:System.IdentityModel.Configuration.AudienceUriElement>クラス。  
  
> [!NOTE]
>  使用、`<audienceUris>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は非推奨とされましたが、旧バージョンとの互換性もサポートします。 上の設定、`<securityTokenHandlerConfiguration>`要素のオーバーライド、`<identityConfiguration>`要素。  
  
## <a name="example"></a>例  
 次の XML では、アプリケーションの許容される対象ユーザー Uri を構成する方法を示します。 この例では、単一の URI を設定します。 この URI のスコープのトークンが受け付けられます、他のすべてのユーザーは拒否されます。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```

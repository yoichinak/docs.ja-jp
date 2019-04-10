---
title: <add> <claimTypeRequirements>要素
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 47eb9f95fd024b7df24a16781b3d89fe6deb0b8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222186"
---
# <a name="add-of-claimtyperequirements-element"></a>\<add> of \<claimTypeRequirements> element
フェデレーション資格情報に表示されると予想される必須のクレームおよび省略可能なクレームの種類を指定します。 たとえば、サービスは、クレームの種類の特定のセットを処理する必要がある受信資格情報について要件を記述します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<wsFederatedBinding>  
\<binding>  
\<セキュリティ >  
\<message>  
\<claimTypeRequirements>  
  
## <a name="syntax"></a>構文  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|claimType|クレームの種類を定義する URI。 たとえば、Web サイトから製品を購入するために、ユーザーは、十分な与信限度額を備えた有効なクレジット カードを示す必要があります。 クレームの種類として、クレジット カードの URI があります。|  
|isOptional|これが省略可能なクレームかどうかを指定するブール値。 これが必須のクレームの場合は、この属性を `false` に設定します。<br /><br /> サービスが必須でない情報を求めるときにこの属性を使用できます。 たとえば、ユーザーに氏名と住所の入力を要求し、電話番号は省略可能にする場合などです。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|必須のクレームの種類のコレクションを指定します。 各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。<br /><br /> フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。 たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。 このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。|  
  
## <a name="remarks"></a>Remarks  
 フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。 たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。 この要件はセキュリティ ポリシー内に明記されます。 クライアントがフェデレーション サービスの資格情報 (CardSpace など) を要求する場合、クライアントは要件をトークン要求 (RequestSecurityToken) に設定します。これにより、フェデレーション サービスは、要件どおりの資格情報を発行できます。  
  
## <a name="example"></a>例  
 次の構成では、2 つのクレームの種類の要件をセキュリティ バインディングに追加しています。  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

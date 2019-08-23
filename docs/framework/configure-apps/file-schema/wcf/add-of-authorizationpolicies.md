---
title: <add> の <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920271"
---
# <a name="add-of-authorizationpolicies"></a>\<authorizationpolicies の\<> を追加 >
クレームの変換の承認ポリシーを指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<behavior>  
\<serviceAuthorization >  
\<authorizationPolicies >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`policyType`|必須の文字列属性。<br /><br /> Windows Communication Foundation (WCF) アクセス制御モデルは、一連の承認ポリシーを型としてプロビジョニングすることをサポートしています。 この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。 アクセス制御は、それに基づいて許可または拒否されます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|承認ポリシーの種類のコレクションを指定します。|  
  
## <a name="remarks"></a>Remarks  
 各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。 この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。 アクセス制御は、それに基づいて許可または拒否されます。 承認ポリシーのしくみの詳細については、 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 「」および「[承認ポリシー](../../../wcf/samples/authorization-policy.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [サービス操作へのアクセスの承認](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [方法: サービスのカスタム承認マネージャーを作成する](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [承認ポリシー](../../../wcf/samples/authorization-policy.md)

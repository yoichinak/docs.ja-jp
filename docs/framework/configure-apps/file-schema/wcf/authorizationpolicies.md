---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: d8ca43a7b633d7d19dd37ceb0ff64075931b6c5c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254772"
---
# <a name="authorizationpolicies"></a>\<authorizationPolicies>
この構成セクションには、`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションが含まれています。 各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。 この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。 アクセス制御は、それに基づいて許可または拒否されます。 承認ポリシーのしくみの詳細については、<xref:System.IdentityModel.Policy.IAuthorizationPolicy>と[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [サービス操作へのアクセスの承認](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [方法: サービスのカスタム承認マネージャーを作成します。](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)

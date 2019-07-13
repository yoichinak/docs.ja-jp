---
title: <remove> <claimTypeRequirements>要素
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 9ab1162ff5d86b8a9d43dae79ebf9c9321119206
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783098"
---
# <a name="remove-of-claimtyperequirements-element"></a>\<削除 > の\<claimTypeRequirements > 要素
フェデレーション資格情報から削除するクレームの種類を指定します。  
  
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
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|claimType|削除するクレームの種類を定義する URI。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|必須のクレームの種類のコレクションを指定します。 各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。<br /><br /> フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。 たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。 このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

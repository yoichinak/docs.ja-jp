---
title: <add> の <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 32eff2e7bfdf1aee4c7d37a0e06166afba3cb398
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566736"
---
# <a name="add-of-namespacetable"></a>\<namespaceTable > の\<> の追加
名前空間とプレフィックスのマッピングを含む構成要素を表します。これは、ルーティングの XPath フィルターで使用されます。  
  
 \<system.serviceModel>  
\<ルーティング >  
\<namespaceTable >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|名前空間|名前空間を示す文字列。|  
|prefix|この名前空間のプレフィックスを示す文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namespaceTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>

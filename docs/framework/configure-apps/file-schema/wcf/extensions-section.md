---
title: <extensions> セクション
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673005"
---
# <a name="extensions-section"></a>\<拡張機能 > セクション
この構成セクションには、拡張のコレクションが含まれています。この拡張のコレクションによってユーザーは、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できます。  
  
\<system.ServiceModel >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behaviorExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|このセクションには、動作拡張を指定する子要素が含まれています。この動作拡張により、ユーザーはサービスまたはエンドポイントの動作をカスタマイズできます。|  
|[\<bindingElementExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインディング要素を使用できます。|  
|[\<bindingExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|このセクションには、バインディング拡張を指定する子要素が含まれています。このバインディング拡張によって、ユーザーはバインディングをカスタマイズできます。|  
|[\<endpointExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|このセクションには、標準エンドポイントを登録する子要素が含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|system.ServiceModel|すべての WCF 構成要素のルート要素です。|

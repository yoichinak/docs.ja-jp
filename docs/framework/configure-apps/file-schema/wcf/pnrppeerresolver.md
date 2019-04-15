---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214054"
---
# <a name="pnrppeerresolver"></a>\<pnrpPeerResolver>
リゾルバーとして PNRP (Peer Name Resolution Protocol) リゾルバーを使用することを指定します。 PNRP は既定のリゾルバーであるため、この要素は省略可能です。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<pnrpResolver >  
  
## <a name="syntax"></a>構文  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|resolverType|使用されるリゾルバーを指定する文字列。 この属性は省略できます。 設定されていない場合、または空の文字列に設定されている場合は、PNRP が使用されます。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="example"></a>例  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [ピア リゾルバー](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

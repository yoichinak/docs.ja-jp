---
title: <add> の <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: fbcb3a07bf40c96a4cd1b2ec87277b6fefdfb89d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164477"
---
# <a name="add-of-baseaddresses"></a>\<add> of \<baseAddresses>
サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。  
  
 \<system.ServiceModel >  
\<client>  
\<endpoint>  
\<host>  
\<baseAddresses>  
\<baseAddress>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`baseAddress`|サービス ホストによって使用されるベース アドレスを指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddresses>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|`baseAddress` 要素のコレクション。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)

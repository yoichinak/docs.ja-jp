---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926419"
---
# <a name="baseaddresses"></a>\<baseAddresses >
自己ホスト環境でのサービス ホストのベース アドレスである `baseAddress` 要素のコレクションを表します。 ベース アドレスが存在すると、そのベース アドレスに関連したアドレスを使用してエンドポイントを構成できます。  
  
 \<system.ServiceModel >  
\<client>  
\<endpoint>  
\<ホスト >  
\<baseAddresses >  
  
## <a name="syntax"></a>構文  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|サービス ホストによって使用されるベース アドレスを指定する構成要素。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ホスト >](host.md)|サービス ホストの設定を指定する構成要素です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [ホスティング](../../../wcf/feature-details/hosting.md)

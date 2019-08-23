---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b159488efa2a80a9dea625e4c6dfe2f215dfc457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939185"
---
# <a name="timeouts"></a>\<タイムアウト >
サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。  
  
 \<system.ServiceModel >  
\<client>  
\<endpoint>  
\<ホスト >  
\<タイムアウト >  
  
## <a name="syntax"></a>構文  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`closeTimeout`|サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。|  
|`openTimeout`|サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ホスト >](host.md)|サービス ホストの設定を指定する構成要素です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [ホスティング](../../../wcf/feature-details/hosting.md)

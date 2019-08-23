---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925853"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization >
  
サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。  
  
\<system.serviceModel>  
\<<behaviors>  
\<endpointBehaviors>  
\<behavior>  
  
## <a name="syntax"></a>構文  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>種類  
  
`Type`  
  
## <a name="attributes-and-elements"></a>属性と要素  
  
以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性

| 属性               | 説明       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | 非同期の送信動作が有効かどうかを示すブール値。 |
| `maxPendingReceives`    | チャネルで発行可能な同時受信の数を指定する整数。<br /><br /> この値は、サービス調整の動作を適切に構成した後に構成する必要があります。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>

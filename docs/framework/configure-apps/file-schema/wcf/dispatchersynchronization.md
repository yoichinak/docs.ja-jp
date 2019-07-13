---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673408"
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
  
## <a name="type"></a>型  
  
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
| [\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>

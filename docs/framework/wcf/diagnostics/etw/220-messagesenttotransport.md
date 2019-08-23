---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948283"
---
# <a name="220---messagesenttotransport"></a>220 - MessageSentToTransport
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|Id|220|  
|キーワード|EndToEndMonitoring、Troubleshooting、ServiceModel|  
|レベル|[情報]|  
|Channel|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、サービス モデルがトランスポートにメッセージを送信すると生成されます。  
  
> [!NOTE]
> 一方向トランスポートでは、このイベントは発生しません。  
  
## <a name="message"></a>Message  
 ディスパッチャーがトランスポートにメッセージを送信しました。 関連付け ID == '%1'。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Correlation ID|`xs:GUID`|サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーション仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例:' 既定の Web サイト/計算 Atorapplication&#124;&#124;/計算 atoratorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|

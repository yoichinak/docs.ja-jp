---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964187"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|215|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|[情報]|  
|Channel|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、TCP ベースのトランスポートがメッセージを受信するときに発生します。 トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。 これはインフラストラクチャの動作によるもので、セキュリティがその一例です。 そのため、生成される `MessageReceivedByTransport` イベントの数が、サービスのバインディングとその構成に応じて異なります。  
  
> [!NOTE]
> 一方向トランスポートでは、このイベントは発生しません。  
  
## <a name="message"></a>Message  
 トランスポートが '%1' からメッセージを受信しました。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Listen Address|`xs:string`|メッセージを受信したアドレス。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーション仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例:' 既定の Web サイト/計算 Atorapplication&#124;&#124;/計算 atoratorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|

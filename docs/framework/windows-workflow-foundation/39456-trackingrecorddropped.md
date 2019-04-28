---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774427"
---
# <a name="39456---trackingrecorddropped"></a>39456 - TrackingRecordDropped
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|39456|  
|キーワード|WFTracking|  
|レベル|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。  
  
## <a name="message"></a>メッセージ  
 追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|

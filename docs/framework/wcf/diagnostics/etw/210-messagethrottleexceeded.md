---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781884"
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|210|  
|キーワード|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|レベル|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、3 つの主要なサービス スロットルの 1 つを超過したときに生成されます。 このイベントが生成されるのは、最初にスロットル制限を超過したときのみです。 たとえば、同時呼び出しのスロットル制限が 10 の場合は、11 番目の同時呼び出しが `MessageThrottleExceeded` イベントになります。 12 番目の呼び出しが別のイベントになることはありません。 また、イベント ストリームが煩雑になるのを避けるため、制限値の前後のアクティビティの結果が別のイベントになることはありません。 この例では、2 つの呼び出しが完了した場合、9 つの同時呼び出しが行われます。 続いて 2 つの呼び出しが行われた場合は、現在の値が再び 11 になります。 これは、別のイベントにはなりません。 現在の値がスロットル制限の 70% になると、アクティビティの遅れを示す別のイベントが生成されます。 以降のアクティビティが制限を超えた場合は、別の `MessageThrottleExceeded` イベントが生成されます。 この例では、同時呼び出しの数が 7 になり、再び 11 に達すると、別の `MessageThrottleExceeded` イベントが生成されます。  
  
## <a name="message"></a>メッセージ  
 スロットル '%1' の '%2' の制限に達しました。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Throttle Name|`xs:string`|超過したスロットルの名前。 `MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。|  
|Limit|`xs:long`|現在構成されている、スロットルの制限。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式が定義されている ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName'。 例:' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|

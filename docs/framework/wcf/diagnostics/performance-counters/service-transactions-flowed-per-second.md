---
title: サービス:1 秒あたりのトランザクション フロー
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: cb41abe74568c3e9641443b81fce3fb6eb6e41bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939413"
---
# <a name="service-transactions-flowed-per-second"></a>サービス:1 秒あたりのトランザクション フロー
カウンター名:1 秒あたりのトランザクション フロー。  
  
## <a name="description"></a>説明  
 このサービスでの操作に対して実行された 1 秒あたりのトランザクションの数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

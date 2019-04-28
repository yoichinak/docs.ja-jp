---
title: 1 秒あたりのトランザクション フロー
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927193"
---
# <a name="transactions-flowed-per-second"></a>1 秒あたりのトランザクション フロー
カウンター名:1 秒あたりのトランザクション フロー  
  
## <a name="description"></a>説明  
 この操作に対して実行された 1 秒あたりのトランザクションの数です。 このカウンターは、操作に送信されたメッセージにトランザクション ID が存在する場合にインクリメントされます。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

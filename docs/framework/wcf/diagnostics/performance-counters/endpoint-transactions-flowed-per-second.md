---
title: エンドポイント:1 秒あたりのトランザクション フロー
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916254"
---
# <a name="endpoint-transactions-flowed-per-second"></a>エンドポイント:1 秒あたりのトランザクション フロー
カウンター名:1 秒あたりのトランザクション フロー。  
  
## <a name="description"></a>説明  
 このエンドポイントでの操作に対して実行された 1 秒あたりのトランザクションの数です。 このカウンターは、エンドポイントに送信されたメッセージにトランザクション ID が付与されている場合は常にインクリメントされます。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

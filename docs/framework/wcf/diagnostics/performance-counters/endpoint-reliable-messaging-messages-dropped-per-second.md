---
title: エンドポイント:信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797203"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>エンドポイント:信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
カウンター名:1 秒あたりの破棄された信頼できるメッセージ セッション。  
  
## <a name="description"></a>説明  
 このエンドポイントで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

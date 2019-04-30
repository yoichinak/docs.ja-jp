---
title: エンドポイント:1 秒あたりのエラーとなった信頼できるメッセージ セッション
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: f6b48ec4c37c28588dd874a5bfa94a01a2f43b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951243"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>エンドポイント:1 秒あたりのエラーとなった信頼できるメッセージ セッション
カウンター名:信頼できるメッセージ セッションが 1 秒あたりのエラーが発生しました。  
  
## <a name="description"></a>説明  
 1 秒以内にこのエンドポイントでエラーになった信頼できるメッセージ セッション数。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

---
title: 1 秒あたりのエラーとなった信頼できるメッセージ セッション
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916124"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a>1 秒あたりのエラーとなった信頼できるメッセージ セッション
カウンター名:信頼できるメッセージ セッションが 1 秒あたりのエラーが発生しました。  
  
## <a name="description"></a>説明  
 1 秒以内にこのサービスでエラーになった信頼できるメッセージ セッションの数。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

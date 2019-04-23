---
title: 1 秒あたりの失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178621"
---
# <a name="calls-failed-per-second"></a>1 秒あたりの失敗した呼び出し
カウンター名:1 秒あたりの失敗した呼び出し  
  
## <a name="description"></a>説明  
 1 秒間にこの操作で未処理の例外が発生した呼び出しの回数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 このカウンターは、この操作で未処理の例外が発生するたびにインクリメントされます。  
  
## <a name="see-also"></a>関連項目

- [コントラクトおよびサービスのエラーの指定と処理](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

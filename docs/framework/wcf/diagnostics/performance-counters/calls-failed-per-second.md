---
title: 1 秒あたりの失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321119"
---
# <a name="calls-failed-per-second"></a>1 秒あたりの失敗した呼び出し
カウンター名 : 1 秒あたりの失敗した呼び出し  
  
## <a name="description"></a>説明  
 1 秒間にこの操作で未処理の例外が発生した呼び出しの回数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 このカウンターは、この操作でハンドルされない例外が発生するたびにインクリメントされます。  
  
## <a name="see-also"></a>関連項目

- [コントラクトおよびサービスのエラーの指定と処理](../../specifying-and-handling-faults-in-contracts-and-services.md)

---
title: サービス:1 秒あたりの失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: d87d5f06d0c9a3849ec80a3d1c7badefde7cf372
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167493"
---
# <a name="service-calls-failed-per-second"></a>サービス:1 秒あたりの失敗した呼び出し
カウンター名:1 秒あたりの呼び出しに失敗しました。  
  
## <a name="description"></a>説明  
 このサービスが 1 秒間に受信した未処理の例外を含む呼び出しの回数。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 マネージド コードでは、エラー条件が発生すると例外がスローされます。  
  
 マネージド コードでは、エラー条件が発生すると例外がスローされます。  
  
 このカウンターは、このサービスで未処理の例外が発生するたびにインクリメントされます。  
  
## <a name="see-also"></a>関連項目

- [コントラクトおよびサービスのエラーの指定と処理](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

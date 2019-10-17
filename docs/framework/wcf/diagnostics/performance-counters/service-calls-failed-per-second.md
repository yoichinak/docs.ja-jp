---
title: 'サービス : 1 秒あたりの失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5431144a4618b146a10dfaa3bbdaae34c519319e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315791"
---
# <a name="service-calls-failed-per-second"></a>サービス : 1 秒あたりの失敗した呼び出し
カウンター名 : 1 秒あたりの失敗した呼び出し。  
  
## <a name="description"></a>説明  
 このサービスが 1 秒間に受信した未処理の例外を含む呼び出しの回数。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 マネージド コードでは、エラー条件が発生すると例外がスローされます。  
  
 マネージド コードでは、エラー条件が発生すると例外がスローされます。  
  
 このカウンターは、このサービスで未処理の例外が発生するたびにインクリメントされます。  
  
## <a name="see-also"></a>関連項目

- [コントラクトおよびサービスのエラーの指定と処理](../../specifying-and-handling-faults-in-contracts-and-services.md)

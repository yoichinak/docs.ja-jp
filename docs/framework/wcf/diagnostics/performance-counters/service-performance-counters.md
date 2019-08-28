---
title: サービス パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 18a9e6336b70341f5da9c7b73cbd3f9bd3f958c7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044275"
---
# <a name="service-performance-counters"></a>サービス パフォーマンス カウンター
サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。 パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
> パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。  
  
## <a name="see-also"></a>関連項目

- [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)

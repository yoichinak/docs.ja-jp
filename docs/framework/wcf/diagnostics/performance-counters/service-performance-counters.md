---
title: サービス パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 929ddcb2f271b7488270ea39e7a3a0037158c855
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320028"
---
# <a name="service-performance-counters"></a>サービス パフォーマンス カウンター
サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。 パフォーマンス モニター (Perfmon.exe) を使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。  
  
## <a name="see-also"></a>関連項目

- [Performance Counters](index.md)

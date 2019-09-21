---
title: 操作パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 31b0f92ae3477bd3c1de8c348a60e5c64d7c53cc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855680"
---
# <a name="operation-performance-counters"></a>操作パフォーマンス カウンター
操作パフォーマンス カウンターは、パフォーマンス モニター (Perfmon.exe) を使用して表示した場合、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。 それぞれの操作に個別のインスタンスがあります。 つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。 オブジェクトのインスタンスには次のパターンの名前が付いています。  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。  
  
> [!CAUTION]
> パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。  
  
## <a name="see-also"></a>関連項目

- [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)

---
title: エンドポイントのパフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 2352bc82998c8e87e72f331104446bac4fcb9fda
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040577"
---
# <a name="endpoint-performance-counters"></a>エンドポイントのパフォーマンス カウンター
エンドポイントのパフォーマンス カウンターは、エンドポイントがどのようにメッセージを受信しているかを示すデータをキャプチャします。 パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスの名前には次のパターンが使用されます。  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 このデータは、個々の操作で収集されるデータに似ていますが、そのエンドポイントだけで集約されたデータです。  
  
> [!CAUTION]
> パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。  
  
## <a name="see-also"></a>関連項目

- [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)

---
title: <filters> の <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: ba60958ad33b46b40285f3f70001273bb3af3a63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925611"
---
# <a name="filters-of-routing"></a>\<ルーティング > の\<> をフィルター処理します

受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter>の種類を決定する一連のルーティングフィルターを定義するための構成セクションを表します。

[ **\<system.serviceModel>** ](system-servicemodel.md)   
&nbsp;&nbsp;[ **\<ルーティング >** ](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<フィルター >**
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし

### <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [ **\<フィルター >** ](filter.md) | 受信メッセージを評価するときに使用される Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) の種類を決定するルーティングフィルターを格納します。 |

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<ルーティング >** ](routing.md) | 一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージ<xref:System.ServiceModel.Dispatcher.MessageFilter>を評価するときに使用する Windows Communication Foundation (WCF) の種類、およびターゲットエンドポイントを定義するルーティングテーブルを決定します。フィルターが一致したときにメッセージをに送信します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

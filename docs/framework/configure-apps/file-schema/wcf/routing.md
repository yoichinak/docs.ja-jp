---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934124"
---
# <a name="routing"></a>\<ルーティング >

一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージ<xref:System.ServiceModel.Dispatcher.MessageFilter>を評価するときに使用する Windows Communication Foundation (WCF) の種類、およびターゲットエンドポイントを定義するルーティングテーブルを決定します。フィルターが一致したときにメッセージをに送信します。

[ **\<system.serviceModel>** ](system-servicemodel.md)   
&nbsp;&nbsp; **\<ルーティング >**
  
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
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
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
| [ **\<フィルター >** ](filters-of-routing.md) | 受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) MessageFilter の種類を決定するルーティングフィルターのセットを格納します。 |
| [ **\<filterTables >** ](filtertables.md) | ルーティング フィルターとターゲット エンドポイントとのマッピングを格納します。フィルターが一致したときにエンドポイントを指定するために使用されます。 |

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| **\<system.ServiceModel>** | すべての WCF 構成要素のルート要素です。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

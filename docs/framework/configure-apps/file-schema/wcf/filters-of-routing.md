---
title: <filters> の <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 8b2c735a19c4cece16dcb77e3ec548eb2d39ec18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701035"
---
# <a name="filters-of-routing"></a>\<フィルター > の\<ルーティング >

Windows Communication Foundation (WCF) の種類を指定するルーティング フィルター セットを定義する構成セクションを表します。<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージを評価するときに使用されます。

[**\<system.serviceModel>**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<ルーティング >**](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**
  
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
| [**\<フィルター >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Windows Communication Foundation (WCF) の種類を決定するルーティング フィルターを含む<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価時に使用されます。 |

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<ルーティング >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Windows Communication Foundation (WCF) の種類を指定するルーティング フィルター セットを定義する構成セクションを表します<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価とルーティング テーブルをするターゲット エンドポイントを定義するときに使用される。フィルターが一致したときにメッセージを送信します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

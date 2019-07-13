---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704038"
---
# <a name="filter"></a>\<フィルター >

Windows Communication Foundation (WCF) の型を決定するルーティング フィルターを定義します。<xref:System.ServiceModel.Dispatcher.MessageFilter>も任意のサポート データまたはフィルターに必要なパラメーターとして、受信メッセージを評価するときに使用します。

\<system.serviceModel> \<routing> \<filters> \<filter>
  
## <a name="syntax"></a>構文  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

| 属性  | 説明 |
| ---------- | ----------- |
| customType | フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。 場合`filterType`に設定されている`custom`、この属性には作成するクラスの完全修飾型名が含まれています。  `filterData` カスタム型フィルターの評価時に使用する値を含めることもできます。 |
| filterData | フィルター データを示す文字列。 この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| filterType | フィルターの種類を示す文字列。 この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。  `filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| name       | フィルター要素の一意の名前を示す文字列。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| ------- | ----------- |
| [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Windows Communication Foundation (WCF) の種類を指定するルーティング フィルター セットを定義する構成セクション<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージを評価するときに使用されます。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855251"
---
# <a name="filter"></a>\<フィルター >

受信メッセージを評価するときに使用する Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter>の種類、およびフィルターに必要なサポートデータまたはパラメーターを決定するルーティングフィルターを定義します。

[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<ルーティング >** ](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<フィルター >** ](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<フィルター >**  
  
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
| customType | フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。 が`filterType` に`custom`設定されている場合、この属性には作成するクラスの完全修飾型名が含まれます。  `filterData`には、カスタム型フィルターの評価時に使用される値を含めることもできます。 |
| filterData | フィルター データを示す文字列。 この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| filterType | フィルターの種類を示す文字列。 この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。  `filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| name       | フィルター要素の一意の名前を示す文字列。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| ------- | ----------- |
| [\<ルーティング >](routing.md) | 一連のルーティングフィルターを定義するための構成セクション。受信メッセージを評価するときに使用<xref:System.ServiceModel.Dispatcher.MessageFilter>する Windows Communication Foundation (WCF) の種類を決定します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

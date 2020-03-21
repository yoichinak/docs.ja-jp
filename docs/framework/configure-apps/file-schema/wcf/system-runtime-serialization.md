---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152971"
---
# <a name="systemruntimeserialization"></a>\<シリアル化>
<xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;**\<シリアル化>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<データコントラクトシリアライザー>](datacontractserializer-of-system-runtime-serialization.md)|逆シリアル化時に使用される既知の型の追加を可能にします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<要素>構成](../configuration-element.md)|構成の最上位の要素。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization>
- [データ コントラクトの使用](../../../wcf/feature-details/using-data-contracts.md)
- [既知のデータ コントラクト型](../../../wcf/feature-details/data-contract-known-types.md)

---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 8b14dc1908ef3a06549154f70efb2d4e5cb10076
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289434"
---
# <a name="parameter"></a>\<パラメーター >
宣言された型がジェネリック型である場合、ジェネリック パラメーターを指定します。  
  
 \<system.runtime.serialization>  
\<dataContractSerializer >  
\<declaredTypes > 要素  
\<追加 > 要素の\<declaredTypes >  
\<knownType > 要素  
\<パラメーター > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|インデックス|宣言された型がジェネリック型である場合、既知の型を返すジェネリック パラメーターを指定します。|  
|型|シリアル化と逆シリアル化で使用される既知の型を説明する文字列。|  
  
## <a name="index-attribute"></a>index 属性  
  
|値|説明|  
|-----------|-----------------|  
|"0"|ジェネリック型の最初のパラメーター。 たとえば、<xref:System.Collections.Generic.List%601> にはパラメーターが 1 つだけあります。 宣言型として使用される場合、index は "0" に設定されます。|  
|"1"|ジェネリック型の 2 番目のパラメーター。 たとえば、<xref:System.Collections.Generic.Dictionary%602> には 2 つのパラメーターがあります。 2 番目のパラメーターによって既知の型が返される場合は、index 属性を "1" に設定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<knownType>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|宣言型のフィールドまたはプロパティによって返される既知の型を指定します。|  
  
## <a name="remarks"></a>Remarks  
 既知の型の詳細については、[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>を参照してください。  
  
 参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。  
  
 この構成要素に、両方の属性を同時に設定することはできません。 両方の属性が設定された場合、<xref:System.Configuration.ConfigurationErrorsException> が発生します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)

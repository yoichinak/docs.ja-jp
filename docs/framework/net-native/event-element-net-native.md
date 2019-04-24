---
title: <Event> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e8ddf9ea72db63c72bfb5393709b4c20de2a14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163001"
---
# <a name="event-element-net-native"></a>\<イベント > 要素 (.NET ネイティブ)
イベントにランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 イベントの名前を指定します。|  
|`Browse`|リフレクション|省略可能な属性です。 イベントに関する情報の照会やイベントの列挙を制御しますが、実行時の動的アクセスは有効にしません。|  
|`Dynamic`|リフレクション|省略可能な属性です。 イベントへの実行時アクセスを制御して、動的プログラミングを有効にします。 このポリシーにより、実行時にイベントを動的に処理できるようになります。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*method_name*|イベントの名前です。 イベントの型は親 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) または [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素により定義されます。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*policy_setting*|イベントのこのポリシーの種類に適用する設定です。 指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。 詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>Remarks  
 イベントのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)
- [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

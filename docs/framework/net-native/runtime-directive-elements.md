---
title: ランタイム ディレクティブ要素
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf692ff93a575858d1d1a89346611cb9c5957b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137814"
---
# <a name="runtime-directive-elements"></a>ランタイム ディレクティブ要素
ランタイム ディレクティブ (rd.xml) ファイル形式は、次のランタイム ディレクティブ要素をサポートします。 階層表現については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。  
  
 [\<アプリケーション >](../../../docs/framework/net-native/application-element-net-native.md)  
 アプリで使用されるすべての型にランタイム リフレクション ポリシーを適用し、実行時にリフレクションに使用できるメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。 これは、[\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 要素の子です。  
  
 [\<アセンブリ >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 アセンブリ内のすべての型に実行時ポリシーを適用します。 これは、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素の子です。  
  
 [\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 それを含んでいる [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ディレクティブが属性の場合、その属性が適用されるコード要素に実行時ポリシーを適用します。  
  
 [\<ディレクティブ >](../../../docs/framework/net-native/directives-element-net-native.md)  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。 その子要素は、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) です。  
  
 [\<イベント >](../../../docs/framework/net-native/event-element-net-native.md)  
 イベントに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<フィールド >](../../../docs/framework/net-native/field-element-net-native.md)  
 フィールドに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 ジェネリック型またはメソッドのパラメーター型に実行時ポリシーを適用します。  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 型に実行時ポリシーを適用します (それを含んでいる型またはメソッドにそのポリシーが適用されている場合)。  
  
 [\<ライブラリ >](../../../docs/framework/net-native/library-element-net-native.md)  
 アセンブリ内のすべての型に実行時ポリシーを適用します。 これは、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素の子です。  
  
 [\<メソッド >](../../../docs/framework/net-native/method-element-net-native.md)  
 メソッドに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 構築されたジェネリック メソッドに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)  
 名前空間内のすべての型に実行時ポリシーを適用します。  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 メソッドに渡された引数の型に実行時ポリシーを適用します。  
  
 [\<プロパティ >](../../../docs/framework/net-native/property-element-net-native.md)  
 プロパティに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。  
  
 [\<型 >](../../../docs/framework/net-native/type-element-net-native.md)  
 型に実行時ポリシーを適用します。  
  
 [\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 構築されたジェネリック型に実行時ポリシーを適用します。  
  
 [\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 メソッドに渡された <xref:System.Type> 引数によって表される型に実行時ポリシーを適用します。  
  
## <a name="see-also"></a>関連項目

- [rd.xml Configuration File Reference (rd.xml 構成ファイル リファレンス)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

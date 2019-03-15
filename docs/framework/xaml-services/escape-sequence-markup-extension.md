---
title: '{} エスケープ シーケンスのマークアップ拡張機能'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: eaee0a1f92d8b7cb3810651eda21f1cc800ebf57
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58018556"
---
# <a name="-escape-sequence--markup-extension"></a>{} エスケープ シーケンス/マークアップ拡張機能
属性値を XAML のエスケープ シーケンスを提供します。 エスケープ シーケンスは、リテラルとして解釈される属性で、後続の値を許可します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML プロパティ要素の使用  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*literalValue*|エスケープ シーケンスに続くリテラル文字列。 通常この文字列が、開くまたは閉じる中かっこ ({または})。|  
  
## <a name="remarks"></a>Remarks  
 エスケープ シーケンス ({}) かっこ ({}) は、XAML 内のリテラル文字として使用できるように使用されます。  
  
 XAML リーダーは通常、マークアップ拡張機能のエントリ ポイントを示すために、始めかっこ ({}) を使用して、右中かっこ (}) があるかどうかを判断するには、次の文字をチェックするただし。 のみときに、2 つの中かっこ ({}) は、エスケープ シーケンスと見なされるを隣接します。  
  
 エスケープ シーケンスが発生した場合、XAML リーダーは、文字列として、文字列の残りの部分を処理する必要があります。 ただし、エスケープ シーケンスは、型コンバーターを持つメンバーに適用する場合、これが XAML ライターによって解釈されるとき、文字列は型変換される可能性もあります。  
  
 エスケープ シーケンスでは、マークアップ拡張機能ではなく、クラスではサポートされません。 ただし、これは、XAML リーダーの (カスタム XAML リーダーを含む) を使用する必要があります規則です。  
  
 引用符 (") は、この方法でエスケープ シーケンスとして使用できません。 非コンテンツ プロパティのプロパティの値として、引用符を設定する必要がある場合は、プロパティ要素構文を使用またはプロパティ要素内の文字列として引用符を配置し XML 文字エンティティを使用します。 コンテンツ プロパティの場合、引用符は全体のコンテンツを指定できます。  
  
 エスケープ シーケンス ({}) は、XAML マークアップ拡張機能が表示される場所の場所に名前空間の修飾子を含める必要のある XML 型を指定するときに頻繁に必要です。 これには、等号 (=) の直後に、マークアップ拡張機能で、XAML 属性の値の開始が含まれます。 次の例では、XAML 属性値の先頭に表示される XML 名前空間のエスケープ シーケンスを示します。  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>関連項目
- [XAML の型コンバーターおよびマークアップ拡張機能](type-converters-and-markup-extensions-for-xaml.md)
- [XML 文字エンティティと XAML](xml-character-entities-and-xaml.md)

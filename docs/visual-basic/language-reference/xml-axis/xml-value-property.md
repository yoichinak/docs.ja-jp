---
title: XML Value プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 1c7aa1cc32bc1c5ef637f7a606db7e695f1dfaee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821952"
---
# <a name="xml-value-property-visual-basic"></a>XML Value プロパティ (Visual Basic)
コレクションの最初の要素の値にアクセスできるように<xref:System.Xml.Linq.XElement>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
object.Value  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須。 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。|  
  
## <a name="return-value"></a>戻り値  
 A `String` 、コレクションの最初の要素の値を格納しているまたは`Nothing`コレクションが空の場合。  
  
## <a name="remarks"></a>Remarks  
 <xref:System.Xml.Linq.XElement.Value%2A>プロパティでは、コレクションの最初の要素の値にアクセスしやすい<xref:System.Xml.Linq.XElement>オブジェクト。 このプロパティは、少なくとも 1 つのオブジェクトがコレクションに含まれるかどうかをまず確認します。 このプロパティを返しますのかどうか、コレクションが空、`Nothing`します。 このプロパティがの値を返しますそれ以外の場合、<xref:System.Xml.Linq.XElement.Value%2A>コレクションの最初の要素のプロパティ。  
  
> [!NOTE]
>  使用して XML 属性の値にアクセスするときに、'\@' 識別子、属性の値として返されます、`String`を明示的に指定する必要はありませんし、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティ。  
  
 コレクション内の他の要素にアクセスするには、XML 拡張機能インデクサー プロパティを使用できます。 詳細については、次を参照してください。[拡張インデクサー プロパティ](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)します。  
  
## <a name="inheritance"></a>継承  
 ほとんどのユーザーが実装する必要はありません<xref:System.Collections.Generic.IEnumerable%601>、し、このため、このセクションを無視できます。  
  
 <xref:System.Xml.Linq.XElement.Value%2A>プロパティを実装する型の拡張機能プロパティは、`IEnumerable(Of XElement)`します。 この拡張機能プロパティのバインドは、バインディングの拡張メソッドに似ています。 そのプロパティに、拡張機能プロパティに優先が型は、インターフェイスの 1 つを実装し、"Value"の名前を持つプロパティを定義、場合。 つまり、この<xref:System.Xml.Linq.XElement.Value%2A>プロパティを実装するクラスの新しいプロパティを定義することでオーバーライドする`IEnumerable(Of XElement)`します。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、<xref:System.Xml.Linq.XElement.Value%2A>プロパティのコレクションの最初のノードへのアクセスを<xref:System.Xml.Linq.XElement>オブジェクト。 例では、という名前のすべての子ノードのコレクションを取得する子軸プロパティを使用して`phone`内にある、`contact`オブジェクト。  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>例  
 次の例は、のコレクションから XML 属性の値を取得する方法を示しています。<xref:System.Xml.Linq.XAttribute>オブジェクト。 例では、値を表示する属性軸プロパティを使用して、`type`のすべての属性、`phone`要素。  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [拡張インデクサー プロパティ](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [XML 子軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 属性軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)

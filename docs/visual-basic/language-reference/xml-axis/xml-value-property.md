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
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942988"
---
# <a name="xml-value-property-visual-basic"></a>XML Value プロパティ (Visual Basic)
オブジェクトの<xref:System.Xml.Linq.XElement>コレクションの最初の要素の値へのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
object.Value  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須。 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。|  
  
## <a name="return-value"></a>戻り値  
 コレクションの最初の要素の値を格納している。コレクションが空の場合は`Nothing`。 `String`  
  
## <a name="remarks"></a>Remarks  
 プロパティ<xref:System.Xml.Linq.XElement.Value%2A>を使用すると、オブジェクトの<xref:System.Xml.Linq.XElement>コレクション内の最初の要素の値に簡単にアクセスできます。 このプロパティは、まず、コレクションに少なくとも1つのオブジェクトが含まれているかどうかを確認します。 コレクションが空の場合、このプロパティは`Nothing`を返します。 それ以外の場合、このプロパティは、 <xref:System.Xml.Linq.XElement.Value%2A>コレクション内の最初の要素のプロパティの値を返します。  
  
> [!NOTE]
> '\@' 識別子を使用して XML 属性の値にアクセスすると、属性値がと`String`して返され、 <xref:System.Xml.Linq.XAttribute.Value%2A>プロパティを明示的に指定する必要はありません。  
  
 コレクション内の他の要素にアクセスするには、XML 拡張インデクサープロパティを使用できます。 詳細については、「[拡張インデクサープロパティ](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)」を参照してください。  
  
## <a name="inheritance"></a>継承  
 ほとんどのユーザーはを実装<xref:System.Collections.Generic.IEnumerable%601>する必要がなく、このセクションを無視してかまいません。  
  
 プロパティ<xref:System.Xml.Linq.XElement.Value%2A>は、を実装`IEnumerable(Of XElement)`する型の拡張プロパティです。 この拡張プロパティのバインディングは、拡張メソッドのバインディングに似ています。型がインターフェイスの1つを実装し、"Value" という名前のプロパティを定義する場合、そのプロパティは拡張プロパティよりも優先されます。 言い換えると、この<xref:System.Xml.Linq.XElement.Value%2A>プロパティをオーバーライドするには、を実装`IEnumerable(Of XElement)`するクラスで新しいプロパティを定義します。  
  
## <a name="example"></a>例  
 次の例は、 <xref:System.Xml.Linq.XElement.Value%2A>プロパティを使用して、オブジェクトの<xref:System.Xml.Linq.XElement>コレクション内の最初のノードにアクセスする方法を示しています。 この例では、子軸プロパティを使用して、 `phone` `contact`オブジェクト内にあるという名前のすべての子ノードのコレクションを取得します。  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>例  
 次の例は、オブジェクトの<xref:System.Xml.Linq.XAttribute>コレクションから XML 属性の値を取得する方法を示しています。 この例では、属性軸プロパティを使用して、 `type` `phone`すべての要素の属性の値を表示します。  
  
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

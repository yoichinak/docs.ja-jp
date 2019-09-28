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
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592014"
---
# <a name="xml-value-property-visual-basic"></a>XML Value プロパティ (Visual Basic)

@No__t-0 オブジェクトのコレクションの最初の要素の値へのアクセスを提供します。

## <a name="syntax"></a>構文

```vb
object.Value
```

## <a name="parts"></a>指定項目

|項目|定義|  
|---|---|  
|`object`|必須。 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。|  

## <a name="return-value"></a>戻り値

 コレクションの最初の要素の値を格納している `String`。コレクションが空の場合は `Nothing`。

## <a name="remarks"></a>コメント

 @No__t-0 プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション内の最初の要素の値に簡単にアクセスできます。 このプロパティは、まず、コレクションに少なくとも1つのオブジェクトが含まれているかどうかを確認します。 コレクションが空の場合、このプロパティは `Nothing` を返します。 それ以外の場合、このプロパティは、コレクション内の最初の要素の <xref:System.Xml.Linq.XElement.Value%2A> プロパティの値を返します。

> [!NOTE]
> ' @No__t-0 ' 識別子を使用して XML 属性の値にアクセスすると、属性値は `String` として返されるため、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを明示的に指定する必要はありません。

 コレクション内の他の要素にアクセスするには、XML 拡張インデクサープロパティを使用できます。 詳細については、「[拡張インデクサープロパティ](extension-indexer-property.md)」を参照してください。

## <a name="inheritance"></a>継承

 ほとんどのユーザーは <xref:System.Collections.Generic.IEnumerable%601> を実装する必要がないため、このセクションを無視できます。

 @No__t-0 プロパティは、`IEnumerable(Of XElement)` を実装する型の拡張プロパティです。 この拡張プロパティのバインディングは、拡張メソッドのバインディングに似ています。型がインターフェイスの1つを実装し、"Value" という名前のプロパティを定義する場合、そのプロパティは拡張プロパティよりも優先されます。 つまり、`IEnumerable(Of XElement)` を実装するクラスで新しいプロパティを定義することで、この <xref:System.Xml.Linq.XElement.Value%2A> プロパティをオーバーライドできます。

## <a name="example"></a>例

 次の例は、<xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用して、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション内の最初のノードにアクセスする方法を示しています。 この例では、子軸プロパティを使用して、`contact` オブジェクト内にある @no__t 0 という名前のすべての子ノードのコレクションを取得します。

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 このコードを実行すると、次のテキストが表示されます。

 `Phone number: 206-555-0144`

## <a name="example"></a>例

 次の例は、@no__t 0 のオブジェクトのコレクションから XML 属性の値を取得する方法を示しています。 この例では、属性軸プロパティを使用して、すべての `phone` 要素の `type` 属性の値を表示します。

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 このコードを実行すると、次のテキストが表示されます。

 ```console
 home
 work
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [XML 軸プロパティ](index.md)
- [XML リテラル](../xml-literals/index.md)
- [Visual Basic での XML の作成](../../programming-guide/language-features/xml/creating-xml.md)
- [拡張メソッド](../../programming-guide/language-features/procedures/extension-methods.md)
- [拡張インデクサー プロパティ](extension-indexer-property.md)
- [XML 子軸プロパティ](xml-child-axis-property.md)
- [XML 属性軸プロパティ](xml-attribute-axis-property.md)

---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: b2bf524214fa8ecca215d50c198b23d127e3b400
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349446"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子孫軸プロパティ (Visual Basic)

Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.

## <a name="syntax"></a>構文

```vb
object...<descendant>
```

## <a name="parts"></a>指定項目

`object` 必須。 <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。

`...<` 必須。 Denotes the start of a descendant axis property.

`descendant` 必須。 Name of the descendant nodes to access, of the form [`prefix:]name`.

|パーツ|説明|
|----------|-----------------|
|`prefix`|省略可能です。 XML namespace prefix for the descendant node. Must be a global XML namespace that is defined by using an `Imports` statement.|
|`name`|必須です。 Local name of the descendant node. See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` 必須。 Denotes the end of a descendant axis property.

## <a name="return-value"></a>戻り値

<xref:System.Xml.Linq.XElement> オブジェクトのコレクション。

## <a name="remarks"></a>Remarks

You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects. Use the XML `Value` property to access the value of the first descendant node in the returned collection. For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.

## <a name="xml-namespaces"></a>XML 名前空間

The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement. It cannot use XML namespaces declared locally within XML element literals. For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>例

The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

このコードを実行すると、次のテキストが表示されます。

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>例

次の例では、`ns` を名前空間プレフィックスとして宣言します。 It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

このコードを実行すると、次のテキストが表示されます。

`Name: Patrick Hines`

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)

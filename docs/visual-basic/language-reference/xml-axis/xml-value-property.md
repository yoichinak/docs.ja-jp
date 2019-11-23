---
title: XML Value プロパティ
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 571d9130ef69df580bbba5d90bc8758b4b627196
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349418"
---
# <a name="xml-value-property-visual-basic"></a>XML Value プロパティ (Visual Basic)

Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.

## <a name="syntax"></a>構文

```vb
object.Value
```

## <a name="parts"></a>指定項目

|用語|定義|  
|---|---|  
|`object`|必須です。 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。|  

## <a name="return-value"></a>戻り値

 A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.

## <a name="remarks"></a>Remarks

 The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects. This property first checks whether the collection contains at least one object. If the collection is empty, this property returns `Nothing`. Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.

> [!NOTE]
> When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.

 To access other elements in a collection, you can use the XML extension indexer property. For more information, see [Extension Indexer Property](extension-indexer-property.md).

## <a name="inheritance"></a>継承

 Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.

 The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`. The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property. In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.

## <a name="example"></a>例

 The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects. The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 このコードを実行すると、次のテキストが表示されます。

 `Phone number: 206-555-0144`

## <a name="example"></a>例

 The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects. The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.

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

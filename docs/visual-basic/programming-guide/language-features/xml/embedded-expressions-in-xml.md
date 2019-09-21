---
title: XML での埋め込み式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 525fa04db86a299d88e1612aac76d014f35124eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922628"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML での埋め込み式 (Visual Basic)
埋め込み式を使用すると、実行時に評価される式を含む XML リテラルを作成できます。 埋め込み式の構文はです`<%=` `expression` `%>`。これは、ASP.NET で使用される構文と同じです。  
  
 たとえば、XML 要素リテラルを作成し、リテラルテキストコンテンツと共に埋め込み式を組み合わせることができます。  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 に`isbnNumber`整数12345が`book`含まれていて、日付3/5/2006 が含まれている場合、このコードを実行すると、の値はになります。`modifiedDate`  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>埋め込み式の位置と検証  
 埋め込み式は、XML リテラル式内の特定の場所でのみ使用できます。 式の場所は、式が返すことができる型`Nothing`と処理方法を制御します。 次の表では、埋め込み式の許可される場所と型について説明します。  
  
|リテラル内の場所|式の種類|処理`Nothing`|  
|---|---|---|  
|XML 要素名|<xref:System.Xml.Linq.XName>|Error|  
|XML 要素のコンテンツ|`Object`またはの配列`Object`|無視|  
|XML 要素の属性名|<xref:System.Xml.Linq.XName>|属性値もでない限り、エラーが発生します。`Nothing`|  
|XML 要素の属性値|`Object`|属性宣言が無視されました|  
|XML 要素属性|<xref:System.Xml.Linq.XAttribute>またはのコレクション<xref:System.Xml.Linq.XAttribute>|無視|  
|XML ドキュメントのルート要素|<xref:System.Xml.Linq.XElement>または、1つ<xref:System.Xml.Linq.XElement>のオブジェクトと任意の数<xref:System.Xml.Linq.XProcessingInstruction>の<xref:System.Xml.Linq.XComment>オブジェクトおよびオブジェクトのコレクション|無視|  
  
- XML 要素名の埋め込み式の例を次に示します。  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- XML 要素のコンテンツ内の埋め込み式の例を次に示します。  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- XML 要素の属性名に含まれる埋め込み式の例を次に示します。  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- XML 要素の属性値に含まれる埋め込み式の例を次に示します。  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- XML 要素属性の埋め込み式の例を次に示します。  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- XML ドキュメントのルート要素内の埋め込み式の例を次に示します。  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 を有効`Option Strict`にした場合、コンパイラは、埋め込み式の型が必要な型に拡大変換されるかどうかをチェックします。 唯一の例外は、コードの実行時に検証される XML ドキュメントのルート要素です。 を指定せず`Option Strict`にコンパイルする場合は、型`Object`の式を埋め込むことができ、その型は実行時に検証されます。  
  
 コンテンツが省略可能な場所では、を含む`Nothing`埋め込み式は無視されます。 これは、XML リテラルを使用する`Nothing`前に、要素の内容、属性値、および配列要素を確認する必要がないことを意味します。 要素名や属性名など、必須の値をに`Nothing`することはできません。  
  
 特定の型のリテラルで埋め込み式を使用する方法の詳細については、「 [Xml ドキュメントリテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)、 [xml 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)」を参照してください。  
  
## <a name="scoping-rules"></a>スコープの規則  
 コンパイラは、各 XML リテラルを適切なリテラル型のコンストラクター呼び出しに変換します。 XML リテラル内のリテラルコンテンツと埋め込み式は、引数としてコンストラクターに渡されます。 これは、XML リテラルで使用できるすべての Visual Basic プログラミング要素も、その埋め込み式で使用できることを意味します。  
  
 Xml リテラル内では、 `Imports`ステートメントで宣言された xml 名前空間プレフィックスにアクセスできます。 `xmlns`属性を使用して、新しい xml 名前空間プレフィックスを宣言したり、既存の xml 名前空間プレフィックスを要素内にシャドウしたりすることができます。 新しい名前空間は、その要素の子ノードでは使用できますが、埋め込み式の XML リテラルには使用できません。  
  
> [!NOTE]
> `xmlns`名前空間属性を使用して XML 名前空間プレフィックスを宣言する場合、属性値は定数文字列である必要があります。 この`xmlns`点で、属性は、 `Imports`ステートメントを使用して XML 名前空間を宣言するのと似ています。 埋め込み式を使用して XML 名前空間の値を指定することはできません。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)

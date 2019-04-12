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
ms.openlocfilehash: 4c96665994a7e56bc70f72b66d5922f5a6472a13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827576"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML での埋め込み式 (Visual Basic)
埋め込み式を使用すると、実行時に評価される式が含まれる XML リテラルを作成できます。 埋め込み式の構文は、 `<%=` `expression` `%>`で使用するための構文は同じ[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]します。  
  
 などを作成する XML 要素リテラルには、埋め込み式のリテラル テキストの内容とを組み合わせることです。  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 場合`isbnNumber`12345 整数が含まれると`modifiedDate`、日付が含まれる 3/5/2006、このコードが実行される場合、値の`book`は。  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>埋め込み式の位置と検証  
 埋め込み式は、XML リテラル式の中で特定の場所でのみ記述できます。 式の型が式の場所のコントロールを返すことができ、どのように`Nothing`処理されます。 次の表では、許可されている場所と埋め込み式の型について説明します。  
  
|リテラル内の場所|式の型|処理 `Nothing`|  
|---|---|---|  
|XML 要素名|<xref:System.Xml.Linq.XName>|Error|  
|XML 要素のコンテンツ|`Object` またはの配列 `Object`|無視|  
|XML 要素の属性名|<xref:System.Xml.Linq.XName>|エラー、属性の値もしない限り、 `Nothing`|  
|XML 要素の属性値|`Object`|属性宣言を無視します|  
|XML 要素の属性|<xref:System.Xml.Linq.XAttribute> またはのコレクション <xref:System.Xml.Linq.XAttribute>|無視|  
|XML ドキュメントのルート要素|<xref:System.Xml.Linq.XElement> いずれかのコレクションまたは<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト|無視|  
  
-   XML 要素名での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
-   XML 要素のコンテンツの埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
-   XML 要素の属性名での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
-   XML 要素の属性値内の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
-   XML 要素の属性での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
-   XML ドキュメントのルート要素の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 有効にした場合`Option Strict`コンパイラは各埋め込み式の型が必要な型に拡大変換を確認します。 唯一の例外は、コードの実行時に検証される XML ドキュメントのルート要素です。 せずにコンパイルする場合`Option Strict`、型の式を埋め込むことができます`Object`し、型が実行時に検証されます。  
  
 コンテンツが、省略可能な場所で埋め込み式が含まれている`Nothing`は無視されます。 これは、その要素のコンテンツの属性の値を確認する必要はありませんし、配列の要素がないことを意味`Nothing`XML リテラルを使用する前にします。 要素および属性の名前などの値にすることはできません必要な`Nothing`します。  
  
 特定の種類のリテラルでの埋め込み式の使用に関する詳細については、[XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)、 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)を参照してください。  
  
## <a name="scoping-rules"></a>スコープの規則  
 コンパイラは、各 XML リテラルを適切なリテラルの型のコンス トラクターの呼び出しに変換します。 リテラルの内容と、XML リテラルでの埋め込み式は、コンス トラクターに引数として渡されます。 つまり、すべて Visual Basic プログラミング要素、XML リテラルに使用できますが、埋め込み式を使用できるもこと。  
  
 XML リテラル内でプレフィックスが宣言されている XML 名前空間をアクセスすることができます、`Imports`ステートメント。 新しい XML 名前空間プレフィックスを宣言したり、シャドウする要素を使用して、既存 XML 名前空間プレフィックス、`xmlns`属性。 新しい名前空間は埋め込み式の XML リテラルではなく、その要素の子ノードに使用できます。  
  
> [!NOTE]
>  使用して XML 名前空間プレフィックスを宣言する場合、`xmlns`名前空間の属性、属性値に定数文字列を指定する必要があります。 この点を使用して、`xmlns`属性は使用と同様、 `Imports` XML 名前空間を宣言するステートメント。 埋め込み式を使用して、XML 名前空間の値を指定することはできません。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML リテラルの概要 (Visual Basic)](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)

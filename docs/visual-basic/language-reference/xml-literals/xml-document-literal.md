---
title: XML ドキュメント リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814628"
---
# <a name="xml-document-literal-visual-basic"></a>XML ドキュメント リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XDocument>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`encoding`|省略可能です。 リテラル テキストをどのエンコード ドキュメントの宣言を使用します。|  
|`standalone`|省略可能です。 リテラル テキスト。 "Yes"にする必要がありますまたは"no"です。|  
|`piCommentList`|省略可能です。 XML 処理命令と XML コメントの一覧です。 次の形式を取ります。<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 各`piComment`次のいずれかを指定できます。<br /><br /> -   [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)します。<br />-   [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)します。|  
|`rootElement`|必須。 ドキュメントのルート要素です。 形式は、次のいずれかです。<br /><br /> <ul><li>[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。</li><li>形式の式を埋め込む`<%=` `elementExp` `%>`します。 `elementExp`次のいずれかを返します。<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> オブジェクト。</li><li>1 つを含むコレクション<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト。</li></ul></li></ul><br /> 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XDocument> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML ドキュメント リテラルは、リテラルの先頭に XML 宣言で識別されます。 各 XML ドキュメント リテラルには、XML のルート要素の 1 つだけ必要がありますが、任意の数 XML 処理命令と XML コメントのことができます。  
  
 XML ドキュメント リテラルは、XML 要素ではできません。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。 これにより、XML ドキュメントの内容をコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラの呼び出しにリテラルの XML ドキュメントを変換する、<xref:System.Xml.Linq.XDocument.%23ctor%2A>と<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>コンス トラクター。  
  
## <a name="example"></a>例  
 次の例では、XML 宣言、処理命令、コメント、および別の要素を格納する要素を含む XML ドキュメントを作成します。  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)

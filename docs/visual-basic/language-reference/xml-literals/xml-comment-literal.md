---
title: XML コメント リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349396"
---
# <a name="xml-comment-literal-visual-basic"></a>XML コメント リテラル (Visual Basic)
<xref:System.Xml.Linq.XComment> オブジェクトを表すリテラル。  
  
## <a name="syntax"></a>構文  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`<!--`|必須です。 XML コメントの先頭を表します。|  
|`content`|必須です。 XML コメントに表示されるテキスト。 連続する 2 つのハイフン (--) を含めたり、終了タグに隣接するハイフンを末尾に使用したりすることはできません。|  
|`-->`|必須です。 XML コメントの末尾を表します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XComment> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML コメント リテラルにはドキュメントのコンテンツではなく、ドキュメントに関する情報が含まれています。 XML コメント セクションの末尾には "-->" シーケンスが使用されます。 これは以下を意味します。  
  
- 埋め込み式の区切り記号は有効な XML コメント コンテンツであるため、XML コメント リテラルでは埋め込み式を使用できません。  
  
- `content` には値 "-->" を含めることができないため、XML コメント セクションを入れ子にすることはできません。  
  
 XML コメント リテラルは、変数に代入するか、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
> XML リテラルは、行連結文字を使用せずに、複数行にまたがることができます。 この機能を使用すると、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。  
  
 XML コメント リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XComment.%23ctor%2A> コンストラクターへの呼び出しに変換されます。  
  
## <a name="example"></a>例  
 次の例では、"This is a comment" というテキストを含む XML コメントを作成します。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XComment>
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

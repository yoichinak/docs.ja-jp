---
title: XML コメント リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965409"
---
# <a name="xml-comment-literal-visual-basic"></a>XML コメント リテラル (Visual Basic)
<xref:System.Xml.Linq.XComment>オブジェクトを表すリテラル。  
  
## <a name="syntax"></a>構文  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`<!--`|必須。 XML コメントの先頭を示します。|  
|`content`|必須。 XML コメントに表示されるテキスト。 連続する2つのハイフン (--) を含めることはできません。また、終了タグに隣接するハイフンで終わることもできません。|  
|`-->`|必須。 XML コメントの末尾を示します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XComment> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML コメントリテラルにドキュメントコンテンツが含まれていません。ドキュメントに関する情報が含まれています。 XML コメントセクションは、シーケンス "-->" で終了します。 これは、次の点を意味します。  
  
- 埋め込み式の区切り記号が有効な XML コメントの内容であるため、XML コメントリテラルで埋め込み式を使用することはできません。  
  
- XML コメントセクションを入れ子に`content`することはできません。には値 "-->" を含めることができません。  
  
 XML コメントリテラルを変数に割り当てるか、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
> XML リテラルは、行連結文字を使用せずに、複数の行にまたがることができます。 この機能を使用すると、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラは、XML コメントリテラルをコンストラクターの<xref:System.Xml.Linq.XComment.%23ctor%2A>呼び出しに変換します。  
  
## <a name="example"></a>例  
 次の例では、"This is a comment" というテキストを含む XML コメントを作成します。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XComment>
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

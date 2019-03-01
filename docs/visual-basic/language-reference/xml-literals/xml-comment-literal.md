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
ms.openlocfilehash: 1f8526c4b67b7d975b11f6ef5dada2b45bb6b1df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964184"
---
# <a name="xml-comment-literal-visual-basic"></a>XML コメント リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XComment>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`<!--`|必須。 XML コメントの開始を示します。|  
|`content`|必須。 XML コメントに表示されるテキスト。 一連の 2 つのハイフン (-) または終了タグの横にあるハイフンでエンドを含めることはできません。|  
|`-->`|必須。 XML コメントの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XComment> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML コメント リテラルにはドキュメントの内容が含まれていませんドキュメントに関する情報が含まれます。 XML コメントのセクションは、シーケンス"-->"で終了します。 これは、次の点を意味します。  
  
-   埋め込み式の区切り記号が有効な XML コメントのコンテンツであるので、XML コメント リテラルの埋め込み式を使うことはできません。  
  
-   XML コメントのセクションでは入れ子にできないため、 `content` "-->"値を含むことはできません。  
  
 XML コメント リテラル、変数に割り当てることができます、または XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。 この機能を使用すると、XML ドキュメントから内容をコピーして、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラに XML コメント リテラルへの呼び出しに変換します、<xref:System.Xml.Linq.XComment.%23ctor%2A>コンス トラクター。  
  
## <a name="example"></a>例  
 次の例では、"This is コメント"テキストを含む XML コメントを作成します。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Xml.Linq.XComment>
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

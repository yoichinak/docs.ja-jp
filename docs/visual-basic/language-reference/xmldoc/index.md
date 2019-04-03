---
title: ドキュメント コメントとして推奨される XML タグ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814951"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>ドキュメント コメントとして推奨される XML タグ (Visual Basic)
Visual Basic コンパイラでは、ドキュメントのコメントをコードに XML ファイルを処理できます。 その他のツールを使用して、ドキュメントに XML ファイルを処理することができます。  
  
 XML コメントは、型などのコード コンストラクトでは許可し、メンバーを入力します。 部分の型は、型の 1 つだけの一部はコメントのメンバーに制限はありませんが、XML コメントを持つことができます。  
  
> [!NOTE]
>  ドキュメントのコメントは、名前空間には適用できません。 理由は、1 つの名前空間は、複数のアセンブリをまたがることができ、同時に読み込む必要がないすべてのアセンブリのことです。  
  
 コンパイラは、有効な XML である任意のタグを処理します。 次のタグは、ユーザー ドキュメントでよく使用される機能を提供します。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>コンパイラが構文を検証します)。  
  
> [!NOTE]
>  山かっこをドキュメントのコメントのテキストで表示される場合を使用して、`&lt;`と`&gt;`します。 たとえば、文字列`"&lt;text in angle brackets&gt;"`として表示されます`<text in angle brackets>`します。  
  
## <a name="see-also"></a>関連項目

- [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [方法: XML ドキュメントを作成します。](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

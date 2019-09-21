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
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913505"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>ドキュメント コメントとして推奨される XML タグ (Visual Basic)
Visual Basic コンパイラは、コード内のドキュメントコメントを XML ファイルに処理できます。 XML ファイルをドキュメントに処理するために、追加のツールを使用できます。  
  
 XML コメントは、型や型のメンバーなどのコード構造で使用できます。 部分型の場合、XML コメントを持つことができるのは型の1つの部分のみですが、そのメンバーのコメントには制限はありません。  
  
> [!NOTE]
> ドキュメントコメントを名前空間に適用することはできません。 これは、1つの名前空間が複数のアセンブリにまたがることができ、すべてのアセンブリを同時に読み込む必要がないためです。  
  
 コンパイラは、有効な XML であるすべてのタグを処理します。 次のタグは、ユーザードキュメントで一般的に使用される機能を提供します。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|param > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/param.md)|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|アクセス許可 > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/permission.md)|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|> を<sup></sup> [参照して\<ください](../../../visual-basic/language-reference/xmldoc/see.md)1|seealso > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/seealso.md)|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>コンパイラは構文を検証します)。  
  
> [!NOTE]
> ドキュメントコメントのテキストに山かっこを表示する場合は、および`&lt;` `&gt;`を使用します。 たとえば、文字列`"&lt;text in angle brackets&gt;"`はとして`<text in angle brackets>`表示されます。  
  
## <a name="see-also"></a>関連項目

- [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [方法: XML ドキュメントの作成](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

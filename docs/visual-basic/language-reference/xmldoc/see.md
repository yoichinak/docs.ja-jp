---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 3c149b8ff60bcc2aba06856ad95f461fb18da4b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352229"
---
# <a name="see-visual-basic"></a>\<see> (Visual Basic)
Specifies a link to another member.  
  
## <a name="syntax"></a>構文  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>パラメーター  
 `member`  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。 `member` は、二重引用符 (" ") で囲む必要があります。  
  
## <a name="remarks"></a>Remarks  
 Use the `<see>` tag to specify a link from within text. Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.  
  
 コンパイル時に [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)

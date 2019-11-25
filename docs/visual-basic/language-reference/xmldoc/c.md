---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348511"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
Indicates that text within a description is code.  
  
## <a name="syntax"></a>構文  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`text`|コードとして指定するテキストです。|  
  
## <a name="remarks"></a>Remarks  
 The `<c>` tag gives you a way to indicate that text within a description should be marked as code. 複数行をコードとして指定する場合は、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグを使用します。  
  
 コンパイル時に [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)

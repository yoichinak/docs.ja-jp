---
title: REM ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346730"
---
# <a name="rem-statement-visual-basic"></a>REM ステートメント (Visual Basic)
Used to include explanatory remarks in the source code of a program.  
  
## <a name="syntax"></a>構文  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>指定項目  
 `comment`  
 省略可能です。 The text of any comment you want to include. A space is required between the `REM` keyword and `comment`.  
  
## <a name="remarks"></a>Remarks  
 You can put a `REM` statement alone on a line, or you can put it on a line following another statement. The `REM` statement must be the last statement on the line. If it follows another statement, the `REM` must be separated from that statement by a space.  
  
 You can use a single quotation mark (`'`) instead of `REM`. This is true whether your comment follows another statement on the same line or sits alone on a line.  
  
> [!NOTE]
> You cannot continue a `REM` statement by using a line-continuation sequence (`_`). Once a comment begins, the compiler does not examine the characters for special meaning. For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.  
  
## <a name="example"></a>例  
 The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program. It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [コード内のコメント](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

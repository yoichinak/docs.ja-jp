---
title: Continue ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354110"
---
# <a name="continue-statement-visual-basic"></a>Continue ステートメント (Visual Basic)
Transfers control immediately to the next iteration of a loop.  
  
## <a name="syntax"></a>構文  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Remarks  
 You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop. Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.  
  
 You can use `Continue` at any location in the loop that allows transfers. The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop. If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.  
  
 If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it. You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.  
  
 If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.  
  
## <a name="example"></a>例  
 The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero. The `Continue While` is inside a `For` loop. It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>関連項目

- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

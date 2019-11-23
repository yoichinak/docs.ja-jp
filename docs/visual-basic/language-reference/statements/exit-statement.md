---
title: Exit ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345937"
---
# <a name="exit-statement-visual-basic"></a>Exit ステートメント (Visual Basic)

Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.

## <a name="syntax"></a>構文

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>ステートメント

 `Exit Do`  
 Immediately exits the `Do` loop in which it appears. Execution continues with the statement following the `Loop` statement. `Exit Do` can be used only inside a `Do` loop. When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.

 `Exit For`  
 Immediately exits the `For` loop in which it appears. Execution continues with the statement following the `Next` statement. `Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop. When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.

 `Exit Function`  
 Immediately exits the `Function` procedure in which it appears. Execution continues with the statement following the statement that called the `Function` procedure. `Exit Function` can be used only inside a `Function` procedure.

 To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement. To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).

 `Exit Property`  
 Immediately exits the `Property` procedure in which it appears. Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value. `Exit Property` can be used only inside a property's `Get` or `Set` procedure.

 To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement. To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.

 In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.

 `Exit Select`  
 Immediately exits the `Select Case` block in which it appears. Execution continues with the statement following the `End Select` statement. `Exit Select` can be used only inside a `Select Case` statement.

 `Exit Sub`  
 Immediately exits the `Sub` procedure in which it appears. Execution continues with the statement following the statement that called the `Sub` procedure. `Exit Sub` can be used only inside a `Sub` procedure.

 In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.

 `Exit Try`  
 Immediately exits the `Try` or `Catch` block in which it appears. Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise. `Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.

 `Exit While`  
 Immediately exits the `While` loop in which it appears. Execution continues with the statement following the `End While` statement. `Exit While` can be used only inside a `While` loop. When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.

## <a name="remarks"></a>Remarks

Do not confuse `Exit` statements with `End` statements. `Exit` does not define the end of a statement.

## <a name="example"></a>例

In the following example, the loop condition stops the loop when the `index` variable is greater than 100. The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>例

The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>例

The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>関連項目

- [Continue ステートメント](continue-statement.md)
- [Do...Loop ステートメント](do-loop-statement.md)
- [End ステートメント](end-statement.md)
- [For Each...Next ステートメント](for-each-next-statement.md)
- [For...Next ステートメント](for-next-statement.md)
- [Function ステートメント](function-statement.md)
- [Return ステートメント](return-statement.md)
- [Stop ステートメント](stop-statement.md)
- [Sub ステートメント](sub-statement.md)
- [Try...Catch...Finally ステートメント](try-catch-finally-statement.md)

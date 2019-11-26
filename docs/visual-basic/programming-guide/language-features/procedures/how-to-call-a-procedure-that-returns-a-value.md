---
title: '方法: 値を返すプロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340739"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>方法: 値を返すプロシージャを呼び出す (Visual Basic)
A `Function` procedure returns a value to the calling code. You call it by including its name and arguments either on the right side of an assignment statement or in an expression.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>To call a Function procedure within an expression  
  
1. Use the `Function` procedure name the same way you would use a variable. You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.  
  
2. Follow the procedure name with parentheses to enclose the argument list. If there are no arguments, you can optionally omit the parentheses. However, using the parentheses makes your code easier to read.  
  
3. Place the arguments in the argument list within the parentheses, separated by commas. Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.  
  
     Alternatively, you can pass one or more arguments by name. For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).  
  
4. The value returned from the procedure participates in the expression just as the value of a variable or constant would.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>To call a Function procedure in an assignment statement  
  
1. Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.  
  
2. Follow the procedure name with parentheses to enclose the argument list. If there are no arguments, you can optionally omit the parentheses. However, using the parentheses makes your code easier to read.  
  
3. Place the arguments in the argument list within the parentheses, separated by commas. Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.  
  
4. The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.  
  
## <a name="example"></a>例  
 The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable. The first line calls `Environ` within an expression, and the second line calls it in an assignment statement. `Environ` takes the variable name as its sole argument. It returns the variable's value to the calling code.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [Function プロシージャ](./function-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [方法 : 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)
- [方法 : プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)
- [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)

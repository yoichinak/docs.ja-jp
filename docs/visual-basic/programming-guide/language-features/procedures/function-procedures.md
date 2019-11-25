---
title: Function プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341087"
---
# <a name="function-procedures-visual-basic"></a>Function プロシージャ (Visual Basic)
A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements. The `Function` procedure performs a task and then returns control to the calling code. When it returns control, it also returns a value to the calling code.  
  
 Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.  
  
 You can define a `Function` procedure in a module, class, or structure. It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.  
  
 A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.  
  
## <a name="declaration-syntax"></a>宣言の構文  
 The syntax for declaring a `Function` procedure is as follows:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing. For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).  
  
### <a name="data-type"></a>データの種類  
 Every `Function` procedure has a data type, just as every variable does. This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code. The following sample declarations illustrate this.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Returning Values  
 The value a `Function` procedure sends back to the calling code is called its return value. The procedure returns this value in one of two ways:  
  
- It uses the `Return` statement to specify the return value, and returns control immediately to the calling program. 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- It assigns a value to its own function name in one or more statements of the procedure. Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed. 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement. This allows you to assign a preliminary value and adjust it later if necessary.  
  
 For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md). For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Calling Syntax  
 You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression. You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses. If no arguments are supplied, you can optionally omit the parentheses.  
  
 The syntax for a call to a `Function` procedure is as follows:  
  
 *lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`  
  
 When you call a `Function` procedure, you do not have to use its return value. If you do not, all the actions of the function are performed, but the return value is ignored. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration of Declaration and Call  
 The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 The following example shows a typical call to `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [方法 : 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)
- [方法 : プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)
- [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)

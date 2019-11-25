---
title: 引数の値渡しと参照渡し
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 28e59753a35ab67b15fbc549df5bb8a3489aba5a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352606"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡し (Visual Basic)
In Visual Basic, you can pass an argument to a procedure *by value* or *by reference*. This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code. The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.  
  
## <a name="distinctions"></a>Distinctions  
 When passing an argument to a procedure, be aware of several different distinctions that interact with each other:  
  
- Whether the underlying programming element is modifiable or nonmodifiable  
  
- Whether the argument itself is modifiable or nonmodifiable  
  
- Whether the argument is being passed by value or by reference  
  
- Whether the argument data type is a value type or a reference type  
  
 For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Choice of Passing Mechanism  
 You should choose the passing mechanism carefully for each argument.  
  
- **Protection**. In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change. The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument. The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.  
  
- **Performance**. Although the passing mechanism can affect the performance of your code, the difference is usually insignificant. One exception to this is a value type passed `ByVal`. In this case, Visual Basic copies the entire data contents of the argument. Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.  
  
     For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms). Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.  
  
## <a name="determination-of-the-passing-mechanism"></a>Determination of the Passing Mechanism  
 The procedure declaration specifies the passing mechanism for each parameter. The calling code can't override a `ByVal` mechanism.  
  
 If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call. For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 The default in Visual Basic is to pass arguments by value.  
  
## <a name="when-to-pass-an-argument-by-value"></a>When to Pass an Argument by Value  
  
- If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). No code can change the value of a nonmodifiable element.  
  
- If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`. Only the calling code can change the value of a modifiable element passed by value.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>When to Pass an Argument by Reference  
  
- If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
- If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`. If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 The following example illustrates when to pass arguments by value and when to pass them by reference. Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter. Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`. Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`. Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)
- [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)

---
title: 'How to: Pass Procedures to Another Procedure'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345247"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>方法 : Visual Basic でプロシージャを別のプロシージャに渡す
This example shows how to use delegates to pass a procedure to another procedure.  
  
 A delegate is a type that you can use like any other type in Visual Basic. The `AddressOf` operator returns a delegate object when applied to a procedure name.  
  
 This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Create the delegate and matching procedures  
  
1. Create a delegate named `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Create a procedure named `DelegateTest` that takes a delegate as a parameter.  
  
     This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8. Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.  
  
## <a name="see-also"></a>関連項目

- [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [方法: デリゲート メソッドを呼び出す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

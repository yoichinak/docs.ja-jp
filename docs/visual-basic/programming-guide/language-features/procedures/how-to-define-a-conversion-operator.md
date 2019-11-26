---
title: '方法 : 変換演算子を定義する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344901"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>方法: 変換演算子を定義する (Visual Basic)
If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).  
  
 Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure. All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Defining an operator on a class or structure is also called *overloading* the operator.  
  
## <a name="example"></a>例  
 The following example defines conversion operators between a structure called `digit` and a `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 You can test the structure `digit` with the following code.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>関連項目

- [演算子プロシージャ](./operator-procedures.md)
- [方法 : 演算子を定義する](./how-to-define-an-operator.md)
- [方法 : 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)
- [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)
- [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [方法 : 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

---
title: += 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 31a6da163061b905b8ffddcfc4b44978f5cdd55e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350310"
---
# <a name="-operator-visual-basic"></a>+= 演算子 (Visual Basic)
Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property. Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須です。 Any numeric or `String` variable or property.  
  
 `expression`  
 必須です。 Any numeric or `String` expression.  
  
## <a name="remarks"></a>Remarks  
 The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array. The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left. The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.  
  
> [!NOTE]
> When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur. Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.  
  
 This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics. For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator. For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>オーバーロード  
 The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. Overloading the `+` operator affects the behavior of the `+=` operator. If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior. 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 The following example uses the `+=` operator to combine the value of one variable with another. The first part uses `+=` with numeric variables to add one value to another. The second part uses `+=` with `String` variables to concatenate one value with another. In both cases, the result is assigned to the first variable.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 The value of `num1` is now 13, and the value of `str1` is now "103".  
  
## <a name="see-also"></a>関連項目

- [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)

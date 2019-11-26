---
title: = 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350202"
---
# <a name="-operator-visual-basic"></a>= 演算子 (Visual Basic)
Assigns a value to a variable or property.  
  
## <a name="syntax"></a>構文  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 Any writable variable or any property.  
  
 `value`  
 Any literal, constant, or expression.  
  
## <a name="remarks"></a>Remarks  
 The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array. The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). The `=` operator assigns the value on its right to the variable or property on its left.  
  
> [!NOTE]
> The `=` operator is also used as a comparison operator. For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>オーバーロード  
 The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator. 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 The following example demonstrates the assignment operator. The value on the right is assigned to the variable on the left.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [& = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

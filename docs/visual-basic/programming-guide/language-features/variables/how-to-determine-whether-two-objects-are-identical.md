---
title: '方法 : 2 つのオブジェクトが同一であるかどうか判別する'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348595"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>方法: 2 つのオブジェクトが同一であるかどうか判別する (Visual Basic)
In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory. For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.  
  
 Visual Basic provides two operators to compare pointers. The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.  
  
## <a name="determining-if-two-objects-are-identical"></a>Determining if Two Objects Are Identical  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>To determine if two objects are identical  
  
1. Set up a `Boolean` expression to test the two objects.  
  
2. In your testing expression, use the `Is` operator with the two objects as operands.  
  
     `Is` returns `True` if the objects point to the same class instance.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Determining if Two Objects Are Not Identical  
 Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`. In such a case you can use the `IsNot` operator.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>To determine if two objects are not identical  
  
1. Set up a `Boolean` expression to test the two objects.  
  
2. In your testing expression, use the `IsNot` operator with the two objects as operands.  
  
     `IsNot` returns `True` if the objects do not point to the same class instance.  
  
## <a name="example"></a>例  
 The following example tests pairs of `Object` variables to see if they point to the same class instance.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 The preceding example displays the following output.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>関連項目

- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [方法: 2 つのオブジェクトが関連しているかどうかを決める](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

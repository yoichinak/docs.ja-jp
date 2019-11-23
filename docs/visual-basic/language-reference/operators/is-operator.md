---
title: Is 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349542"
---
# <a name="is-operator-visual-basic"></a>Is 演算子 (Visual Basic)
Compares two object reference variables.  
  
## <a name="syntax"></a>構文  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須です。 Any `Boolean` value.  
  
 `object1`  
 必須です。 Any `Object` name.  
  
 `object2`  
 必須です。 Any `Object` name.  
  
## <a name="remarks"></a>Remarks  
 The `Is` operator determines if two object references refer to the same object. However, it does not perform value comparisons. If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.  
  
 `Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.  
  
> [!NOTE]
> The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>例  
 The following example uses the `Is` operator to compare pairs of object references. The results are assigned to a `Boolean` value representing whether the two objects are identical.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.  
  
## <a name="see-also"></a>関連項目

- [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

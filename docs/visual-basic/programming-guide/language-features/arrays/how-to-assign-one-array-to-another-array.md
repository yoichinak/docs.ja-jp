---
title: '方法 : 配列を別の配列に代入する'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351890"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>方法: 配列を別の配列に代入する (Visual Basic)

Because arrays are objects, you can use them in assignment statements like other object types. An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.

### <a name="to-assign-one-array-to-another-array"></a>To assign one array to another array

1. Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.

2. Use a standard assignment statement to assign the source array to the destination array. Do not follow either array name with parentheses.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

When you assign one array to another, the following rules apply:

- **Equal Ranks.** The rank (number of dimensions) of the destination array must be the same as that of the source array.

  Provided the ranks of the two arrays are equal, the dimensions do not need to be equal. The number of elements in a given dimension can change during assignment.

- **Element Types.** Either both arrays must have *reference type* elements or both arrays must have *value type* elements. 詳細については、「 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。

  - If both arrays have value type elements, the element data types must be exactly the same. The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.

  - If both arrays have reference type elements, the source element type must derive from the destination element type. When this is the case, the two arrays have the same inheritance relationship as their elements. This is called *array covariance*.

The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal. You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment. You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.

## <a name="see-also"></a>関連項目

- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)

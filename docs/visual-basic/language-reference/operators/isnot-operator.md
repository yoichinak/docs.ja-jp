---
title: IsNot 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336074"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 演算子 (Visual Basic)

Compares two object reference variables.

## <a name="syntax"></a>構文

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>指定項目
 `result` 必須。 `Boolean` 値。

 `object1` 必須。 Any `Object` variable or expression.

 `object2` 必須。 Any `Object` variable or expression.

## <a name="remarks"></a>Remarks
 The `IsNot` operator determines if two object references refer to different objects. However, it does not perform value comparisons. If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.

 `IsNot` is the opposite of the `Is` operator. The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.

 You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.

## <a name="example"></a>例
 The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>関連項目

- [Is 演算子](is-operator.md)
- [TypeOf 演算子](typeof-operator.md)
- [Visual Basic における演算子の優先順位](operator-precedence.md)
- [方法: 2 つのオブジェクトが等しいかどうかをテストする](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)

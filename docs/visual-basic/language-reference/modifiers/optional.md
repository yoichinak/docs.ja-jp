---
title: Optional
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: a16dae35bf4bc84d95501624c4f023f390a8dda8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351434"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)

Specifies that a procedure argument can be omitted when the procedure is called.

## <a name="remarks"></a>Remarks

For each optional parameter, you must specify a constant expression as the default value of that parameter. If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.

If the parameter list contains an optional parameter, every parameter that follows it must also be optional.

`Optional` 修飾子は、次のコンテキストで使用できます。

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> When calling a procedure with or without optional parameters, you can pass arguments by position or by name. For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).

> [!NOTE]
> You can also define a procedure with optional parameters by using overloading. If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t. 詳細については、「 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。

## <a name="example"></a>例

The following example defines a procedure that has an optional parameter.

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a>例

The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name. The procedure has two optional parameters.

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>関連項目

- [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)
- [省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)

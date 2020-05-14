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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351434"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)

プロシージャが呼び出されるときにプロシージャ引数が省略可能であることを示します。

## <a name="remarks"></a>Remarks

省略可能なパラメーターごとに、そのパラメーターの既定値として定数式を指定する必要があります。 式が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価される場合は、値データ型の既定値がパラメーターの既定値として使用されます。

パラメーター リストに省略可能なパラメーターが含まれている場合は、その後に続くすべてのパラメーターも省略可能である必要があります。

`Optional` 修飾子は、次のコンテキストで使用できます。

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> 省略可能なパラメーターの有無にかかわらず、プロシージャを呼び出すときは、位置または名前によって引数を渡すことができます。 詳細については、「[位置と名前による引数渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)」を参照してください。

> [!NOTE]
> オーバーロードを使用して省略可能なパラメーターを持つプロシージャを定義することもできます。 省略可能なパラメーターが 1 つあるとすると、パラメーターを受け取る場合と受け取らない場合の、2 つのオーバーロードされたバージョンのプロシージャを定義できます。 詳細については、「 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。

## <a name="example"></a>例

次の例では、省略可能なパラメーターがあるプロシージャを定義しています。

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

次の例では、位置で渡される引数と名前で渡される引数を使用してプロシージャを呼び出す方法を示します。 このプロシージャには、2 つの省略可能なパラメーターがあります。

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>関連項目

- [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)
- [省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)

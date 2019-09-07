---
title: If...Then...Else ステートメント (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: db81a1c41809b563d5f9d0777c3feb064c5e540b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400709"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else ステートメント (Visual Basic)

式の値に応じてステートメント グループを条件付きで実行します。

## <a name="syntax"></a>構文

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a>コード例へのクイックリンク

この記事には、 `If`...`Then`...`Else`ステートメント:

- [複数行構文の例](#multi-line)
- [入れ子になった構文の例](#nested)
- [単一行構文の例](#single-line)

## <a name="parts"></a>指定項目

`condition` \
必須。 条件. `True`は`Boolean`、、、またはに暗黙的に変換可能なデータ型に評価される必要があります。 `False`

式が[Nothing](../../../visual-basic/language-reference/nothing.md)に`False`評価される[null 許容](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`変数である場合、条件は式がで`ElseIf`あるかのように処理され、ブロックが存在する場合`Else`は評価され、ブロックは存在する場合は実行されます。

`Then` \
単一行の構文では必須です。複数行の構文では省略可能です。

`statements` \
任意。 次の1つまた`If`は複数のステートメントをフォローしています...`Then`が`condition`に評価`True`される場合に実行される。

`elseifcondition` \
が存在`ElseIf`する場合は必須です。 条件. `True`は`Boolean`、、、またはに暗黙的に変換可能なデータ型に評価される必要があります。 `False`

`elseifstatements` \
任意。 次の1つまた`ElseIf`は複数のステートメントをフォローしています...`Then`が`elseifcondition`に評価`True`される場合に実行される。

`elsestatements` \
任意。 前`condition`のまたは`elseifcondition`式がと評価`True`されなかった場合に実行される1つ以上のステートメント。

`End If` \
の`If`複数行バージョンを終了します...`Then`...`Else`ブロック。

## <a name="remarks"></a>Remarks

### <a name="multiline-syntax"></a>複数行の構文

`If`When...`Then`...ステートメントが検出されました。がテストされています。`condition` `Else` `Then`が`condition` の`True`場合は、次のステートメントが実行されます。 `ElseIf`が`condition` の場合、各ステートメント(存在する場合)は順番に評価されます。`False` が見つかると、関連付けられ`ElseIf`たの直後にあるステートメントが実行されます。 `True` `elseifcondition` `ElseIf`がに`elseifcondition`評価されない場合、またはステートメントが存在しない`Else`場合は、次のステートメントが実行されます。 `True` 、 `Then` `End If`、または`Else`に続くステートメントを実行すると、次のステートメントで実行が続行されます。 `ElseIf`

句`ElseIf` と`Else`句はどちらも省略可能です。 必要な数`ElseIf` `If`の句を含めることができます...`Then`...ステートメントですが、句の後に`Else`句を記述することはできません`ElseIf`。 `Else` `If`...`Then`...`Else`ステートメントは、入れ子にすることができます。

複数行構文`If`では、ステートメントが1行目の唯一のステートメントである必要があります。 、 `ElseIf` 、`Else`および`End If`の各ステートメントの前には、行ラベルだけを指定できます。 `If`...`Then`...ブロックは`End If`ステートメントで終了する必要があります。 `Else`

> [!TIP]
> [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)をいくつかの値を持つ 1 つの式を評価するときにさらに便利な場合があります。

### <a name="single-line-syntax"></a>単一行の構文

単一行構文を使用すると、コードを含む単一の条件を使用して、true の場合に実行できます。 ただし、複数行の構文では、より多くの構造と柔軟性が提供され、読み取り、保守、デバッグが簡単になります。

ステートメントが単`Then`一行`If`であるかどうかを判断するために、キーワードの後に続く内容を確認します。 コメント以外のものが`Then`同じ行にある場合、ステートメントは単一行`If`のステートメントとして扱われます。 が`Then`存在しない場合は、複数行`If`の先頭にする必要があります...`Then`...`Else`.

単一行構文では、... の結果として複数の`If`ステートメントを実行できます。`Then`決定。 すべてのステートメントは、同じ行にあり、コロンで区切られている必要があります。

## <a name="multiline-syntax-example"></a>複数行構文の例

<a name="multi-line"></a>

次の例では、 `If`... の複数行構文の使用方法を示しています。`Then`...`Else`ステートメント。

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>入れ子になった構文の例

<a name="nested"></a>

次の例には`If`、入れ子になった...`Then`...`Else`ステートメント。

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>単一行構文の例

<a name="single-line"></a>単一行構文の使用例を次に示します。

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [条件判断構造](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Visual Basic の論理演算子とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)

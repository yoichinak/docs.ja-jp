---
title: If 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249488"
---
# <a name="if-operator-visual-basic"></a>If 演算子 (Visual Basic)

短絡評価を使用して、条件的に 2 つの値のいずれかを返します。 演算子`If`は、3 つの引数または 2 つの引数を使用して呼び出すことができます。

## <a name="syntax"></a>構文

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>演算子が 3 つの引数で呼び出された場合

3`If`つの引数を使用して呼び出された場合、最初の引数は`Boolean`、 としてキャストできる値に評価される必要があります。 この`Boolean`値によって、他の 2 つの引数のうち、評価されて返される引数が決まります。 次のリストは、演算子が`If`3 つの引数を使用して呼び出された場合にのみ適用されます。

### <a name="parts"></a>要素

|期間|定義|
|---|---|
|`argument1`|必須。 `Boolean`. 評価して返す他の引数を決定します。|
|`argument2`|必須。 `Object`. 評価され、評価`argument1`された場合に`True`返されます。|
|`argument3`|必須。 `Object`. 評価され、評価`argument1`された場合、`False`または`argument1`Nothing[に評価](../../../visual-basic/language-reference/nothing.md)される[Null 許容](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean`変数かどうかが返されます。|

3`If`つの引数を指定して呼び出される`IIf`演算子は、短絡評価を使用する点を除いて関数と同様に機能します。 関数`IIf`は常に 3 つの引数すべてを評価しますが`If`、3 つの引数を持つ演算子では 2 つの引数のみが評価されます。 最初`If`の引数が評価され、結果が`Boolean`値としてキャスト`True`されます。 `False` 値が`True`の`argument2`場合は、評価され、その値は返`argument3`されますが、評価されません。 `Boolean`式の値が の`argument3`場合`False`は、評価され、その値は返されますが`argument2`、評価されません。 次の例は、3`If`つの引数を使用する場合の使用方法を示しています。

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

次の例は、短絡評価の値を示しています。 この例では、変数で`number``divisor``divisor`変数を除いて変数を除いて変数を除く 2 つの試みが示されています。 この場合は、0 を返す必要があり、ランタイム エラーが発生するため、除算を実行する試行は行いません。 式は`If`短絡評価を使用するため、最初の引数の値に応じて、2 番目または 3 番目の引数を評価します。 最初の引数が true の場合、除数はゼロではなく、2 番目の引数を評価して除算を実行しても安全です。 最初の引数が false の場合、3 番目の引数のみが評価され、0 が返されます。 したがって、除数が 0 の場合、除算の実行は試行されず、エラー結果も発生しません。 ただし、短`IIf`絡評価を使用しないため、最初の引数が false の場合でも 2 番目の引数が評価されます。 これにより、実行時の 0 除算エラーが発生します。

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>演算子が 2 つの引数で呼び出された場合

最初の引数は`If`省略できます。 これにより、演算子は 2 つの引数のみを使用して呼び出すことができます。 次のリストは、演算子が`If`2 つの引数で呼び出された場合にのみ適用されます。

### <a name="parts"></a>要素

|期間|定義|
|---|---|
|`argument2`|必須。 `Object`. 参照または null 許容値型である必要があります。 評価され、 以外`Nothing`の値に評価されると返されます。|
|`argument3`|必須。 `Object`. 評価され、評価`argument2`された場合に`Nothing`返されます。|

引数を`Boolean`省略する場合、最初の引数は参照または null 許容値型である必要があります。 最初の引数が`Nothing`に評価された場合、2 番目の引数の値が返されます。 それ以外の場合は、最初の引数の値が返されます。 次の例は、この評価のしくみを示しています。

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [null 許容値型](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)

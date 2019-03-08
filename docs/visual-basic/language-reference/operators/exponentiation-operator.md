---
title: ^ 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 54de9c91d4e166b8ca1733952dfa9c98ebf11ffe
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674095"
---
# <a name="-operator-visual-basic"></a>^ 演算子 (Visual Basic)

数値のべき乗する数値を生成します。

## <a name="syntax"></a>構文

```
number ^ exponent
```

## <a name="parts"></a>指定項目

`number`\
必須。 任意の数式。

`exponent`\
必須。 任意の数式。

## <a name="result"></a>結果

結果は`number`の累乗`exponent`、として常に、`Double`値。

## <a name="supported-types"></a>サポートされている型

`Double`。 さまざまな型のオペランドが変換されます`Double`します。

## <a name="remarks"></a>Remarks

Visual Basic の指数演算を常に実行する、 [Double データ型](../../../visual-basic/language-reference/data-types/double-data-type.md)します。

値`exponent`、小数部は、負の値、またはその両方です。

1 つの式で複数の指数演算を実行すると、`^`左から右にした、演算子が評価されます。

> [!NOTE]
> `^`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。

## <a name="example"></a>例

次の例では、`^`演算子を使って数値の指数。 最初のオペランドが 2 番目の累乗になります。

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

前の例では、次の結果が生成されます。

`exp1` 4 (2 乗) に設定されます。

`exp2` 19683 (3 乗を 2 乗し、その値) に設定されます。

`exp3` -125 (アイス -5) に設定されます。

`exp4` 625 (4 番目の電源を-5) に設定されます。

`exp5` 2 (8 の立方根) に設定されます。

`exp6` 0.5 (8 の立方根で割った値 1.0) に設定されます。

上記の例の式のかっこの中の重要性に注意してください。 ため*演算子の優先順位*、Visual Basic が通常は、`^`する前に、他の演算子も、単項`–`演算子。 場合`exp4`と`exp6`が計算されたかっこがない場合、次の結果を作成した場合します。

`exp4 = -5 ^ 4` -(4 番目の電源を 5) として計算されます-625 されると、します。

`exp6 = 8 ^ -1.0 / 3.0` (– 1 の電源または 0.125 8) として計算は 3.0 では、0.041666666666666666666666666666667 なりますで割った値します。

## <a name="see-also"></a>関連項目

- [^= 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

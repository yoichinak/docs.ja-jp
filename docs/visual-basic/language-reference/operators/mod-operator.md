---
title: Mod 演算子 (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: 08e3eec08ba099e6f5c7796a459c55de09afa917
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929329"
---
# <a name="mod-operator-visual-basic"></a>Mod 演算子 (Visual Basic)

2つの数値を除算し、剰余だけを返します。

## <a name="syntax"></a>構文

```vb
result = number1 Mod number2
```

## <a name="parts"></a>指定項目

`result` \
必須。 任意の数値変数またはプロパティ。

`number1` \
必須。 任意の数式。

`number2` \
必須。 任意の数式。

## <a name="supported-types"></a>サポートされる型

すべての数値型。 これには、符号なしおよび浮動小数点`Decimal`型とが含まれます。

## <a name="result"></a>結果

結果は、をで`number1` `number2`除算した後の剰余になります。 たとえば、式`14 Mod 4`は2に評価されます。

> [!NOTE]
> 算術の*剰余*と*剰余*の違いはありますが、負の数値の結果は異なります。 Visual Basic の`op_Modulus`演算子、.NET Framework 演算子、および基になる [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 命令はすべて、剰余演算を実行します。`Mod`

`Mod`操作の結果は、 `number1`被除数の符号を保持します。したがって、正の値または負の値を指定できます。 結果は常に (-`number2`, `number2`) の範囲内にあり、排他的です。 例:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Remarks

または`number1` `number2`のいずれかが浮動小数点値の場合は、除算の浮動小数点の剰余が返されます。 結果のデータ型は、および`number1` `number2`のデータ型との除算によって得られるすべての値を保持できる最小のデータ型です。

また`number1`は`number2`が[Nothing](../../../visual-basic/language-reference/nothing.md)に評価される場合、0として扱われます。

関連する演算子は次のとおりです。

- [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)は、除算の整数の商を返します。 たとえば、式`14 \ 4`は3に評価されます。

- [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)は、剰余を含む完全な商を浮動小数点数として返します。 たとえば、式`14 / 4`は3.5 に評価されます。

## <a name="attempted-division-by-zero"></a>0による除算を試行しました

が`number2` 0 に評価される場合、 `Mod`演算子の動作はオペランドのデータ型によって異なります。

- コンパイル時にを特定<xref:System.DivideByZeroException>できず`number2` 、コンパイル時にがゼロに評価された`number2`場合、が`BC30542 Division by zero occurred while evaluating this expression`コンパイル時エラーを生成する場合、整数除算は例外をスローします。
- 浮動小数点除算はを<xref:System.Double.NaN?displayProperty=nameWithType>返します。

## <a name="equivalent-formula"></a>同等の式

式`a Mod b`は、次の数式のいずれかに相当します。

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>浮動小数点おける誤差

浮動小数点数を使用する場合は、メモリ内で常に正確な10進表現が使用されるわけではないことに注意してください。 これにより、値の比較や`Mod`演算子など、特定の操作によって予期しない結果が発生する可能性があります。 詳細については、「[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。

## <a name="overloading"></a>オーバーロード

演算子はオーバーロードできます。つまり、クラスまたは構造体が動作を再定義できます。 `Mod` このようなオーバーロード`Mod`を含むクラスまたは構造体のインスタンスにコードを適用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。

## <a name="example"></a>例

次の例では`Mod` 、演算子を使用して2つの数値を除算し、剰余だけを返します。 どちらかの数値が浮動小数点数の場合、結果は剰余を表す浮動小数点数になります。

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>例

次の例は、浮動小数点オペランドのおける誤差の可能性を示しています。 最初のステートメントでは、オペランドは`Double`で、0.2 は0.20000000000000001 の値が格納された無限の連続するバイナリ部分です。 2番目のステートメントでは、リテラル`D`の型文字は`Decimal`両方のオペランドを強制的ににし、0.2 は正確な表現を持ちます。

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic の算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)

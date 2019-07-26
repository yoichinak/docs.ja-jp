---
title: 10 進型 (Decimal) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: bab5a0bd7e0a85d550362bc3c1166566f6dcb81b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512772"
---
# <a name="decimal-data-type-visual-basic"></a>10 進型 (Decimal) (Visual Basic)

10の可変指数でスケーリングされた96ビット (12 バイト) の整数値を表す、符号付き128ビット (16 バイト) の値を保持します。 スケールファクターは、小数点の右側の桁数を指定します。0から28までの範囲です。 小数点以下桁数が 0 (小数点以下桁数) の場合、有効な最大値は +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28) です。 小数点以下を28桁にすると、最大値は +/-7.9228162514264337593543950335、0以外の最小値は +/-0.0000000000000000000000000001 (+/-1E-28) になります。

## <a name="remarks"></a>Remarks

データ`Decimal`型は、数値の有効桁数の最大値を提供します。 最大29桁の有効桁数をサポートし、7.9228 x 10 ^ 28 を超える値を表すことができます。 これは、多くの数字を必要とするが丸め誤差を許容できない財務などの計算に特に適しています。

`Decimal` の既定値は 0 です。

## <a name="programming-tips"></a>プログラミングのヒント

- **精度.** `Decimal`が浮動小数点データ型ではありません。 構造`Decimal`体は、2進数の整数値を保持します。符号ビットと、値のどの部分が小数点であるかを指定する整数の拡大率です。 このため、数値`Decimal`は浮動小数点型 (`Single`および`Double`) よりも、メモリ内でより正確に表現されます。

- **パフォーマンス。** `Decimal`データ型は、すべての数値型の中で最も低速なものです。 データ型を選択する前に、精度の重要性をパフォーマンスと比較する必要があります。

- **広げ.** データ`Decimal`型はまたは`Single` `Double`に拡大変換されます。 これは、エラーを`Decimal` <xref:System.OverflowException?displayProperty=nameWithType>発生させることなく、いずれかの型に変換できることを意味します。

- **後続のゼロ。** Visual Basic は、 `Decimal`リテラルに後続のゼロを格納しません。 ただし、変数`Decimal`は、計算を取得した後続のゼロを保持します。 次に例を示します。

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  前の例`MsgBox`のの出力は次のようになります。

  ```
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **文字を入力します。** あるリテラルにリテラルの型文字 `D` を付けると、そのリテラルは `Decimal` に変換されます。 ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 (`Decimal`) に変換されます。

- **フレームワークの種類。** .NET Framework において対応する型は、<xref:System.Decimal?displayProperty=nameWithType> 構造体です。

## <a name="range"></a>範囲
 型文字を使用して`D` 、 `Decimal`変数または定数に大きな値を割り当てることが必要になる場合があります。 この要件は、次の例に示すよう`Long`に、リテラルの型文字がリテラルの後に続く場合を除き、コンパイラがリテラルをとして解釈するためです。

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

の`bigDec1`宣言はオーバーフローを生成しません。これは、割り当てられた値がの`Long`範囲内にあるためです。 変数に値を割り当てることができます。 `Long` `Decimal`

に割り当てら`bigDec2`れた値が大きすぎる`Long`ため、の宣言によってオーバーフローエラーが生成されます。 数値リテラルは最初にとして`Long`解釈できないため、 `Decimal`変数に代入することはできません。

の`bigDec3`場合、リテラルの型`D`文字は、コンパイラがリテラルをとしてでは`Decimal`なく`Long`として解釈するよう強制することで、問題を解決します。

## <a name="see-also"></a>関連項目

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Single データ型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double 型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

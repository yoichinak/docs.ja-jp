---
title: Decimal データ型
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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243324"
---
# <a name="decimal-data-type-visual-basic"></a>10 進型 (Decimal) (Visual Basic)

可変 10 の累乗によってスケーリングされた 96 ビット (12 バイト) 整数値を表す符号付き 128 ビット (16 バイト) 値を保持します。 スケール ファクターは、小数点の右側の桁数を指定します。0 から 28 までの範囲です。 0 (小数点以下の桁数なし) の場合、最大の値は +/-79,228,162,514,264,337,593,543,950,335 (+/-7.92816251422643375935335335E+28) です。 小数点以下 28 桁の最大値は +/-7.92281625142643375935439393955555555530335 で、ゼロ以外の最小値は +/-0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000

## <a name="remarks"></a>解説

データ`Decimal`型は、数値の有効桁数の最大数を提供します。 最大 29 桁の有効桁数をサポートし、7.9228 x 10^28 を超える値を表すことができます。 特に、財務計算など、桁数が多く必要な場合でも、丸め誤差を許容できない計算に適しています。

`Decimal` の既定値は 0 です。

## <a name="programming-tips"></a>プログラミングのヒント

- **精度。** `Decimal`は浮動小数点データ型ではありません。 この`Decimal`構造体には、2 進整数値と、符号ビットと、値のどの部分が小数であるかを指定する整数のスケーリング係数が格納されます。 このため、`Decimal`数値は浮動小数点型 ( および`Single``Double`) よりも正確なメモリ表現を持ちます。

- **パフォーマンス。** データ`Decimal`型は、すべての数値型の中で最も低速です。 データ型を選択する前に、精度の重要性とパフォーマンスの比較を検討する必要があります。

- **拡大。** データ`Decimal`型が、 または`Single``Double`に拡大されます。 つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`Decimal`することなく、これらの型のいずれかに変換できます。

- **末尾のゼロ。** Visual Basic では、末尾のゼロは`Decimal`リテラルに格納されません。 ただし、変数`Decimal`は計算上、取得した後続のゼロを保持します。 次の例を使って説明します。

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  上記の`MsgBox`例の出力は次のとおりです。

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **文字を入力します。** あるリテラルにリテラルの型文字 `D` を付けると、そのリテラルは `Decimal` に変換されます。 ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 (`Decimal`) に変換されます。

- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.Decimal?displayProperty=nameWithType> 構造体です。

## <a name="range"></a>範囲

 変数または定数に大きな`D`値を割り当てるには、型`Decimal`文字を使用する必要がある場合があります。 この要件は、次の例に示すように、`Long`リテラルの型文字がリテラルの後に続く場合を除き、コンパイラがリテラルを解釈するためです。

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

に割り`bigDec1`当てられた値が の範囲内にあるため、 の宣言ではオーバーフローが発生しません`Long`。 値`Long`は変数に`Decimal`割り当てることができます。

に割り`bigDec2`当てられた値が大きすぎるため、 の宣言はオーバーフロー エラーを`Long`生成します。 数値リテラルは、 として`Long`解釈できないため、 変数に`Decimal`代入することはできません。

リテラル`bigDec3`型文字`D`は、リテラルを の`Decimal`代わりに a として解釈するようにコンパイラに強制することによって、この問題`Long`を解決します。

## <a name="see-also"></a>関連項目

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [Single データ型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double データ型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [CString](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

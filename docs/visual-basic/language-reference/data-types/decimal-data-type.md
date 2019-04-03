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
ms.openlocfilehash: 4d530a8c1f85d2f0045184c05df63849047a8204
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834102"
---
# <a name="decimal-data-type-visual-basic"></a>10 進型 (Decimal) (Visual Basic)
符号付き 10 の累乗によってスケーリング 96 ビット (12 バイト) の整数値を表す 128 ビット (16 バイト) 値を保持します。 スケール ファクターは小数点の右側にある数字の数を指定します。その範囲は 0 から 28 です。 最大有効値は 0 (数値) の小数点以下桁数、79,228,162,514,264,337,593,543,950,335 +/-(7 +/-.9228162514264337593543950335E + 28)。 小数点以下桁数が 28 7.9228162514264337593543950335 については、最大値は、および 0 以外の最小値は、(1 e ~ 28) +/-+/-0.0000000000000000000000000001。  
  
## <a name="remarks"></a>Remarks  
 `Decimal`データ型有効桁数の最大数を提供しています。 最大 29 桁をサポートし、7.9228 x 10 を超える値を表すことができます ^28。 など、計算に特に適しています金融機関、多くの桁数が必要ですが、丸めエラーを許容することはできません。  
  
 `Decimal` の既定値は 0 です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **有効桁数です。** `Decimal` 浮動小数点データ型はありません。 `Decimal`構造体は、符号ビットとスケール ファクターがどの程度の値が 10 進数の割合を指定する整数値のバイナリ整数値を保持します。 このため、`Decimal`番号は、浮動小数点型よりもメモリ内でより正確な表現を持ち (`Single`と`Double`)。  
  
-   **パフォーマンス。** `Decimal`データ型はすべての数値型の最も遅い。 データ型を選択する前にパフォーマンスと精度の重要性を比較検討する必要があります。  
  
-   **拡大します。** `Decimal`拡大変換後のデータ型`Single`または`Double`します。 つまり、変換できる`Decimal`遭遇することがなくこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラー。  
  
-   **後続のゼロ。** Visual Basic では後続の 0 を格納しません、`Decimal`リテラル。 ただし、`Decimal`変数には、計算に必要なすべての後続のゼロが保持されます。 次に例を示します。  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     出力`MsgBox`前の例では、次のようにします。  
  
     d1 2.375、d2 の = = 1.625、d3 4.000、d4 を = = 4  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `D` を付けると、そのリテラルは `Decimal` に変換されます。 ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 (`Decimal`) に変換されます。  
  
-   **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Decimal?displayProperty=nameWithType> 構造体です。  
  
## <a name="range"></a>範囲  
 使用する必要があります、`D`文字入力すると大きな値を割り当てる、`Decimal`変数または定数。 この要件は、コンパイラがリテラルとして解釈されるので`Long`しない限り、リテラルの型文字以下、リテラルの例を次に示します。  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 宣言`bigDec1`に割り当てられている値の範囲内に収まるために、オーバーフローを生成しない`Long`します。 `Long`に値を割り当てることができます、`Decimal`変数。  
  
 宣言`bigDec2`用に割り当てられている値が大きすぎるために、オーバーフロー エラーが発生`Long`します。 数値リテラルとしてまず解釈できないため、`Long`に割り当てることができない、`Decimal`変数。  
  
 `bigDec3`、リテラルの型文字`D`としてリテラルを解釈するコンパイラを強制することで、問題を解決する`Decimal`の代わりとして、 `Long`。  
  
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

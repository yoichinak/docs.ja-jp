---
title: 整数型 (Integer)
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343983"
---
# <a name="integer-data-type-visual-basic"></a>Integer data type (Visual Basic)

-2,147,483,648 から 2,147,483,647 までの符号付き 32 ビット (4 バイト) の整数を保持します。  
  
## <a name="remarks"></a>Remarks

 `Integer` データ型は、32 ビットのプロセッサでパフォーマンスが最大になります。 他の整数型では、メモリとの間の読み込みと格納により長い時間がかかります。  
  
 `Integer` の既定値は 0 です。  

## <a name="literal-assignments"></a>Literal assignments

You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal. 整数リテラルが `Integer` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Integer` 値に割り当てられています。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal. 10 進リテラルには、プレフィックスはありません。

Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits. (例:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>プログラミングのヒント

- **Interop Considerations.** If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments. そのようなコンポーネントに 16 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 (`Integer`) ではなく短整数型 (`Short`) として宣言します。  
  
- **Widening.** `Integer` データ型は、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。 これは、`Integer` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **Type Characters.** あるリテラルにリテラルの型文字 `I` を付けると、そのリテラルは `Integer` に変換されます。 ある識別子に識別子の型文字 `%` を付けると、その識別子は整数型 (`Integer`) に変換されます。  
  
- **Framework Type.** .NET Framework において対応する型は、<xref:System.Int32?displayProperty=nameWithType> 構造体です。  
  
## <a name="range"></a>範囲

整数型の変数をその型の範囲外の数値に設定しようとすると、エラーが発生します。 小数に設定しようとすると、最も近い整数値に丸められます。 2 つの整数値に等しく近い場合は、最も近い偶数の整数に丸められます。 この処理により、常に中間値を単一方向に丸めるために発生する丸め誤差が最小限に抑えられます。 丸めの例を次のコードに示します。  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>関連項目

- <xref:System.Int32?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

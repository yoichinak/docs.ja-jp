---
title: Short 型
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343937"
---
# <a name="short-data-type-visual-basic"></a>Short data type (Visual Basic)

Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.  
  
## <a name="remarks"></a>Remarks  

 Use the `Short` data type to contain integer values that do not require the full data width of `Integer`. In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.  
  
 `Short` の既定値は 0 です。  
  
## <a name="literal-assignments"></a>Literal assignments

You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal. 整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal. 10 進リテラルには、プレフィックスはありません。

Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits. (例:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>プログラミングのヒント

- **Widening.** The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`. これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **Type Characters.** あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。 `Short` has no identifier type character.  
  
- **Framework Type.** .NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Int16?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

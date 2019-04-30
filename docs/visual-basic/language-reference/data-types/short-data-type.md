---
title: Short 型 (Visual Basic)
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
ms.openlocfilehash: d4dab1a72d1e240bc428b2c6b83a722584e35ecc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971796"
---
# <a name="short-data-type-visual-basic"></a>Short データ型 (Visual Basic)
符号付き 16 ビット (2 バイト) 整数-32,768 32,767 の範囲です。  
  
## <a name="remarks"></a>Remarks  
 使用して、`Short`データ型の完全なデータの幅を必要としない整数値を含む`Integer`します。 場合によっては、共通言語ランタイムをパックできます、`Short`変数、緊密に協力し、メモリ消費量を保存します。  
  
 `Short` の既定値は 0 です。  
  
## <a name="literal-assignments"></a>リテラルの割り当て

宣言し、初期化を`Short`10 進リテラル、16 進リテラル、8 進数のリテラルを割り当てることや (Visual Basic 2017 以降) バイナリ リテラルでは、変数。 整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数が 16 進数、10 進数として表される 1,034 に等しくなりからのバイナリ リテラルを暗黙的に変換されます[整数](integer-data-type.md)に`Short`値。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`を 16 進リテラル、プレフィックスを示すために`&b`または`&B`、バイナリ リテラル、およびプレフィックスを示すために`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますも、アンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、 `S` [文字入力](../../programming-guide/language-features/data-types/type-characters.md)を示すために、`Short`データ型は、次の例を示します。

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>プログラミングのヒント

- **拡大します。** `Short`拡大変換後のデータ型`Integer`、 `Long`、 `Decimal`、 `Single`、または`Double`します。 これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **型宣言文字。** あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。 `Short` 識別子の型文字がありません。  
  
- **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Int16?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

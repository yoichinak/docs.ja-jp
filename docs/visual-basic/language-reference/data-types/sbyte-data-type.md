---
title: SByte 型 (Visual Basic)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 1da5de4971928ca23a23c4dcfc5f338c4d7a3875
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971783"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte データ型 (Visual Basic)

符号付き-128 から 127 までの範囲の 8 ビット (1 バイト) の整数を保持します。  
  
## <a name="remarks"></a>Remarks

使用して、`SByte`データ型の完全なデータの幅を必要としない整数値を含む`Integer`のデータの半分の幅も`Short`します。 場合によっては、共通言語ランタイムでをパックできる場合があります、`SByte`変数、緊密に協力し、メモリ消費量を保存します。

`SByte` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て
  
宣言し、初期化を`SByte`10 進リテラル、16 進リテラル、8 進数のリテラルを割り当てることや (Visual Basic 2017 以降) バイナリ リテラルでは、変数。

次の例では、整数が 16 進数、10 進数として表される-102 に等しくなりに割り当てられているバイナリ リテラル`SByte`値。 この例では、使用してコンパイルする必要があります、`/removeintchecks`コンパイラ スイッチ。

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> プレフィックスを使用する`&h`または`&H`を 16 進リテラル、プレフィックスを示すために`&b`または`&B`、バイナリ リテラル、およびプレフィックスを示すために`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますも、アンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

整数リテラルが `SByte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.SByte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。 整数リテラルには、サフィックスがあるないとき、[整数](integer-data-type.md)推論されます。 整数リテラルの範囲外の場合、`Integer`の種類、[長い](long-data-type.md)推論されます。 つまり、前の例では、数値リテラルで`0x9A`と`0b10011010`を超える値が、156 の 32 ビット符号付き整数として解釈される<xref:System.SByte.MaxValue?displayProperty=nameWithType>します。 10 進数以外の整数を代入するこのようなコードをコンパイルする、`SByte`次のいずれかを行うことができます。

- コンパイルする整数の範囲チェックを無効にする、`/removeintchecks`コンパイラ スイッチ。

- 使用して、[文字入力](../../programming-guide/language-features/data-types/type-characters.md)に割り当てるリテラルの値を明示的に定義する、`SByte`します。 次の例では、負の値のリテラル`Short`値を`SByte`します。 負の数値に注意してください、数値リテラルの上位の単語の上位ビットを設定する必要があります。 このビットの場合はこの例では、リテラルの 15`Short`値。

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>プログラミングのヒント
  
- **CLS 準拠です。** `SByte`データ型がの一部、[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) に CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。

- **拡大します。** `SByte`拡大変換後のデータ型`Short`、 `Integer`、 `Long`、 `Decimal`、 `Single`、および`Double`します。 つまり、変換できる`SByte`遭遇することがなくこれらの型のいずれにも、<xref:System.OverflowException?displayProperty=nameWithType>エラー。
  
- **型宣言文字。** `SByte` リテラルの型文字または識別子の型文字がありません。  
  
- **フレームワークの型。** .NET Framework において対応する型は、<xref:System.SByte?displayProperty=nameWithType> 構造体です。
  
## <a name="see-also"></a>関連項目

- <xref:System.SByte?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

---
title: SByte 型
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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401383"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte データ型

-128 から 127 までの範囲の符号付き 8 ビット (1 バイト) 整数を保持します。

## <a name="remarks"></a>解説

データ型`SByte`を使用して、データの幅全体を必要としない整数値、または`Integer`の半分のデータ幅を`Short`含めるには、 を使用します。 場合によっては、共通言語ランタイムが変数を密接にパックし、メモリ`SByte`消費量を節約できる場合があります。

`SByte` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラル代入

変数を`SByte`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。

次の例では、10 進数、16 進数、およびバイナリ リテラルとして表される -102 に`SByte`等しい整数が値に割り当てられます。 この例では、コンパイラ スイッチを`/removeintchecks`使用してコンパイルする必要があります。

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

整数リテラルが `SByte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.SByte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。 整数リテラルにサフィックスがない場合、[整数](integer-data-type.md)は推論されます。 整数リテラルが`Integer`型の範囲外の場合は、[長整数](long-data-type.md)型が推論されます。 つまり、前の例では、数値リテラル`0x9A`と`0b10011010`、値が 156 の 32 ビット符号付き整数として解釈されます。 <xref:System.SByte.MaxValue?displayProperty=nameWithType> このようなコードを正常にコンパイルして、10 進以外の整数を`SByte`に割り当てるには、次のいずれかの操作を行います。

- コンパイラ スイッチを使用してコンパイルすることにより、整数`/removeintchecks`の境界チェックを無効にします。

- [型文字](../../programming-guide/language-features/data-types/type-characters.md)を使用して、に割り当てるリテラル値を明示的に定義します`SByte`。 次の例では、負のリテラル`Short`値をに`SByte`代入します。 負の数の場合は、数値リテラルの上位ワードの上位ビットを設定する必要があります。 この例の場合、これはリテラル`Short`値のビット 15 です。

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>プログラミングのヒント

- **CLS コンプライアンス。** データ`SByte`型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) の一部ではないため、CLS 準拠のコードで使用するコンポーネントを使用することはできません。

- **拡大。** データ`SByte`型は`Short`、 、 `Integer`、 `Long` `Decimal`、 `Single`、 `Double`、 、 、 にまで広がります。 つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`SByte`することなく、これらの型に変換できます。

- **文字を入力します。** `SByte`リテラル型文字または識別子型文字がありません。

- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.SByte?displayProperty=nameWithType> 構造体です。

## <a name="see-also"></a>関連項目

- <xref:System.SByte?displayProperty=nameWithType>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

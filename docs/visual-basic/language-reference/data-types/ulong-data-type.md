---
title: ULong データ型
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401317"
---
# <a name="ulong-data-type-visual-basic"></a>ULong データ型

0 から 18,446,744,073,709,551,615 (1.84 倍以上 10 ^ 19) の範囲の符号なし 64 ビット (8 バイト) 整数を保持します。

## <a name="remarks"></a>解説

データ型`ULong`を使用して、バイナリ データが大`UInteger`きすぎて に対しては大きすぎたか、または最大の符号なし整数値を含めることができます。

`ULong` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラル代入

変数を`ULong`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが `ULong` の範囲外にある場合 (つまり、<xref:System.UInt64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 7,934,076,125 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`ULong` 値に割り当てられています。

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

次の例に示すように、`UL`数値`ul`リテラルには`ULong`、データ型を示す[or 型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めることもできます。

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>プログラミングのヒント

- **負の数。** 符号`ULong`なしの型であるため、負の数を表すことはできません。 型`-``ULong`と評価される式に単項マイナス ( ) 演算子を使用すると、その式が最初に`Decimal`変換されます。

- **CLS コンプライアンス。** データ`ULong`型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) の一部ではないため、CLS 準拠のコードで使用するコンポーネントを使用することはできません。

- **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとインターフェイスを使用している場合は、他`ulong`の環境ではデータ幅 (32 ビット) が異なる型が使用される場合があります。 このようなコンポーネントに 32 ビットの引数を渡す場合は、マネージ`UInteger`Visual `ULong` Basic コードではなく、それを宣言します。

  さらに、オートメーションは、Windows 95、Windows 98、Windows ME、または Windows 2000 では 64 ビットの整数をサポートしていません。 これらのプラットフォームでは、Visual `ULong` Basic の引数をオートメーション コンポーネントに渡すことはできません。

- **拡大。** データ`ULong`型は`Decimal`、 、 `Single`、 `Double`、 、 に拡大されます。 つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`ULong`することなく、これらの型に変換できます。

- **文字を入力します。** リテラルにリテラルの型文字`UL`を追加すると、データ型に`ULong`強制的に追加されます。 `ULong`識別子の種類の文字がありません。

- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.UInt64?displayProperty=nameWithType> 構造体です。

## <a name="see-also"></a>関連項目

- <xref:System.UInt64>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

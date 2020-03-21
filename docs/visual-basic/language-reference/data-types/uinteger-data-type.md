---
title: UInteger 型
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401377"
---
# <a name="uinteger-data-type"></a>UInteger データ型

0 から 4,294,967,295 までの範囲の符号なし 32 ビット (4 バイト) 整数を保持します。

## <a name="remarks"></a>解説

データ`UInteger`型は、最も効率的なデータ幅で最大の符号なし値を提供します。

`UInteger` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラル代入

変数を`UInteger`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが `UInteger` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`UInteger` 値に割り当てられています。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

次の例に示すように、`UI`数値`ui`リテラルには`UInteger`、データ型を示す[or 型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めることもできます。

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>プログラミングのヒント

`Integer`および`UInteger`データ型は、使用するビット数が少なくても、より少ない整数型 (`UShort` `Short`、 `Byte`、 `SByte`、 、 ) が読み込み、格納、およびフェッチに時間がかかるため、32 ビット プロセッサで最適なパフォーマンスを提供します。

- **負の数。** 符号`UInteger`なしの型であるため、負の数を表すことはできません。 型`-``UInteger`と評価される式に単項マイナス ( ) 演算子を使用すると、その式が最初に`Long`変換されます。

- **CLS コンプライアンス。** データ`UInteger`型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) の一部ではないため、CLS 準拠のコードで使用するコンポーネントを使用することはできません。

- **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとインターフェイスを使用している場合は、他`uint`の環境ではデータ幅 (16 ビット) が異なる型が使用される場合があります。 このようなコンポーネントに 16 ビットの引数を渡す場合は、マネージ`UShort`Visual `UInteger` Basic コードではなく、それを宣言します。

- **拡大。** データ`UInteger`型は`Long`、 、 `ULong`、 `Decimal` `Single`、 `Double`、 、 、 にまで広がります。 つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`UInteger`することなく、これらの型に変換できます。

- **文字を入力します。** リテラルにリテラルの型文字`UI`を追加すると、データ型に`UInteger`強制的に追加されます。 `UInteger`識別子の種類の文字がありません。

- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.UInt32?displayProperty=nameWithType> 構造体です。

## <a name="see-also"></a>関連項目

- <xref:System.UInt32>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

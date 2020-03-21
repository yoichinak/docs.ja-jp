---
title: UShort データ型
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401311"
---
# <a name="ushort-data-type-visual-basic"></a>データ型を短くする

0 から 65,535 までの範囲の符号なし 16 ビット (2 バイト) 整数を保持します。  
  
## <a name="remarks"></a>解説

 データ型`UShort`を使用して、バイナリ データが大`Byte`きすぎて.  
  
 `UShort` の既定値は 0 です。  

## <a name="literal-assignments"></a>リテラル代入

変数を`UShort`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが `UShort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、10 進数、16 進数、およびバイナリ リテラルとして表される 65,034 に`UShort`等しい整数が値に割り当てられます。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

次の例に示すように、`US`数値`us`リテラルには`UShort`、データ型を示す[or 型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めることもできます。

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>プログラミングのヒント
  
- **負の数。** 符号`UShort`なしの型であるため、負の数を表すことはできません。 型`-``UShort`と評価される式に単項マイナス ( ) 演算子を使用すると、その式が最初に`Integer`変換されます。  
  
- **CLS コンプライアンス。** データ`UShort`型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) の一部ではないため、CLS 準拠のコードで使用するコンポーネントを使用することはできません。
  
- **拡大。** データ`UShort`型は`Integer`、 、 `UInteger`、 `Long` `ULong`、 `Decimal` `Single`、 `Double`、 、 、 、 にまで広がります。 つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`UShort`することなく、これらの型に変換できます。  
  
- **文字を入力します。** リテラルにリテラルの型文字`US`を追加すると、データ型に`UShort`強制的に追加されます。 `UShort`識別子の種類の文字がありません。  
  
- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.UInt16?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.UInt16>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

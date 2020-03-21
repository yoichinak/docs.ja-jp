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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401341"
---
# <a name="short-data-type-visual-basic"></a>短いデータ型

-32,768 から 32,767 までの範囲の符号付き 16 ビット (2 バイト) 整数を保持します。  
  
## <a name="remarks"></a>解説  

 データ型`Short`を使用して、データの幅全体を必要としない整数値を格納`Integer`します。 場合によっては、共通言語ランタイムによって変数をまとめて格納し`Short`、メモリ消費量を節約できる場合があります。  
  
 `Short` の既定値は 0 です。  
  
## <a name="literal-assignments"></a>リテラル代入

変数を`Short`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、10 進数、16 進数、およびバイナリ リテラルとして表される 1,034 に等しい整数は`Short`[、Integer](integer-data-type.md)から値に暗黙的に変換されます。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

次の例に示すように、`S`数値リテラルにはデータ型を`Short`示す[型文字](../../programming-guide/language-features/data-types/type-characters.md)も含めることができます。

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>プログラミングのヒント

- **拡大。** データ`Short`型は`Integer`、 、 `Long`、 `Decimal` `Single`、 `Double`、 、または に拡大されます。 これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **文字を入力します。** あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。 `Short`識別子の種類の文字がありません。  
  
- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Int16?displayProperty=nameWithType>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

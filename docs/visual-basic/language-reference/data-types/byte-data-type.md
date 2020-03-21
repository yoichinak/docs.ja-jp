---
title: バイト型 (Byte)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401353"
---
# <a name="byte-data-type-visual-basic"></a>バイト データ型

0 から 255 までの範囲の符号なし 8 ビット (1 バイト) 整数を保持します。

## <a name="remarks"></a>解説

バイナリ`Byte`データを格納するには、データ型を使用します。  
  
`Byte` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラル代入

変数を`Byte`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが a`Byte`の範囲外の場合 (つまり、それより小さい<xref:System.Byte.MinValue?displayProperty=nameWithType>かそれより大<xref:System.Byte.MaxValue?displayProperty=nameWithType>きい場合)、コンパイル エラーが発生します。

次の例では、10 進数、16 進数、およびバイナリ リテラルとして表される 201 の整数は[、Integer](integer-data-type.md)から値に`byte`暗黙的に変換されます。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>プログラミングのヒント

- **負の数。** 符号`Byte`なしの型であるため、負の数を表すことはできません。 型`-``Byte`と評価される式に単項マイナス ( ) 演算子を使用すると、その式が最初に`Short`変換されます。
  
- **変換の書式設定。** Visual Basic では、ファイルの読み取りまたは書き込みを行うとき、または DLL、メソッド、およびプロパティを呼び出すときに、データ形式間で自動的に変換できます。 変数や配列に`Byte`格納されたバイナリデータは、このようなフォーマット変換中に保持されます。 ANSI 形式`String`と Unicode 形式の変換中に、その内容が破損する可能性があるため、バイナリ データには変数を使用しないでください。

- **拡大。** データ`Byte`型`Short`は、 、 `UShort`、 `Integer` `UInteger`、 `Long` `ULong`、 `Decimal` `Single`、 `Double`、 、 、 、 、 、 、 に拡大されます。 つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`Byte`することなく、これらの型に変換できます。
  
- **文字を入力します。** `Byte`リテラル型文字または識別子型文字がありません。

- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.Byte?displayProperty=nameWithType> 構造体です。

## <a name="example"></a>例

 次の例では、`b`変数です`Byte`。 このステートメントは、変数の範囲と、それに対するビットシフト演算子の適用を示します。

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>関連項目

- <xref:System.Byte?displayProperty=nameWithType>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

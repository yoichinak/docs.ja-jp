---
title: 文字型 (Char) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512792"
---
# <a name="char-data-type-visual-basic"></a>文字型 (Char) (Visual Basic)

0 ~ 65535 の値の範囲内の符号なし16ビット (2 バイト) コードポイントを保持します。 各*コードポイント*(文字コード) は、1つの Unicode 文字を表します。

## <a name="remarks"></a>Remarks

1つ`Char`の文字だけを保持する必要があり、の`String`オーバーヘッドを必要としない場合は、データ型を使用します。 場合によっては、 `Char()`要素の`Char`配列を使用して、複数の文字を保持できます。

の`Char`既定値は、コードポイントが0の文字です。

## <a name="unicode-characters"></a>Unicode 文字

Unicode の最初の128コードポイント (0 ~ 127) は、標準の U.S. キーボードの文字と記号に対応しています。 これらの最初の128コードポイントは、ASCII 文字セットで定義されているものと同じです。 2番目の128コードポイント (128 ~ 255) は、ラテン語に基づくアルファベット文字、アクセント、通貨記号、分数などの特殊文字を表します。 Unicode では、世界中のコードポイント (256-65535) を使用して、世界中のテキスト文字、分音記号、数学記号、技術記号などのさまざまなシンボルを使用します。

変数にや<xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A>などのメソッドを使用して、Unicode 分類を決定することができます。 `Char`

## <a name="type-conversions"></a>型変換

Visual Basic は、と数値型`Char`の間で直接変換されません。 関数<xref:Microsoft.VisualBasic.Strings.Asc%2A>または<xref:Microsoft.VisualBasic.Strings.AscW%2A>関数を使用すると、 `Char`そのコードポイント`Integer`を表すに値を変換できます。 関数<xref:Microsoft.VisualBasic.Strings.Chr%2A>または<xref:Microsoft.VisualBasic.Strings.ChrW%2A>関数を使用すると、 `Integer`そのコードポイント`Char`を持つに値を変換できます。

型チェックスイッチ ([Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)) がオンになっている場合は、リテラル型の文字を`Char`データ型として識別するために、1文字の文字列リテラルに追加する必要があります。 次に例を示します。

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a>プログラミングのヒント

- **負の数値。** `Char`は符号なしの型であり、負の値を表すことはできません。 どのような場合でも、を`Char`使用して数値を保持することはできません。

- **相互運用に関する考慮事項。** .NET Framework 用に作成されていないコンポーネント (オートメーションや COM オブジェクトなど) とのインターフェイスを使用する場合は、文字型のデータ幅が異なる (8 ビット) ことに注意してください。 このようなコンポーネントに8ビットの引数を渡す場合は、新しい Visual Basic `Byte`コードで`Char`ではなく、として宣言します。

- **広げ.** データ`Char`型はに`String`拡大変換されます。 これは、に`Char` `String`変換でき<xref:System.OverflowException?displayProperty=nameWithType> 、エラーが発生しないことを意味します。

- **文字を入力します。** リテラル型の文字`C`を1文字の文字列リテラルに追加すると、強制的`Char`にデータ型になります。 `Char`に識別子の型文字がありません。

- **フレームワークの種類。** .NET Framework において対応する型は、<xref:System.Char?displayProperty=nameWithType> 構造体です。

## <a name="see-also"></a>関連項目

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法: 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

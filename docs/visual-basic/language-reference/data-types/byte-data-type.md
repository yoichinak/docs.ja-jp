---
title: バイト型 (Byte) (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 217778a21fb9f231f448436ca5a68c42e5837566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797008"
---
# <a name="byte-data-type-visual-basic"></a>Byte データ型 (Visual Basic)
0 から 255 までの範囲の符号なし 8 ビット (1 バイト) 整数を保持します。

## <a name="remarks"></a>Remarks

使用して、`Byte`バイナリ データを格納するデータ型。  
  
`Byte` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て

宣言し、初期化を`Byte`10 進リテラル、16 進リテラル、8 進数のリテラルを割り当てることや (Visual Basic 2017 以降) バイナリ リテラルでは、変数。 整数リテラルの範囲外の場合、 `Byte` (である場合より小さい<xref:System.Byte.MinValue?displayProperty=nameWithType>以上<xref:System.Byte.MaxValue?displayProperty=nameWithType>)、コンパイル エラーが発生します。

次の例では、整数が 16 進数、10 進数として表される 201 に等しくなりからのバイナリ リテラルを暗黙的に変換されます[整数](integer-data-type.md)に`byte`値。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`を 16 進リテラル、プレフィックスを示すために`&b`または`&B`、バイナリ リテラル、およびプレフィックスを示すために`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますも、アンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>プログラミングのヒント

- **負の数。** `Byte`符号なしの型は、負の数を表すことはできません。 単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`Byte`、Visual Basic の式を変換する`Short`最初。
  
- **形式の変換。** Visual Basic の読み取りまたはファイルの書き込み時に、または Dll、メソッド、およびプロパティを呼び出すときは、データ形式間で自動的に変換できます。 格納されているバイナリ データ`Byte`変数および配列はこのような形式の変換中に保持されます。 使用しないようにする、 `String` ANSI および Unicode 形式の間で変換中にその内容が破損することがあるため、バイナリ データ変数。

- **拡大します。** `Byte`拡大変換後のデータ型`Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、または`Double`します。 つまり、変換できる`Byte`遭遇することがなくこれらの型のいずれにも、<xref:System.OverflowException?displayProperty=nameWithType>エラー。
  
- **型宣言文字。** `Byte` リテラルの型文字または識別子の型文字がありません。

- **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Byte?displayProperty=nameWithType> 構造体です。

## <a name="example"></a>例

 次の例では、`b`は、`Byte`変数。 ステートメントは、変数の範囲とビット シフト演算子のアプリケーションを示します。

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>関連項目

- <xref:System.Byte?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

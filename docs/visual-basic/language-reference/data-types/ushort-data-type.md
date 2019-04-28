---
title: UShort 型 (Visual Basic)
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
ms.openlocfilehash: 8845a6bde4e1a701b5420029788259724cd0f8d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748761"
---
# <a name="ushort-data-type-visual-basic"></a>UShort データ型 (Visual Basic)

保留符号なし 16 ビット (2 バイト) 整数 0 から 65,535 までの範囲します。  
  
## <a name="remarks"></a>Remarks

 使用して、`UShort`データ型に対して大きすぎますバイナリ データを格納する`Byte`します。  
  
 `UShort` の既定値は 0 です。  

## <a name="literal-assignments"></a>リテラルの割り当て

宣言し、初期化を`UShort`10 進リテラル、16 進リテラル、8 進数のリテラルを割り当てることや (Visual Basic 2017 以降) バイナリ リテラルでは、変数。 整数リテラルが `UShort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数が 16 進数、10 進数として表される 65, 034 を等しくなりに割り当てられているバイナリ リテラル`UShort`値。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`を 16 進リテラル、プレフィックスを示すために`&b`または`&B`、バイナリ リテラル、およびプレフィックスを示すために`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますも、アンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、`US`または`us`[文字入力](../../programming-guide/language-features/data-types/type-characters.md)を示すために、`UShort`データ型は、次の例を示します。

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>プログラミングのヒント
  
- **負の数。** `UShort`符号なしの型は、負の数を表すことはできません。 単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`UShort`、Visual Basic の式を変換する`Integer`最初。  
  
- **CLS 準拠です。** `UShort`データ型がの一部、[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) に CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。
  
- **拡大します。** `UShort`拡大変換後のデータ型`Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、および`Double`します。 つまり、変換できる`UShort`遭遇することがなくこれらの型のいずれにも、<xref:System.OverflowException?displayProperty=nameWithType>エラー。  
  
- **型宣言文字。** リテラルの型文字を付加`US`リテラルに強制的に、`UShort`データ型。 `UShort` 識別子の型文字がありません。  
  
- **フレームワークの型。** .NET Framework において対応する型は、<xref:System.UInt16?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.UInt16>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法: 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

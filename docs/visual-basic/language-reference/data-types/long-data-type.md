---
title: Long データ型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: ca0f95342783d22559761294ccea6056cd3e4fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918451"
---
# <a name="long-data-type-visual-basic"></a>Long データ型 (Visual Basic)

符号付き 64 ビット (8 バイト) の整数 9,223,372,036,854,775,807-9,223,372,036,854,775,808 から値までの保持 (9.2... E + 18)。  
  
## <a name="remarks"></a>Remarks

 使用して、`Long`が大きすぎてに収まるように整数値を格納するデータ型、`Integer`データ型。  
  
 `Long` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て 

宣言し、初期化を`Long`10 進リテラル、16 進リテラル、8 進数のリテラルを割り当てることや (Visual Basic 2017 以降) バイナリ リテラルでは、変数。 整数リテラルが `Long` の範囲外にある場合 (つまり、<xref:System.Int64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Long` 値に割り当てられています。
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`を 16 進リテラル、プレフィックスを示すために`&b`または`&B`、バイナリ リテラル、およびプレフィックスを示すために`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますも、アンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、 `L` [文字入力](../../programming-guide/language-features/data-types/type-characters.md)を示すために、`Long`データ型は、次の例を示します。

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>プログラミングのヒント

- **相互運用の考慮事項。** .NET Framework、例のオートメーションまたは COM オブジェクト用に作成されていないコンポーネントとやり取りする場合に注意している`Long`に他の環境は別のデータ幅 (32 ビット)。 このようなコンポーネントに 32 ビットの引数を渡す場合の宣言として`Integer`の代わりに`Long`で新しい Visual Basic コードです。  
  
- **拡大します。** `Long`拡大変換後のデータ型`Decimal`、 `Single`、または`Double`します。 これは、`Long` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **型宣言文字。** あるリテラルにリテラルの型文字 `L` を付けると、そのリテラルは `Long` に変換されます。 ある識別子に識別子の型文字 `&` を付けると、その識別子は整数型 (`Long`) に変換されます。  
  
- **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Int64?displayProperty=nameWithType> 構造体です。  

## <a name="see-also"></a>関連項目

- <xref:System.Int64>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Integer データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

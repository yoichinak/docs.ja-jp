---
title: '`Integer` データ型 (Visual Basic)'
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: b0d24027f00c4ab4ba49f4948a9f5488a2eff3fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054407"
---
# <a name="integer-data-type-visual-basic"></a>`Integer` データ型 (Visual Basic)
-2,147,483,648 から 2,147,483,647 までの符号付き 32 ビット (4 バイト) の整数を保持します。  
  
## <a name="remarks"></a>Remarks
 `Integer` データ型は、32 ビットのプロセッサでパフォーマンスが最大になります。 他の整数型では、メモリとの間の読み込みと格納により長い時間がかかります。  
  
 `Integer` の既定値は 0 です。  

## <a name="literal-assignments"></a>リテラルの割り当て

宣言し、初期化を`Integer`10 進リテラル、16 進リテラル、8 進数のリテラルを割り当てることや (Visual Basic 2017 以降) バイナリ リテラルでは、変数。 整数リテラルが `Integer` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Integer` 値に割り当てられています。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`を 16 進リテラル、プレフィックスを示すために`&b`または`&B`、バイナリ リテラル、およびプレフィックスを示すために`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますも、アンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Visual Basic 15.5 以降では、使用することできますもアンダー スコア文字 (`_`) プレフィックスと 16 進数、バイナリ、または 8 進数の桁の間の先頭の区切り記号として。 例:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、 `I` [文字入力](../../programming-guide/language-features/data-types/type-characters.md)を示すために、`Integer`データ型は、次の例を示します。

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>プログラミングのヒント

- **相互運用の考慮事項。** オートメーションまたは COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合に注意している`Integer`に他の環境は別のデータ幅 (16 ビット)。 そのようなコンポーネントに 16 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 (`Integer`) ではなく短整数型 (`Short`) として宣言します。  
  
- **拡大します。** `Integer` データ型は、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。 これは、`Integer` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **型宣言文字。** あるリテラルにリテラルの型文字 `I` を付けると、そのリテラルは `Integer` に変換されます。 ある識別子に識別子の型文字 `%` を付けると、その識別子は整数型 (`Integer`) に変換されます。  
  
- **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Int32?displayProperty=nameWithType> 構造体です。  
  
## <a name="range"></a>範囲

整数型の変数をその型の範囲外の数値に設定しようとすると、エラーが発生します。 小数に設定しようとすると、最も近い整数値に丸められます。 2 つの整数値に等しく近い場合は、最も近い偶数の整数に丸められます。 この処理により、常に中間値を単一方向に丸めるために発生する丸め誤差が最小限に抑えられます。 丸めの例を次のコードに示します。  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>関連項目

- <xref:System.Int32?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

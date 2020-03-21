---
title: 整数型 (Integer)
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
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401347"
---
# <a name="integer-data-type-visual-basic"></a>整数データ型

-2,147,483,648 から 2,147,483,647 までの符号付き 32 ビット (4 バイト) の整数を保持します。  
  
## <a name="remarks"></a>解説

 `Integer` データ型は、32 ビットのプロセッサでパフォーマンスが最大になります。 他の整数型では、メモリとの間の読み込みと格納により長い時間がかかります。  
  
 `Integer` の既定値は 0 です。  

## <a name="literal-assignments"></a>リテラル代入

変数を`Integer`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが `Integer` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Integer` 値に割り当てられています。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

次の例に示すように、`I`数値リテラルにはデータ型を`Integer`示す[型文字](../../programming-guide/language-features/data-types/type-characters.md)も含めることができます。

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>プログラミングのヒント

- **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとの間に`Integer`インターフェイスを設定している場合は、他の環境ではデータ幅 (16 ビット) が異なっていることを覚えておいてください。 そのようなコンポーネントに 16 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 (`Integer`) ではなく短整数型 (`Short`) として宣言します。  
  
- **拡大。** `Integer` データ型は、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。 これは、`Integer` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
- **文字を入力します。** あるリテラルにリテラルの型文字 `I` を付けると、そのリテラルは `Integer` に変換されます。 ある識別子に識別子の型文字 `%` を付けると、その識別子は整数型 (`Integer`) に変換されます。  
  
- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.Int32?displayProperty=nameWithType> 構造体です。  
  
## <a name="range"></a>Range

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
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

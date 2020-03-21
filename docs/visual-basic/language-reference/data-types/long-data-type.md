---
title: Long 型
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
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401401"
---
# <a name="long-data-type-visual-basic"></a>長いデータ型

符号付き 64 ビット (8 バイト) の整数を保持し、-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 (9.2.E+18) までの範囲の整数を保持します。

## <a name="remarks"></a>解説

データ型`Long`に収まらない大きな整数を格納するには、データ型を`Integer`使用します。

`Long` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラル代入

変数を`Long`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。 整数リテラルが `Long` の範囲外にある場合 (つまり、<xref:System.Int64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Long` 値に割り当てられています。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。 次に例を示します。

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

次の例に示すように、`L`数値リテラルにはデータ型を`Long`示す[型文字](../../programming-guide/language-features/data-types/type-characters.md)も含めることができます。

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>プログラミングのヒント

- **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとインターフェイスを使用`Long`している場合は、他の環境ではデータ幅 (32 ビット) が異なっていることを覚えておいてください。 このようなコンポーネントに 32 ビットの引数を渡す場合は、新しい`Integer`Visual `Long` Basic コードではなく、それを宣言します。

- **拡大。** データ`Long`型は`Decimal`、 、 `Single`、 `Double`、 または に拡大されます。 これは、`Long` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。

- **文字を入力します。** あるリテラルにリテラルの型文字 `L` を付けると、そのリテラルは `Long` に変換されます。 ある識別子に識別子の型文字 `&` を付けると、その識別子は整数型 (`Long`) に変換されます。

- **Framework のデータ型** .NET Framework において対応する型は、<xref:System.Int64?displayProperty=nameWithType> 構造体です。

## <a name="see-also"></a>関連項目

- <xref:System.Int64>
- [データ型](../../../visual-basic/language-reference/data-types/index.md)
- [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

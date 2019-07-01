---
title: float キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: db0139f2000c1bc2c5a13a3a542164201e73f0fb
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424210"
---
# <a name="float-c-reference"></a>float (C# リファレンス)

`float` キーワードは、32 ビット浮動小数点値を格納する単純な型を示します。 次の表では、`float` 型の有効桁数とおおよその範囲を示します。

|型|おおよその範囲|有効桁数|.NET 型|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|±1.5 x 10<sup>−45</sup> から ±3.4 x 10<sup>38</sup>|~6 ～9 桁|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a>リテラル

既定では、代入演算子の右辺にある実数値リテラルは、[double](double.md) として扱われます。 したがって、float 変数を初期化するには、次の例のように、サフィックス `f` または `F` を使います。

```csharp
float x = 3.5F;
```

前の宣言でサフィックスを使わないと、[double](double.md) 値を `float` 変数に保存しようとするため、コンパイル エラーが発生します。

## <a name="conversions"></a>変換

整数型と浮動小数点型を 1 つの式の中の混在させることができます。 この場合、整数型が浮動小数点型に変換されます。 式の評価は、次の規則に従って実行されます。

- 浮動小数点型の 1 つが [double](double.md) の場合、式は [double](double.md) または [bool](bool.md) (リレーショナル比較または等価比較の場合) と評価されます。

- 式に [double](double.md) 型が含まれない場合は、式は `float` または [bool](bool.md) (リレーショナル比較または等価比較の場合) と評価されます。

浮動小数点式は、次の値のセットを含むことができます。

- 正および負のゼロ

- 正および負の無限大

- Not-a-Number (NaN) 値

- ゼロ以外の値の有限のセット

これらの値について詳しくは、[IEEE](https://www.ieee.org) の Web サイトで入手できるバイナリ浮動小数点演算の IEEE 標準に関する資料をご覧ください。

## <a name="example"></a>例

次の例では、[int](../builtin-types/integral-numeric-types.md)、[short](../builtin-types/integral-numeric-types.md)、`float` が算術式に含まれ、`float` の結果を提供します。 (`float` は <xref:System.Single?displayProperty=nameWithType> 型のエイリアスです。)式には [double](double.md) が存在しないことに注意してください。

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- <xref:System.Single>
- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [キャストと型変換](../../programming-guide/types/casting-and-type-conversions.md)
- [C# のキーワード](index.md)
- [整数型](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [組み込み型の一覧表](built-in-types-table.md)
- [暗黙的な数値変換の一覧表](implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](explicit-numeric-conversions-table.md)

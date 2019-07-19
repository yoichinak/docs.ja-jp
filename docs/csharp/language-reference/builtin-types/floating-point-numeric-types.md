---
title: 浮動小数点数値型 - C# リファレンス
description: Overview of the built-in C# floating-point types (組み込みの C# 浮動小数点型の概要)
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664192"
---
# <a name="floating-point-numeric-types-c-reference"></a>浮動小数点数値型 (C# リファレンス)

**浮動小数点型**は**単純型**のサブセットであり、[*リテラル*](#floating-point-literals)を使用して初期化できます。 すべての浮動小数点型は値の型でもあります。 すべての浮動小数点数値型は、[算術](../operators/arithmetic-operators.md)の[比較および等値](../operators/equality-operators.md)演算子をサポートします。

次の表では、浮動小数点型の有効桁数とおおよその範囲を示します。
  
|型|おおよその範囲|有効桁数|  
|----------|-----------------------|---------------|  
|`float`|±1.5 x 10<sup>−45</sup> から ±3.4 x 10<sup>38</sup>|~6 ～9 桁|  
|`double`|±5.0 × 10<sup>−324</sup> - ±1.7 × 10<sup>308</sup>|~15-17 桁|  
|`decimal`|±1.0 x 10<sup>-28</sup> から ±7.9228 x 10<sup>28</sup>|28 から 29 桁の数字|  

すべての浮動小数点型の既定値は `0` です。 各浮動小数点型には、その型の最小値と最大値に対する `MinValue` と `MaxValue` という名前の定数があります。 `float` 型と `double` 型には、さらに `PositiveInfinity`、`NegativeInfinity`、および `NaN` の定数 ("数値ではない" 場合) があります。 `decimal` 型には、`Zero`、`One`、および`MinusOne` の定数が含まれています。

`decimal` 型は、`float` と `double` の両方よりも有効桁数が多く、範囲が狭いため、財務や金融の計算に適しています。

整数型と浮動小数点型を 1 つの式の中の混在させることができます。 この場合、整数型が浮動小数点型に変換されます。 式の評価は、次の規則に従って実行されます。

- 浮動小数点型の 1 つが `double` の場合、式は `double` または [bool](../keywords/bool.md) (リレーショナル比較または等価比較の場合) と評価されます。
- 式に `double` 型が含まれない場合は、式は `float` または [bool](../keywords/bool.md) (リレーショナル比較または等価比較の場合) と評価されます。

浮動小数点式は、次の値のセットを含むことができます。

- 正および負のゼロ
- 正および負の無限大
- Not-a-Number (NaN) 値
- ゼロ以外の値の有限のセット

これらの値について詳しくは、[IEEE](https://www.ieee.org) の Web サイトで入手できるバイナリ浮動小数点演算の IEEE 標準に関する資料をご覧ください。

浮動小数点値の書式指定には、[標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md)または[カスタムの数値書式指定文字列](../../../standard/base-types/custom-numeric-format-strings.md)のいずれかを使用できます。

## <a name="floating-point-literals"></a>浮動小数点リテラル

既定では、代入演算子の右側にある浮動小数点数リテラルは `double` として扱われます。 サフィックスを使用して、浮動小数点リテラルまたは整数リテラルを特定の型に変換できます。

- `d` または `D` サフィックスによって、リテラルは `double` に変換されます。
- `f` または `F` サフィックスによって、リテラルは `float` に変換されます。
- `m` または `M` サフィックスによって、リテラルは `decimal` に変換されます。

次の例は、各サフィックスを示しています。

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>変換

`float` から `double` への暗黙の変換があります (*拡大変換*と呼ばれます)。`float` 値の範囲は `double` の真部分集合であり、`float` から `double` に有効桁数の損失はないためです。 

ソース型からターゲット型への暗黙の型変換が定義されていない場合、ある浮動小数点型を別の浮動小数点型に変換するには、明示的なキャストを使用する必要があります。 これは*縮小変換*と呼ばれています。 変換によりデータが失われる場合があるため、明示的なケースが必要となります。 `decimal` 型は `float` または `double` よりも有効桁数が多いため、他の浮動小数点型と `decimal` 型の間の暗黙の変換はありません。

暗黙的な数値変換の詳細については、「[暗黙的な数値変換の一覧表](../keywords/implicit-numeric-conversions-table.md)」を参照してください。

明示的な数値変換の詳細については、「[明示的な数値変換の一覧表](../keywords/explicit-numeric-conversions-table.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [整数型](integral-numeric-types.md)
- [既定値の一覧表](../keywords/default-values-table.md)
- [数値結果テーブルの書式設定](../keywords/formatting-numeric-results-table.md)
- [組み込み型の一覧表](../keywords/built-in-types-table.md)
- [.NET における数値](../../../standard/numerics.md)
- [キャストと型変換](../../programming-guide/types/casting-and-type-conversions.md)
- [暗黙的な数値変換の一覧表](../keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)

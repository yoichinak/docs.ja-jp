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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002196"
---
# <a name="floating-point-numeric-types-c-reference"></a>浮動小数点数値型 (C# リファレンス)

**浮動小数点型**は**単純型**のサブセットであり、[*リテラル*](#floating-point-literals)を使用して初期化できます。 すべての浮動小数点型は値の型でもあります。 すべての浮動小数点数値型では、[算術](../operators/arithmetic-operators.md)、[比較、および等値](../operators/equality-operators.md)演算子がサポートされています。

## <a name="characteristics-of-the-floating-point-types"></a>浮動小数点型の特性

C# では、次の定義済みの浮動小数点型がサポートされています。
  
|C# 型/キーワード|おおよその範囲|Precision|Size|.NET 型|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1.5 x 10<sup>−45</sup> から ±3.4 x 10<sup>38</sup>|~6 ～9 桁|4 バイト|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5.0 × 10<sup>−324</sup> - ±1.7 × 10<sup>308</sup>|~15-17 桁|8 バイト|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1.0 x 10<sup>-28</sup> から ±7.9228 x 10<sup>28</sup>|28 から 29 桁の数字|16 バイト|<xref:System.Decimal?displayProperty=nameWithType>|

上の表の左端の列にある各 C# 型/キーワードは、対応する .NET 型の別名です。 これらは交換可能です。 たとえば、次の宣言では、同じ型の変数が宣言されています。

```csharp
double a = 12.3;
System.Double b = 12.3;
```

各浮動小数点型の既定値はゼロ `0` です。 各浮動小数点型には、その型の最小および最大有限値を指定する `MinValue` および `MaxValue` 定数があります。 `float` および `double` 型では、数字ではない値や無限値を表す定数も提供されています。 たとえば、`double` 型では、定数 <xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>、<xref:System.Double.PositiveInfinity?displayProperty=nameWithType> が提供されています。

`decimal` 型は、`float` と `double` の両方よりも有効桁数が多く、範囲が狭いため、財務や金融の計算に適しています。

[整数](integral-numeric-types.md)型と浮動小数点型を 1 つの式の中で混在させることができます。 この場合、整数型が浮動小数点型に変換されます。 式の評価は、次の規則に従って実行されます。

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
- [組み込み型の一覧表](../keywords/built-in-types-table.md)
- [.NET における数値](../../../standard/numerics.md)
- [キャストと型変換](../../programming-guide/types/casting-and-type-conversions.md)
- [暗黙的な数値変換の一覧表](../keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [数値結果テーブルの書式設定](../keywords/formatting-numeric-results-table.md)
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)

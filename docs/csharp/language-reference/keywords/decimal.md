---
title: decimal キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 7ad01f9e4f5a8b1a153b1ef306e9d6168335eb3d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424303"
---
# <a name="decimal-c-reference"></a>decimal (C# リファレンス)

`decimal` キーワードは、128 ビットのデータ型を示します。 `decimal` 型は、他の浮動小数点型よりも有効桁数が多く、範囲が狭いので、財務や金融の計算に適しています。 `decimal` 型の概算の範囲と有効桁数は、次のとおりです。

|型|おおよその範囲|有効桁数|.NET 型|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|±1.0 x 10<sup>-28</sup> から ±7.9228 x 10<sup>28</sup>|有効桁数 28 ～ 29|<xref:System.Decimal?displayProperty=nameWithType>|

`decimal` の既定値は 0m です。

## <a name="literals"></a>リテラル

実数値リテラルを `decimal` として扱うには、サフィックス m または M を使用します。次に例を示します。

```csharp
decimal myMoney = 300.5m;
```

サフィックス m がない場合は [double](../../../csharp/language-reference/keywords/double.md) として扱われ、コンパイラ エラーになります。

## <a name="conversions"></a>変換

整数型は、暗黙的に `decimal` に変換され、結果は `decimal` になります。 したがって、サフィックスなしで整数リテラルを使用して 10 進変数を初期化できます。次に例を示します。

```csharp
decimal myMoney = 300;
```

他の浮動小数点型と `decimal` 型の間に暗黙の型変換はありません。2 つの型の間で変換を実行するには、キャストを使用する必要があります。 次に例を示します。

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

`decimal` 型と数値の整数型を同じ式に混在させることもできます。 ただし、`decimal` 型と他の浮動小数点型をキャストなしで混在させると、コンパイル エラーになります。

暗黙的な数値変換の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。

明示的な数値変換の詳細については、「[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)」を参照してください。

## <a name="formatting-decimal-output"></a>10 進出力の書式指定

結果の書式を指定するには、`String.Format` メソッドを使用するか、<xref:System.Console.Write%2A?displayProperty=nameWithType> を呼び出す `String.Format()` メソッドを使用します。 通貨書式を指定するには、この記事の 2 番目の例に示されているように、標準の通貨の書式指定文字列である "C" または "c" を使用します。 `String.Format` メソッドの詳細については、<xref:System.String.Format%2A?displayProperty=nameWithType> を参照してください。

## <a name="example"></a>例

次の例では、[double](../../../csharp/language-reference/keywords/double.md) の変数と `decimal` の変数を加算しようとして、コンパイラ エラーが発生します。

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

実行の結果、次のエラーが生成されます。

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

この例では、同じ式に `decimal` と [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) が混在しています。 結果は `decimal` 型になります。

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>例

ここでは、通貨の書式指定文字列を使用して、出力の書式を指定する例を示します。 小数点以下の桁数が $0.99 を超えるため、`x` を丸めている点に注意してください。 変数 `y` は最大固定桁数を表し、正しい書式で正確に表示されます。

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- <xref:System.Decimal>
- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [整数型](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)

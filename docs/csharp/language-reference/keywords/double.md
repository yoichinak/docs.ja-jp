---
title: double キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: f4d6bb4eb698e4afbda6571ba382e828a5f836a4
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424259"
---
# <a name="double-c-reference"></a>double (C# リファレンス)

`double` キーワードは、64 ビット浮動小数点値を格納する単純な型を示します。 次の表では、`double` 型の有効桁数とおおよその範囲を示します。

|型|おおよその範囲|有効桁数|.NET 型|
|----------|-----------------------|---------------|-------------------------|
|`double`|±5.0 × 10<sup>−324</sup> - ±1.7 × 10<sup>308</sup>|~15-17 桁|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

既定では、代入演算子の右辺にある実数値リテラルは `double` として扱われます。 ただし、整数を `double` として処理する場合、次のようにサフィックスの d または D を使用します。

```csharp
double x = 3D;
```

## <a name="conversions"></a>変換

整数型と浮動小数点型を 1 つの式の中の混在させることができます。 この場合、整数型が浮動小数点型に変換されます。 式の評価は、次の規則に従って実行されます。

- 浮動小数点型の 1 つが `double` の場合、式は `double` または [bool](../../../csharp/language-reference/keywords/bool.md) (リレーショナル比較および等価比較の場合) と評価されます。

- 式に `double` 型が含まれない場合は、式は [float](../../../csharp/language-reference/keywords/float.md) または [bool](../../../csharp/language-reference/keywords/bool.md) (リレーショナル比較または等価比較の場合) と評価されます。

 浮動小数点式は、次の値のセットを含むことができます。

- 正および負のゼロ。

- 正および負の無限大。

- Not-a-Number (NaN) 値。

- ゼロ以外の値の有限のセット。

これらの値について詳しくは、[IEEE](https://www.ieee.org) の Web サイトで入手できるバイナリ浮動小数点演算の IEEE 標準に関する資料をご覧ください。

## <a name="example"></a>例

次の例では、[int](../builtin-types/integral-numeric-types.md)、[short](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)、[float](../../../csharp/language-reference/keywords/float.md)、`double` がまとめて追加され、結果として `double` になります。

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)
- [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [浮動小数点型の一覧表](../../../csharp/language-reference/keywords/floating-point-types-table.md)
- [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

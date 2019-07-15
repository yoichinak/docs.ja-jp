---
title: char キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: b58730d945582ded7b76fcd5c4c65bc1dd9324da
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661454"
---
# <a name="char-c-reference"></a>char (C# リファレンス)

`char` キーワードは、Unicode 文字を表すために .NET Framework によって使用される <xref:System.Char?displayProperty=nameWithType> 構造体のインスタンスを宣言するときに使用されます。 `Char` オブジェクトの値は、16 ビット数 (序数) 値です。

 Unicode 文字は、世界各国の文字言語の大半を表すために使用されます。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 ～ U+FFFF|Unicode 16 ビット文字|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`char` 型の定数は、文字リテラル、16 進数のエスケープ シーケンス、または Unicode 表現として記述できます。 また、整数の文字コードをキャストすることもできます。 次の例では、4 つの `char` 変数が `X` という同じ文字で初期化されています。

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>変換

`char` は、[ushort](../builtin-types/integral-numeric-types.md)、[int](../builtin-types/integral-numeric-types.md)、[uint](../builtin-types/integral-numeric-types.md)、[double](../builtin-types/floating-point-numeric-types.md)、または [decimal](../builtin-types/floating-point-numeric-types.md) に暗黙的に変換できます。 ただし、他の型から `char` 型へと暗黙的に変換することはできません。

<xref:System.Char?displayProperty=nameWithType> 型では、`char` 値を操作するための静的メソッドがいくつか提供されています。

## <a name="c-language-specification"></a>C# 言語仕様  

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Char>
- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [整数型](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)
- [文字列](../../../csharp/programming-guide/strings/index.md)

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
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698773"
---
# <a name="char-c-reference"></a>char (C# リファレンス)

`char` キーワードは、Unicode 文字を表すために .NET Framework によって使用される <xref:System.Char?displayProperty=nameWithType> 構造体のインスタンスを宣言するときに使用されます。 `Char` オブジェクトの値は、16 ビット数 (序数) 値です。

 Unicode 文字は、世界各国の文字言語の大半を表すために使用されます。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 ～ U+FFFF|Unicode 16 ビット文字|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`char` 型の定数は、文字リテラル、16 進数のエスケープ シーケンス、または Unicode 表現として記述できます。 また、整数の文字コードをキャストすることもできます。 次の例では、`char` の配列の 4 つの要素が同じ文字 `X` を使用して初期化されています。

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>変換

`char` は、[ushort](../builtin-types/integral-numeric-types.md)、[int](../builtin-types/integral-numeric-types.md)、[uint](../builtin-types/integral-numeric-types.md)、[double](../builtin-types/floating-point-numeric-types.md)、または [decimal](../builtin-types/floating-point-numeric-types.md) に暗黙的に変換できます。 ただし、他の型から `char` 型へと暗黙的に変換することはできません。

<xref:System.Char?displayProperty=nameWithType> 型では、`char` 値を操作するための静的メソッドがいくつか提供されています。

## <a name="c-language-specification"></a>C# 言語仕様  

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Char>
- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
- [整数型](../builtin-types/integral-numeric-types.md)
- [組み込み型の一覧表](./built-in-types-table.md)
- [暗黙的な数値変換の一覧表](./implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](./explicit-numeric-conversions-table.md)
- [文字列](../../programming-guide/strings/index.md)

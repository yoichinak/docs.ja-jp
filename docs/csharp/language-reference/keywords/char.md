---
title: char キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771798"
---
# <a name="char-c-reference"></a>char (C# リファレンス)

`char` 型のキーワードは、Unicode UTF-16 文字を表す .NET <xref:System.Char?displayProperty=nameWithType> 構造体型のエイリアスです。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 ～ U+FFFF|16 ビット|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`char` 型の定数は、文字リテラル、16 進数のエスケープ シーケンス、または Unicode 表現として記述できます。 また、整数の文字コードを対応する `char` 値にキャストすることもできます。 次の例では、`char` の配列の 4 つの要素が同じ文字 `X` を使用して初期化されています。

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>変換

`char` 型は、[整数](../builtin-types/integral-numeric-types.md)型 (`ushort`、`int`、`uint`、`long`、`ulong`) に暗黙的に変換できます。 また、組み込みの[浮動小数点](../builtin-types/floating-point-numeric-types.md)数値型 (`float`、`double`、`decimal`) に暗黙的に変換することもできます。 `sbyte`、`byte`、`short` 整数型に明示的に変換できます。

他の型から `char` 型へと暗黙的に変換することはできません。 しかし、[整数](../builtin-types/integral-numeric-types.md)または[浮動小数点](../builtin-types/floating-point-numeric-types.md)の数値型は、`char` に明示的に変換できます。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# キーワード](./index.md)
- [組み込み型の一覧表](./built-in-types-table.md)
- [文字列](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>

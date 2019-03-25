---
title: int - C# リファレンス
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 6cabc2c6d4930c5d5fc88e76a17c1a6425ddd1bd
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185780"
---
# <a name="int-c-reference"></a>int (C# リファレンス)

`int` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`int`|-2,147,483,648 ～ 2,147,483,647|符号付き 32 ビット整数|<xref:System.Int32?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`int` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。  整数リテラルが `int` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`int` 値に割り当てられています。

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]

> [!NOTE]
> 16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。 10 進リテラルには、プレフィックスはありません。

C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。
- C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。
- C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。 10 進リテラルは先頭にアンダー スコアを持つことはできません。

以下にいくつか例を示します。

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]

整数リテラルでは型を示すサフィックスを含めることもできますが、`int` 型を示すサフィックスはありません。 サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。

1. `int`
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md)

ここで示した例では、リテラル 90946 は `int` 型になります。

## <a name="conversions"></a>変換

`int` から [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙の型変換が組み込まれています。 次に例を示します。

```csharp
// '123' is an int, so an implicit conversion takes place here:
float f = 123;
```

[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[char](../../../csharp/language-reference/keywords/char.md) から `int` への、定義済みの暗黙の型変換が組み込まれています。 たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。

```csharp
long aLong = 22;
int i1 = aLong;       // Error: no implicit conversion from long.
int i2 = (int)aLong;  // OK: explicit conversion.
```

浮動小数点型から `int` への暗黙的な変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。

```csharp
int x = 3.0;         // Error: no implicit conversion from double.
int y = (int)3.0;    // OK: explicit conversion.
```

浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Int32>
- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

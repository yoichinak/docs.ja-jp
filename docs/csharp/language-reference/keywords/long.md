---
title: long - C# リファレンス
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 997ce7399dc9742076932b213811abd1f847e60b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613292"
---
# <a name="long-c-reference"></a>long (C# リファレンス)

`long` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`long`|-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807|符号付き 64 ビット整数|<xref:System.Int64?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`long` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。

次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`long` 値に割り当てられています。

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]

> [!NOTE]
> 16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。 10 進リテラルには、プレフィックスはありません。

C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。
- C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。
- C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。 10 進リテラルは先頭にアンダー スコアを持つことはできません。

以下にいくつか例を示します。

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

整数リテラルには、型を表すサフィックスを含めることもできます。 サフィックス `L` は `long` を表します。 次の例では、`L` サフィックスを使って long 整数を示しています。

```csharp
long value = 4294967296L;
```

> [!NOTE]
> 小文字の "l" もサフィックスとして使用できます。 ただし、文字の "l" は数字の "1" と混同しやすいため、コンパイラから警告が出されます。 明確にするには、"L" を使用します。

サフィックス `L` を使う場合、整数リテラルの型は、そのサイズに応じて `long` または [ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかに決まります。 この場合、整数リテラルが [ulong](../../../csharp/language-reference/keywords/ulong.md) の範囲より小さいため、`long` になります。

サフィックスは、オーバーロードされたメソッドの呼び出しによく使われます。 たとえば、次のオーバーロードされたメソッドには、`long` 型と [int](../../../csharp/language-reference/keywords/int.md) 型のパラメーターがあります。

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(long l) {}
```

`L` サフィックスにより、適切なオーバーロードが呼び出されることが保証されます。

```csharp
SampleMethod(5);    // Calls the method with the int parameter
SampleMethod(5L);   // Calls the method with the long parameter
```

サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md)

前の例のリテラル 4294967296 は、[uint](../../../csharp/language-reference/keywords/uint.md) の範囲を超えているため、`long` 型になります (整数型の記憶サイズについては、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」をご覧ください)。

同じ式の他の整数型で `long` 型を使うと、式は `long` (関係式またはブール式の場合は [bool](../../../csharp/language-reference/keywords/bool.md)) として評価されます。 たとえば、次の式は `long` として評価されます。

```csharp
898L + 88
```

浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。

## <a name="conversions"></a>変換

`long` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。 それ以外の型の場合は、キャストを使用する必要があります。 たとえば、次の代入ステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。

```csharp
int x = 8L;        // Error: no implicit conversion from long to int
int y = (int)8L;   // OK: explicit conversion to int
```

[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[char](../../../csharp/language-reference/keywords/char.md) から `long` への暗黙の型変換が組み込まれています。

また、浮動小数点型から `long` への暗黙の型変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。

```csharp
long x = 3.0;         // Error: no implicit conversion from double
long y = (long)3.0;   // OK: explicit conversion
```

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Int64>
- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

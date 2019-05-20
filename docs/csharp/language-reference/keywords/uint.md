---
title: unit キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: 9a60460f67f9b6cf0b57d40ebf2789536e870d75
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633143"
---
# <a name="uint-c-reference"></a>uint (C# リファレンス)

`uint` キーワードは、次の表に示すサイズと範囲で値を格納する整数型を示します。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`uint`|0 ～ 4,294,967,295|符号なし 32 ビット整数|<xref:System.UInt32?displayProperty=nameWithType>|

**メモ** `uint` 型は CLS に準拠していません。 可能な場合は、`int` を使用します。

## <a name="literals"></a>リテラル

`uint` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。 整数リテラルが `uint` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`uint` 値に割り当てられています。

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> 16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。 10 進リテラルには、プレフィックスはありません。

C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。

- C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。
- C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。 10 進リテラルは先頭にアンダー スコアを持つことはできません。

以下にいくつか例を示します。

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

整数リテラルには、型を表すサフィックスを含めることもできます。 サフィックス `U` または 'u' は、リテラルの数値に応じて `uint` または `ulong` を示します。 次の例では、`u` サフィックスを使って、両方の型の符号なし整数を示しています。 最初のリテラルは値が <xref:System.UInt32.MaxValue?displayProperty=nameWithType> より小さいため、`uint` であるのに対し、2 番目は値が <xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きいため、`ulong` であることに注意してください。

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。

1. [int](int.md)
2. `uint`
3. [long](long.md)
4. [ulong](ulong.md)

## <a name="conversions"></a>変換

`uint` から [long](long.md)、[ulong](ulong.md)、[float](float.md)、[double](double.md)、[decimal](decimal.md) への、定義済みの暗黙的な変換が組み込まれています。 次に例を示します。

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

[byte](byte.md)、[ushort](ushort.md)、または [char](char.md) から `uint` への、定義済みの暗黙的な変換が組み込まれています。 それ以外の場合は、キャストを使用する必要があります。 たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

浮動小数点型から `uint` への暗黙的な変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

浮動小数点型と整数型の混在する算術式の詳細については、「[float](float.md)」および「[double](double.md)」を参照してください。

暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](implicit-numeric-conversions-table.md)」を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.UInt32>
- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [整数型の一覧表](integral-types-table.md)
- [組み込み型の一覧表](built-in-types-table.md)
- [暗黙的な数値変換の一覧表](implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](explicit-numeric-conversions-table.md)

---
title: byte - C# リファレンス
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 94ecc19294d82038e5406a05f8e1281d47e43081
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185910"
---
# <a name="byte-c-reference"></a>byte (C# リファレンス)

`byte` は、次の表に示された値を格納する整数型を示します。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`byte`|0 ～ 255|符号なし 8 ビット整数|<xref:System.Byte?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`byte` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。 整数リテラルが `byte` の範囲外にある場合 (つまり、<xref:System.Byte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Byte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 201 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `byte` 値に暗黙的に変換されています。

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]

> [!NOTE]
> 16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。 10 進リテラルには、プレフィックスはありません。

C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。
- C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。
- C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。 10 進リテラルは先頭にアンダー スコアを持つことはできません。

以下にいくつか例を示します。

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]

## <a name="conversions"></a>変換

`byte` から [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。

より大きな記憶領域のサイズを持つ、リテラル以外の数値型を暗黙的に `byte` に変換することはできません。 整数型の記憶域サイズの詳細については、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください。 たとえば、2 つの `byte` 変数 `x` と `y` があるとします。

```csharp
byte x = 10, y = 20;
```

次の代入ステートメントは、代入演算子の右側にある算術式が既定で `int` に評価されるため、コンパイル エラーになります。

```csharp
// Error: conversion from int to byte:
byte z = x + y;
```

この問題を解決するには、キャストを使用します。

```csharp
// OK: explicit conversion:
byte z = (byte)(x + y);
```

ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。

```csharp
int x = 10, y = 20;
int m = x + y;
long n = x + y;
```

浮動小数点型から `byte` への暗黙の型変換はありません。 たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。

```csharp
// Error: no implicit conversion from double:
byte x = 3.0;
// OK: explicit conversion:
byte y = (byte)3.0;
```

オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。 たとえば、`byte` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(byte b) {}
```

`byte` キャストを使用すると、正しい型が呼び出されます。次に例を示します。

```csharp
// Calling the method with the int parameter:
SampleMethod(5);
// Calling the method with the byte parameter:
SampleMethod((byte)5);
```

浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。

暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Byte>
- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

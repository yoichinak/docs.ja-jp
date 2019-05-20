---
title: short - C# リファレンス
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 0b02e72e0588f1c1a0343a391430b5878b96b5f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633993"
---
# <a name="short-c-reference"></a>short (C# リファレンス)

`short` は、次の表に示すサイズと範囲で値を格納する整数データ型を示します。

|型|範囲|サイズ|.NET 型|
|----------|-----------|----------|-------------------------|
|`short`|-32,768 ～ 32,767|符号付き 16 ビット整数|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a>リテラル

`short` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。  整数リテラルが `short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 1,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](int.md) から `short` 値に暗黙的に変換されています。

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> 16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。 10 進リテラルには、プレフィックスはありません。

C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。

- C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。
- C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。 10 進リテラルは先頭にアンダー スコアを持つことはできません。

以下にいくつか例を示します。

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a>コンパイラのオーバーロード解決

オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。 たとえば、`short` パラメーターと [int](int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

`short` キャストを使用すると、正しい型が呼び出されます。次に例を示します。

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a>変換

`short` から [int](int.md)、[long](long.md)、[float](float.md)、[double](double.md)、[decimal](decimal.md) への、定義済みの暗黙的な変換が組み込まれています。

記憶領域が大きなリテラル以外の数値型を暗黙的に `short` に変換することはできません (整数型の記憶領域については、「[整数型の一覧表](integral-types-table.md)」を参照してください)。 たとえば、2 つの `short` 変数 `x` と `y` があるとします。

```csharp
short x = 5, y = 12;
```

次の代入ステートメントは、代入演算子の右側にある算術式が既定で [int](int.md) に評価されるため、コンパイル エラーになります。

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

この問題を解決するには、キャストを使用します。

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

次のステートメントを使うこともできます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。

```csharp
int m = x + y;
long n = x + y;
```

浮動小数点型から `short` への暗黙的な変換は行われません。 たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

浮動小数点型と整数型の混在する算術式の詳細については、「[float](float.md)」と「[double](double.md)」を参照してください。

暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](implicit-numeric-conversions-table.md)」をご覧ください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Int16>
- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [整数型の一覧表](integral-types-table.md)
- [組み込み型の一覧表](built-in-types-table.md)
- [暗黙的な数値変換の一覧表](implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](explicit-numeric-conversions-table.md)

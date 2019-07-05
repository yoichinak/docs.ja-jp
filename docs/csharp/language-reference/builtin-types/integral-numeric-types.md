---
title: 整数数値型 - C# リファレンス
description: 各整数数値型の範囲、ストレージ サイズ、および使用方法について説明します。
ms.date: 06/25/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: bde0b7cea52951cd72bde6cfd7d8f1c7dbcb8f46
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425597"
---
# <a name="integral-numeric-types--c-reference"></a>整数数値型 (C# リファレンス)

**整数数値型**は**単純型**のサブセットであり、[*リテラル*](#integral-literals)を使用して初期化できます。 すべての整数型は、値型でもあります。

すべての整数数値型では [arithmetic](../operators/arithmetic-operators.md)、[bitwise logical](../operators/bitwise-and-shift-operators.md)、[comparison、equality](../operators/equality-operators.md) 演算子がサポートされています。

## <a name="sizes-and-ranges"></a>サイズと範囲

次の表は、整数型のサイズと範囲を示しています。

|型|範囲|サイズ|  
|----------|-----------|----------|  
|`sbyte`|-128 ～ 127|符号付き 8 ビット整数|  
|`byte`|0 ～ 255|符号なし 8 ビット整数|  
|`short`|-32,768 ～ 32,767|符号付き 16 ビット整数|  
|`ushort`|0 ～ 65,535|符号なし 16 ビット整数|  
|`int`|-2,147,483,648 ～ 2,147,483,647|符号付き 32 ビット整数|  
|`uint`|0 ～ 4,294,967,295|符号なし 32 ビット整数|  
|`long`|-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807|符号付き 64 ビット整数|  
|`ulong`|0 ～ 18,446,744,073,709,551,615|符号なし 64 ビット整数|  

すべての整数型の既定値は、`0` です。 各整数型には、型の最小値と最大値に対して、`MinValue` および `MaxValue` という名前の定数があります。

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> 構造体を使用して、上限や下限のない符号付き整数を表します。

## <a name="integral-literals"></a>整数リテラル

整数リテラルは、*10 進リテラル*、*16 進数リテラル*、または*バイナリ リテラル*として指定できます。 それぞれの例を次に示します。

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

10 進リテラルには、プレフィックスは必要ありません。 `x` または `X` プレフィックスは *16 進数リテラル*を意味します。 `b` または `B` プレフィックスは*バイナリ リテラル*を意味します。 `binaryLiteral` の宣言は、`_` を*桁区切り記号*として使用することを示します。 桁区切り記号は、すべての数値リテラルで使用できます。 バイナリ リテラルと桁区切り記号 `_` は、C# 7.0 以降でサポートされています。

## <a name="literal-suffixes"></a>リテラル サフィックス 

`l` または `L` サフィックスは、整数リテラルが `long` 型である必要があることを示します。 `ul` または `UL` サフィックスは、`ulong` 型を示します。 `L` サフィックスが 9,223,372,036,854,775,807 (`long` の最大値) より大きいリテラルで使用されている場合、値は `ulong` 型に変換されます。 整数リテラルで表される値が <xref:System.UInt64.MaxValue?displayProperty=nameWithType> を超えると、コンパイル エラー [CS1021](../../misc/cs1021.md) が発生します。 

> [!NOTE]
> 小文字の "l" はサフィックスとして使用できます。 ただし、文字の "l" は数字の "1" と混同しやすいため、コンパイラから警告が出されます。 明確にするには、"L" を使用します。

## <a name="type-of-an-integral-literal"></a>整数リテラルの型

サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。

1. `int`
1. `uint`
1. `long`
1. `ulong`

整数リテラルは、割り当てまたはキャストのどちらかを使用して、既定よりも小さな範囲の型に変換することができます。

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

整数リテラルは、割り当て、キャスト、またはリテラル上のサフィックスのいずれかを使用して、既定よりも大きな範囲の型に変換することができます。

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>変換

変換先の型に変換元の型のすべての値を格納可能な、任意の 2 つの整数型間の暗黙的な変換 (*拡大変換*と呼ばれます) があります。 たとえば、`int` 値の範囲が `long` の適切なサブセットであるため、`int` から `long` への暗黙的な変換があります。 小さな符号なし整数型から、大きな符号付き整数型への暗黙的な変換があります。 任意の整数型から、任意の浮動小数点型への暗黙的な変換もあります。  任意の符号付き整数型から、任意の符号なし整数型への暗黙的な変換はありません。

変換元の型から変換先の型への暗黙的な変換が定義されていない場合、明示的なキャストを使用して、1 つの整数型を別の整数型に変換する必要があります。 これは*縮小変換*と呼ばれています。 変換によりデータが失われる場合があるため、明示的なケースが必要となります。

## <a name="see-also"></a>関連項目

- [C# 言語仕様 - 整数型](~/_csharplang/spec/types.md#integral-types)
- [C# リファレンス](../index.md)
- [浮動小数点型の一覧表](../keywords/floating-point-types-table.md)
- [既定値の一覧表](../keywords/default-values-table.md)
- [数値結果テーブルの書式設定](../keywords/formatting-numeric-results-table.md)
- [組み込み型の一覧表](../keywords/built-in-types-table.md)
- [.NET における数値](../../../standard/numerics.md)

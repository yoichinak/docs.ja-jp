---
title: 値型の一覧表 - C# リファレンス
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 959d4840344ba041ae1b01fd6d202f2b53936afc
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422375"
---
# <a name="value-types-table-c-reference"></a>値型の一覧表 (C# リファレンス)

C# の値の型を次の表に示します。

|値の種類|カテゴリ|型のサフィックス|
|----------------|--------------|-----------------|
|[bool](bool.md)|ブール型||
|[byte](byte.md)|符号なし、数値、[整数](integral-types-table.md)||
|[char](char.md)|符号なし、数値、[整数](integral-types-table.md)||
|[decimal](decimal.md)|数値、[浮動小数点数](floating-point-types-table.md)|M または m|
|[double](double.md)|数値、[浮動小数点数](floating-point-types-table.md)|D または d|
|[enum](enum.md)|列挙||
|[float](float.md)|数値、[浮動小数点数](floating-point-types-table.md)|F または f|
|[int](int.md)|符号付き、数値、[整数](integral-types-table.md)||
|[long](long.md)|符号付き、数値、[整数](integral-types-table.md)|L または l|
|[sbyte](sbyte.md)|符号付き、数値、[整数](integral-types-table.md)||
|[short](short.md)|符号付き、数値、[整数](integral-types-table.md)||
|[struct](struct.md)|ユーザー定義構造体||
|[uint](uint.md)|符号なし、数値、[整数](integral-types-table.md)|U または u|
|[ulong](ulong.md)|符号なし、数値、[整数](integral-types-table.md)|UL、Ul、uL、ul、LU、Lu、lU、または lu|
|[ushort](ushort.md)|符号なし、数値、[整数](integral-types-table.md)||

## <a name="remarks"></a>解説

型のサフィックスを使用して数値リテラルの型を指定します。 次に例を示します。

```csharp
decimal a = 0.1M;
```

[整数リテラル](~/_csharplang/spec/lexical-structure.md#integer-literals)にサフィックスがない場合、以下の型のうちその値を表すことができる最初のものが使用されます: `int`、`uint`、`long`、`ulong`。

[実数値リテラル](~/_csharplang/spec/lexical-structure.md#real-literals)にサフィックスがない場合、その型は `double` になります。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [既定値の一覧表](default-values-table.md)
- [値型](value-types.md)
- [数値結果テーブルの書式設定](formatting-numeric-results-table.md)

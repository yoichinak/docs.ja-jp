---
title: 値型の一覧表 - C# リファレンス
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 2e2897ff647140b58b3a1812e153a44a6fcdaef7
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859557"
---
# <a name="value-types-table-c-reference"></a>値型の一覧表 (C# リファレンス)

C# の値の型を次の表に示します。

|値の種類|カテゴリ|型のサフィックス|
|----------------|--------------|-----------------|
|[bool](bool.md)|ブール型||
|`byte`|符号なし、数値、[整数](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|符号なし、数値、[整数](../builtin-types/integral-numeric-types.md)
|`decimal`|数値、[浮動小数点数](../builtin-types/floating-point-numeric-types.md)|M または m|
|`double`|数値、[浮動小数点数](../builtin-types/floating-point-numeric-types.md)|D または d|
|[enum](enum.md)|列挙||
|`float`|数値、[浮動小数点数](../builtin-types/floating-point-numeric-types.md)|F または f|
|`int`|符号付き、数値、[整数](../builtin-types/integral-numeric-types.md)||
|`long`|符号付き、数値、[整数](../builtin-types/integral-numeric-types.md)|L または l|
|`sbyte`|符号付き、数値、[整数](../builtin-types/integral-numeric-types.md)||
|`short`|符号付き、数値、[整数](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|ユーザー定義構造体||
|`uint`|符号なし、数値、[整数](../builtin-types/integral-numeric-types.md)|U または u|
|`ulong`|符号なし、数値、[整数](../builtin-types/integral-numeric-types.md)|UL、Ul、uL、ul、LU、Lu、lU、または lu|
|`ushort`|符号なし、数値、[整数](../builtin-types/integral-numeric-types.md)||

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

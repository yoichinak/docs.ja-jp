---
title: 暗黙的な数値変換の一覧表 - C# リファレンス
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 516505ccacfd2a8a5c275b0de033e1316fa06d3a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661334"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>暗黙的な数値変換の一覧表 (C# リファレンス)

.NET 数値型間の定義済みの暗黙的な変換を次の表に示します。
  
|変換元|終了|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`short`、`int`、`long`、`float`、`double`、または `decimal`|  
|[byte](../builtin-types/integral-numeric-types.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[char](char.md)|`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[short](../builtin-types/integral-numeric-types.md)|`int`、`long`、`float`、`double`、または `decimal`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[int](../builtin-types/integral-numeric-types.md)|`long`、`float`、`double`、または `decimal`|  
|[uint](../builtin-types/integral-numeric-types.md)|`long`、`ulong`、`float`、`double`、または `decimal`|  
|[long](../builtin-types/integral-numeric-types.md)|`float`、 `double`、または `decimal`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`float`、 `double`、または `decimal`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`double`|  
  
## <a name="remarks"></a>解説  

- [整数型](../builtin-types/integral-numeric-types.md)はすべて、あらゆる[浮動小数点型](../builtin-types/floating-point-numeric-types.md)に暗黙的に変換できます。

- `int`、`uint`、`long`、または `ulong` から `float` への変換と `long` から `ulong` または `double` への変換では、有効桁数が失われる場合があります (絶対値ではありません)。  
  
- `char`、`byte`、`sbyte` 型への暗黙的な変換はありません。  

- `double` および `decimal` 型からの暗黙的な変換はありません。
  
- `decimal` 型と `float` 型または `double` 型の間に暗黙的な変換はありません。  
  
- 型 `int` の定数式の値 (整数リテラルで表される値など) は、それが変換先の型の範囲内にある場合、`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong` に変換できます。

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

明示的な変換に関する詳細については、[C# 言語仕様](../language-specification/index.md)に関するページの「[Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions)」 (明示的な変換) セクションをご覧ください。
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [整数型](../builtin-types/integral-numeric-types.md)
- [浮動小数点型の一覧表](../builtin-types/floating-point-numeric-types.md)
- [組み込み型の一覧表](built-in-types-table.md)
- [明示的な数値変換の一覧表](explicit-numeric-conversions-table.md)
- [キャストと型変換](../../programming-guide/types/casting-and-type-conversions.md)

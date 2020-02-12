---
title: 組み込み型 - C# リファレンス
description: C# の組み込みの値型と参照型を示します
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 4f748373350ed0596a5f1d595c273243ae3227c3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095295"
---
# <a name="built-in-types-c-reference"></a>組み込み型 (C# リファレンス)

C# の組み込みの[値](value-types.md)型を次の表に一覧表示します。

|C# 型キーワード|.NET 型|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

C# の組み込みの[参照](../keywords/reference-types.md)型を次の表に一覧表示します。

|C# 型キーワード|.NET 型|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

上の表の左の列にある各 C# 型キーワードは、対応する .NET 型の別名です。 これらは交換可能です。 たとえば、次の宣言では、同じ型の変数が宣言されています。

```csharp
int a = 123;
System.Int32 b = 123;
```

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# 型の既定値](default-values.md)
- [`dynamic` キーワード](reference-types.md#the-dynamic-type)

---
title: 組み込み型の一覧表 - C# リファレンス
ms.custom: seodec18
description: C# の組み込み型のキーワード
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bd8c52cd798496a4df3086411dfe3be6241fbff5
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422346"
---
# <a name="built-in-types-table-c-reference"></a>組み込み型の一覧表 (C# リファレンス)

次の表は、C# の組み込み型のキーワードを示しています。これは、<xref:System> 名前空間の定義済み型の別名です。  
  
|C# 型|.NET 型|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>解説

表内の、`object` と `string` を除くすべての型が、単純型と呼ばれます。  
  
C# 型のキーワードと別名は相互に交換できます。 たとえば、整数の変数を宣言するには、次のいずれかの宣言を使用します。  

```csharp
int x = 123;
System.Int32 y = 123;
```

[typeof](typeof.md) 演算子を使用して、指定した型を表す <xref:System.Type?displayProperty=nameWithType> インスタンスを取得します。

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](index.md)
- [値型](value-types.md)
- [参照型](reference-types.md)
- [既定値の一覧表](default-values-table.md)
- [dynamic](dynamic.md)

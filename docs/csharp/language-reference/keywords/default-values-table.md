---
title: 既定値の一覧表 - C# リファレンス
ms.custom: seodec18
description: C# の型における既定値について説明します。
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627747"
---
# <a name="default-values-table-c-reference"></a>既定値の一覧表 (C# リファレンス)

次の表では、C# の型の既定値を示します。

|型|既定値|
|---------|------------------|
|すべての参照型|`null`|
|任意の[組み込み整数数値型](../builtin-types/integral-numeric-types.md)|0 (ゼロ)|
|任意の[組み込み浮動小数点数値型](../builtin-types/floating-point-numeric-types.md)|0 (ゼロ)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|式 `(E)0` によって生成される値。`E` は列挙型識別子です。|
|[struct](struct.md)|すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。|
|任意の [null 許容値型](../../programming-guide/nullable-types/index.md)|<xref:System.Nullable%601.HasValue%2A> プロパティが `false` で、<xref:System.Nullable%601.Value%2A> プロパティが未定義のインスタンス。 その規定値は、null 許容値型の "*null*" 値とも呼ばれます。|

[既定の値式](../../programming-guide/statements-expressions-operators/default-value-expressions.md)を使用して、次の例に示すように、型の既定値を生成します。

```csharp
int a = default(int);
```

C# 7.1 以降、[`default` リテラル](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference)を使用して、その型の既定値に変数を初期化できます。

```csharp
int a = default;
```

値の型については、次の例が示すように、暗黙的なパラメーターなしのコンストラクターによっても、型の既定値が生成されます。

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。

- [既定値](~/_csharplang/spec/variables.md#default-values)
- [既定のコンストラクター](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# キーワード](index.md)
- [組み込み型の一覧表](built-in-types-table.md)
- [コンストラクター](../../programming-guide/classes-and-structs/constructors.md)

---
title: 既定値の一覧表 - C# リファレンス
ms.custom: seodec18
description: C# の値型における既定値について説明します。
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: 4fc9a35f69540e047a97c21788015ca8e54068a0
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422034"
---
# <a name="default-values-table-c-reference"></a>既定値の一覧表 (C# リファレンス)

次の表では、[値型](value-types.md)の既定値を示します。

|値の種類|既定値|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0.0D|
|[enum](enum.md)|式 `(E)0` によって生成される値。`E` は列挙型識別子です。|
|[float](float.md)|0.0F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="remarks"></a>解説

C# で初期化されていない変数を使用することはできません。 変数はその型の既定値に初期化することができます。 また、型の既定値を使用して、メソッドの[省略可能な引数](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments)の既定値を指定することもできます。

[既定の値式](../../programming-guide/statements-expressions-operators/default-value-expressions.md)を使用して、次の例に示すように、型の既定値を生成します。

```csharp
int a = default(int);
```

C# 7.1 以降、[`default` リテラル](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference)を使用して、その型の既定値に変数を初期化できます。

```csharp
int a = default;
```

また、次の例に示すように、パラメーターなしのコンストラクターまたは暗黙的なパラメーターなしのコンストラクターを使用して、値型の既定値を生成することもできます。 コンストラクターの詳細については、[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)に関する記事を参照してください。

```csharp
int a = new int();
```

[参照型](reference-types.md)の既定値は `null` です。 [null 許容型](../../programming-guide/nullable-types/index.md)の既定値は、<xref:System.Nullable%601.HasValue%2A> プロパティが `false` で、<xref:System.Nullable%601.Value%2A> プロパティが未定義のインスタンスです。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [値型](value-types.md)
- [値型の一覧表](value-types-table.md)
- [組み込み型の一覧表](built-in-types-table.md)

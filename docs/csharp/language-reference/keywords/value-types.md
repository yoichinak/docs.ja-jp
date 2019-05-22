---
title: 値型 - C# リファレンス
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 390b2226cc2f345d2f42659bd092e36a4bd0c4fc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632923"
---
# <a name="value-types-c-reference"></a>値型 (C# リファレンス)

2 種類の値型があります。

- [構造体](struct.md)

- [列挙型](enum.md)

## <a name="main-features-of-value-types"></a>値型の主な機能

値型の変数には、その型の値が含まれています。 たとえば、`int` 型の変数には値 `42` が含まれている可能性があります。 これは、オブジェクトとも呼ばれる型のインスタンスへの参照を含む参照型の変数とは異なります。 値型の変数に新しい値を割り当てると、その値はコピーされます。 参照型の変数に新しい値を割り当てると、オブジェクト自体ではなく参照がコピーされます。

すべての値型が <xref:System.ValueType?displayProperty=nameWithType> から暗黙的に派生されます。

参照型とは異なり、値型から新しい型を派生することはできません。 ただし、参照型の場合と同様に、構造体はインターフェイスを実装できます。

値型の変数は既定で `null` にすることはできません。 ただし、対応する [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)の変数を `null` にすることはできます。

各値型には、その型の既定値を初期化する暗黙のパラメーターなしのコンストラクターがあります。 値型の既定値の詳細については、「[既定値の一覧表](default-values-table.md)」を参照してください。

## <a name="simple-types"></a>単純型

*単純型*は、C# に用意されている定義済みの構造体型のセットであり、次の型を構成します。

- [整数型](integral-types-table.md): 整数の数値型と [char](char.md) 型
- [浮動小数点型](floating-point-types-table.md)
- [bool](bool.md)

単純型はキーワードで識別されますが、これらのキーワードは、<xref:System> 名前空間に事前に定義されている構造体型の単なるエイリアスです。 たとえば、[int](int.md) は <xref:System.Int32?displayProperty=nameWithType> のエイリアスです。 エイリアスの完全な一覧については、「[組み込み型の一覧表](built-in-types-table.md)」を参照してください。

単純型は、ある追加の操作を許可している点で、他の構造体型とは異なります。

- 単純型はリテラルを使用して初期化できます。 たとえば、`'A'` は `char` 型のリテラルで、`2001` は `int` 型のリテラルです。

- 単純型の定数は、[const](const.md) キーワードを使用して宣言できます。 他の構造体型の定数を持つことはできません。

- オペランドがすべて単純型の定数式は、コンパイル時に評価されます。

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[単純型](~/_csharplang/spec/types.md#simple-types)に関するセクションを参照してください。

## <a name="initializing-value-types"></a>値型の初期化

C# では、ローカル変数を使用する前に初期化する必要があります。 たとえば、次の例のように、初期化せずにローカル変数を宣言した場合、

```csharp
int myInt;
```

初期化してからでないとこれを使用することはできません。 次のステートメントを使用して初期化できます。

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

このステートメントは、次のステートメントと同じです。

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

もちろん、次の例のように、宣言と初期化を同じステートメントに含めることができます。

```csharp
int myInt = new int();
```

または

```csharp
int myInt = 0;
```

[new](new.md) 演算子を使用すると、特定の型のパラメーターなしのコンストラクターを呼び出し、既定値を変数に代入します。 前の例では、パラメーターなしのコンス トラクターで値 `0` を `myInt` に代入していました。 既定のコンストラクターの呼び出しにより値を代入する詳細については、「[既定値の一覧表](default-values-table.md)」を参照してください。

ユーザー定義型では、[new](new.md) を使用してパラメーターなしのコンストラクターを呼び出します。 たとえば、次のステートメントは、`Point` 構造体のパラメーターなしのコンストラクターを呼び出します。

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

この呼び出しの後、構造体は明示的に代入されると見なされます。つまり、すべてのメンバーがその既定値に初期化されます。

`new` 演算子の詳細については、「[new](new.md)」を参照してください。

数値型の出力の書式設定については、「[数値結果テーブルの書式設定](formatting-numeric-results-table.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [型](types.md)
- [型のリファレンス表](reference-tables-for-types.md)
- [参照型](reference-types.md)
- [Null 許容型](../../programming-guide/nullable-types/index.md)

---
title: ?? 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816011"
---
# <a name="-operator-c-reference"></a>?? 演算子 (C# リファレンス)

null 合体演算子 `??` では、それが `null` ではない場合、その左側のオペランドの値が返されます。それ以外の場合は、右側のオペランドが評価され、その結果が返されます。 `??` 演算子では、左側のオペランドが null 値以外に評価された場合は、その右側のオペランドは評価されません。

null 合体演算子は右結合です。つまり、次のフォームの式は

```csharp
a ?? b ?? c
```

これが次のように評価されます。

```csharp
a ?? (b ?? c)
```

`??` 演算子は、次のシナリオで役立つことがあります。

- [null 条件演算子 ?. および ?[]](member-access-operators.md#null-conditional-operators--and-) を含む式は、null 条件演算の式の結果が `null` の場合に評価する代替の式を指定するために、null 合体演算子を使用することができます。

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- [null 値許容型](../../programming-guide/nullable-types/index.md)を使用して、基になる値の型の値を提供する必要がある場合、null 合体演算子を使用して、null 値許容型が `null` の場合に提供する値を指定します。

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  null 値許容型が `null` の場合に使用される値を、基になる値型の既定値にする場合は、<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> メソッドを使用します。

- C# 7.0 以降、null 合体演算子の右側のオペランドとして [`throw` 式](../keywords/throw.md#the-throw-expression)を使用し、引数のチェック コードをより簡潔にすることができます。

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  上記の例は、[式のようなメンバー](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)を使用してプロパティを定義する方法も示しています。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

null 合体演算子はオーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の [null 合体演算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [?. および ?[] 演算子](member-access-operators.md#null-conditional-operators--and-)
- [?:演算子 (C# リファレンス)](conditional-operator.md)

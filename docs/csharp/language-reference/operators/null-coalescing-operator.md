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

Null 合体演算子`??`でない場合は、左側のオペランドの値を返します`null`。 そうしないと、右側のオペランドを評価し、その結果を返します。 `??`左側のオペランドが null 以外に評価された場合、演算子は、右辺のオペランドを評価しません。

Null 合体演算子は右から左、形式の式は、

```csharp
a ?? b ?? c
```

これが次のように評価されます。

```csharp
a ?? (b ?? c)
```

`??`演算子は、次のシナリオで役に立ちます。

- 含む式で、 [null 条件演算子?. およびですか?](member-access-operators.md#null-conditional-operators--and-)、null 合体演算子を使用するには代替場合に、null 条件操作を使用して式の結果を評価する式を指定する`null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- 操作が[null 許容値型](../../programming-guide/nullable-types/index.md)場合に、null 許容型の値を提供する値を指定する null 合体演算子を使用して、基になる値型の値を指定する必要があると`null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  使用して、<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>メソッド場合、null 許容型の値は、ときに使用される値`null`基になる値型の既定値である必要があります。

- 以降でC#使用することができます、7.0、 [ `throw`式](../keywords/throw.md#the-throw-expression)引数チェック コードを簡潔にするため null 合体演算子の右側のオペランドとして。

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  上記の例では、使用する方法も示しています[に式形式メンバー](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)プロパティを定義します。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

Null 合体演算子はオーバー ロードすることはできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、次を参照してください。 [null 合体演算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)のセクション、 [ C#言語仕様](~/_csharplang/spec/introduction.md)します。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [?. および ?[] 演算子](member-access-operators.md#null-conditional-operators--and-)
- [?:演算子 (C# リファレンス)](conditional-operator.md)

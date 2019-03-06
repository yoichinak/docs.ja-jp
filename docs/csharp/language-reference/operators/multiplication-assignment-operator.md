---
title: '*= 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967387"
---
# <a name="-operator-c-reference"></a>\*= 演算子 (C# リファレンス)

乗算代入演算子です。

次のような `*=` 演算子を使用する式があるとします

```csharp
x *= y
```

上記の式は、次の式と同じです。

```csharp
x = x * y
```

ただし、`x` が評価されるのは 1 回だけです。

数値型の場合、[\* 演算子](multiplication-operator.md)によってそのオペランドの積が計算されます。

`*=` 演算子の使用例を次に示します。

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型により[乗算演算子](multiplication-operator.md) `*` が[オーバーロード](../keywords/operator.md)される場合、乗算代入演算子 `*=` は暗黙的にオーバーロードされます。 ユーザー定義型で乗算代入演算子を明示的にオーバー ロードすることはできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[複合代入](~/_csharplang/spec/expressions.md#compound-assignment)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)

---
title: ?:演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 210b7cabb658c6f068d9ab34c83050ad6267e426
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704909"
---
# <a name="-operator-c-reference"></a>?:演算子 (C# リファレンス)

条件演算子 `?:` は、一般に三項条件演算子と呼ばれ、ブール式を評価し、ブール式の評価結果 (`true` または `false`) に応じて、2 つの式のいずれかの評価結果を返します。 C# 7.2 以降、[ref 条件式](#conditional-ref-expression)は、2 つの式のいずれかの結果への参照を返します。

この条件演算子の構文は次のとおりです。

```csharp
condition ? consequence : alternative
```

`condition` 式は `true` または `false` と評価する必要があります。 `condition` が `true` と評価された場合は、`consequence` 式が評価され、その結果が演算の結果になります。 `condition` が `false` と評価された場合は、`alternative` 式が評価され、その結果が演算の結果になります。 `consequence` または `alternative` のみが評価されます。

`consequence` の型と `alternative` の型は同じ型であるか、一方の型から他方の型への暗黙の型変換が存在している必要があります。

条件演算子は右結合です。つまり、次の形式の式があるとします。

```csharp
a ? b : c ? d : e
```

これが次のように評価されます。

```csharp
a ? b : (c ? d : e)
```

条件演算子の使用例を次に示します。

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>ref 条件式

C# 7.2 以降、ref 条件式を使用して、2 つの式のいずれかの結果に対する参照を返すことができます。 この参照を [ref ローカル](../keywords/ref.md#ref-locals)または [ref readonly ローカル](../keywords/ref.md#ref-readonly-locals)変数に代入できます。または、[参照の戻り値](../keywords/ref.md#reference-return-values)または [`ref` メソッドのパラメーター](../keywords/ref.md#passing-an-argument-by-reference)として使用できます。

ref 条件式の構文は次のとおりです。

```csharp
condition ? ref consequence : ref alternative
```

元の条件演算子と同じように、ref 条件式は、2 つの式 (`consequence` または `alternative`) のいずれかのみを評価します。

ref 条件式の場合、`consequence` と`alternative` の型は同じである必要があります。

ref 条件演算子の使用例を次に示します。

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

詳細については、[機能提案メモ](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md)を参照してください。

## <a name="conditional-operator-and-an-ifelse-statement"></a>条件演算子と `if..else` ステートメント

条件演算子を [if-else](../keywords/if-else.md) ステートメントで使用すると、値の計算を条件付きで実行する必要がある場合に、コードをもっと簡潔にできる可能性があります。 次の例では、整数を負の値または負以外の値に分類するための 2 つの方法を示しています。

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

条件演算子は、オーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の「[条件演算子](~/_csharplang/spec/expressions.md#conditional-operator)」セクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [if-else ステートメント](../keywords/if-else.md)
- [?. 演算子と ?[] 演算子](null-conditional-operators.md)
- [??演算子](null-coalescing-operator.md)
- [ref キーワード](../keywords/ref.md)

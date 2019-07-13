---
title: Null 許容型の使用 - C# プログラミング ガイド
ms.custom: seodec18
description: Learn how to work with C# nullable types (C# Null 許容型の操作方法について)
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: ef7c9c18d303131b5a1c0156be820e1d475e7ec1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306652"
---
# <a name="using-nullable-types-c-programming-guide"></a>Null 許容型の使用 (C# プログラミング ガイド)

Null 許容型は、基になる値型 `T` のすべての値と、追加の [null](../../language-reference/keywords/null.md) 値を表す型です。 詳細については、「[Null 許容型](index.md)」のトピックを参照してください。

Null 許容型は、`Nullable<T>` または `T?` のいずれかの形式で参照できます。 この 2 つの形式は同義であり、どちらでも使用できます。  
  
## <a name="declaration-and-assignment"></a>宣言と代入

値型は、対応する Null 許容型に暗黙的に変換できるので、基になる値型の場合と同様に Null 許容型に値を代入します。 `null` 値を代入することもできます。  次に例を示します。
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Null 許容型の値の検査

Null 許容型のインスタンスが null かどうかを調べて、基になる型の値を取得するには、次の読み取り専用プロパティを使用します。  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> は、Null 許容型のインスタンスに、基になる型の値が含まれるかどうかを示します。
  
- <xref:System.Nullable%601.HasValue%2A> が `true` の場合、<xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> は基になる型の値を取得します。 <xref:System.Nullable%601.HasValue%2A> が `false` の場合、<xref:System.Nullable%601.Value%2A> プロパティは <xref:System.InvalidOperationException> をスローします。
  
次の例のコードでは、`HasValue` プロパティを使用して、値を表示する前に変数に値が格納されているかどうかをテストします。
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
次の例に示すように、`HasValue` プロパティを使用する代わりに、Null 許容型の変数を `null` と比較することもできます。  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

C# 7.0 以降では、[パターン マッチング](../../pattern-matching.md)を使用して Null 許容型の値を調べて取得することができます。

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Null 許容型から基になる型への変換

Null 許容型の値を Null 非許容型に代入する必要がある場合は、[Null 合体演算子 `??`](../../language-reference/operators/null-coalescing-operator.md) を使用して、Null 許容型の値が null の場合に代入される値を指定します (<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> メソッドを使用してこの操作を行うこともできます)。
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Null 許容型の値が null の場合に使用される値を、基になる値型の既定値にする場合は、<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> メソッドを使用します。
  
Null 許容型を Null 非許容型に明示的にキャストすることができます。 次に例を示します。  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

実行時に Null 許容型の値が null の場合は、明示的なキャストによって <xref:System.InvalidOperationException> がスローされます。

Null 非許容値型は、対応する Null 許容型に暗黙的に変換されます。
  
## <a name="operators"></a>演算子

値型向けに存在している定義済みの単項演算子、2 項演算子およびすべてのユーザー定義演算子は、Null 許容型でも使用できます。 これらの演算子では、1 つまたは両方のオペランドが null の場合は null 値が生成され、null 以外の場合は、含まれている値に基づいて結果が算出されます。 次に例を示します。  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> `bool?` 型の場合、定義済みの `&` および `|` 演算子は、このセクションで説明されている規則に従わないことに注意してください。オペランドの 1 つが null の場合も、演算子の評価の結果は null 以外である可能性があります。 詳細については、「[Boolean logical operators (ブール論理演算子)](../../language-reference/operators/boolean-logical-operators.md)」記事の「[Nullable Boolean logical operators (null 許容論理演算子)](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators)」セクションを参照してください。
  
関係演算子 (`<`、`>`、`<=`、`>=`) では、1 つまたは両方のオペランドが null の場合、結果は `false` になります。 ある比較 (たとえば、`<=`) から返される結果が `false` であっても、逆の比較 (`>`) から返される結果が `true` であるとは限りません。 次の例は、10 が

- null より大きくも等しくもなく、
- null 未満でもないことを示しています。
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
上記の例は、どちらも null である 2 つの null 許容型を等価比較すると、結果が `true` と評価されることを示しています。

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの「[リフトされた演算子](~/_csharplang/spec/expressions.md#lifted-operators)」セクションを参照してください。

## <a name="boxing-and-unboxing"></a>ボックス化とボックス化解除

Null 許容値型は、次の規則に従って[ボックス化](../types/boxing-and-unboxing.md)されます。

- <xref:System.Nullable%601.HasValue%2A> が `false` を返した場合は、null 参照が生成されます。  
- <xref:System.Nullable%601.HasValue%2A> が `true` を返した場合は、<xref:System.Nullable%601> のインスタンスではなく、基になる値型 `T` の値がボックス化されます。

次の例に示すように、ボックス化された値型を、対応する Null 許容型にボックス化解除できます。

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>関連項目

- [Null 許容型](index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [What Exactly Does 'Lifted' mean? ('Lifted' の正確な意味)](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)

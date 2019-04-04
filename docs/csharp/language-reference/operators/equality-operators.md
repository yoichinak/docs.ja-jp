---
title: 等値演算子 - C# リファレンス
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 98b96f5b4c6d6ea70687a97c849e89573c67c37e
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545893"
---
# <a name="equality-operators-c-reference"></a>等値演算子 (C# リファレンス)

[`==` (等価)](#equality-operator-) と [`!=` (非等値)](#inequality-operator-) 演算子は、そのオペランドが等しいかどうを確認します。

## <a name="equality-operator-"></a>等値演算子 ==

等値演算子 `==` は、そのオペランドが等しい場合には `true` を返し、それ以外の場合は `false` を返します。

### <a name="value-types-equality"></a>値の型の等価性

[組み込みの値の型](../keywords/value-types-table.md)のオペランドは、その値が等しい場合は等しくなります。

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> 等価演算子、関係演算子 `==`、`>`、`<`、`>=`、`<=` で、いずれかのオペランドが数字 (<xref:System.Double.NaN?displayProperty=nameWithType> または <xref:System.Single.NaN?displayProperty=nameWithType>) ではない場合、演算の結果は `false` になります。 つまり、`NaN` の値は、`NaN` を含む他のどの `double` (または `float`) の値を上回ることも、下回ることも、等しいこともありません。 詳細およびサンプルについては、<xref:System.Double.NaN?displayProperty=nameWithType> または <xref:System.Single.NaN?displayProperty=nameWithType> の参照記事をご覧ください。

同じ[列挙](../keywords/enum.md)型の 2 つのオペランドは、基になる整数型の対応する値が等しい場合は等しくなります。

既定ではユーザー定義 [struct](../keywords/struct.md) 型は `==` 演算子をサポートしていません。 `==` 演算子をサポートするには、ユーザー定義 struct でそれを[オーバーロード](#operator-overloadability)する必要があります。

C# 7.3 より、`==` および `!=` 演算子は C# の[タプル](../../tuples.md)によってサポートされています。 詳細については、「[C# のタプル型](../../tuples.md)」の記事の「[等値とタプル](../../tuples.md#equality-and-tuples)」のセクションを参照してください。

### <a name="string-equality"></a>文字列の等価性

2 つの [string](../keywords/string.md) オペランドは、その両方が `null` であるか、両方の文字列インスタンスの長さが同じで、それぞれの文字列の位置に同じ文字が含まれている場合に等しくなります。

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

序数の比較では大文字と小文字が区別されます。 文字列の比較に関する詳細については、「[C# で文字列を比較する方法](../../how-to/compare-strings.md)」を参照してください。

### <a name="reference-types-equality"></a>参照型の等価性

`string` 参照型オペランド以外の 2 つは、同じオブジェクトを参照しているときに等しくなります。

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

次の例は、ユーザー定義の参照型が既定で `==` 演算子をサポートしていることを示しています。 ただし、ユーザー定義の参照型は `==` 演算子をオーバーロードできます。 参照型が `==` 演算子をオーバーロードする場合、その型の 2 つの参照が同じオブジェクトを参照しているかどうかを調べるには <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> メソッドを使用します。

## <a name="inequality-operator-"></a>非等値演算子 !=

非等値演算子 `!=` は、そのオペランドが等しくない場合には `true` を返し、それ以外の場合は `false` を返します。 [組み込み型](../keywords/built-in-types-table.md)のオペランドの場合、式 `x != y` と式 `!(x == y)` では同じ結果が生成されます。 等価型の詳細については、「[等値演算子](#equality-operator-)」セクションを参照してください。

`!=` 演算子の使用例を次に示します。

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は `==` 演算子と `!=` 演算子を[オーバーロード](../keywords/operator.md)できます。 ある型でこの 2 つの演算子の 1 つをオーバーロードする場合は、もう 1 つの演算子もオーバーロードする必要があります。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの「[関係演算子と型検査演算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)」のセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [等価比較](../../programming-guide/statements-expressions-operators/equality-comparisons.md)

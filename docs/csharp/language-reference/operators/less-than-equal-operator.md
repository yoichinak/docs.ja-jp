---
title: <= 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 54c8300ad883e81cfb3d4886881984fd5a0ebdb3
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545378"
---
# <a name="-operator-c-reference"></a>\<= 演算子 (C# リファレンス)

"次の値より小さいか等しい" 関係演算子 `<=` は、最初のオペランドが 2 番目のオペランドより小さいか等しい場合に `true` を返し、それ以外の場合は `false` を返します。 すべての数値型と列挙型が `<=` 演算子をサポートします。 同じ[列挙](../keywords/enum.md)型のオペランドで、基になる整数型の対応する値が比較されます。

> [!NOTE]
> 関係演算子 `==`、`>`、`<`、`>=`、および `<=` で、いずれかのオペランドが数字 (<xref:System.Double.NaN?displayProperty=nameWithType> または <xref:System.Single.NaN?displayProperty=nameWithType>) ではない場合、演算の結果は `false` になります。 つまり、`NaN` の値はそれ以外のどの `double` (または `float`) の値を上回ることも、下回ることも、等しいこともありません。 詳細およびサンプルについては、<xref:System.Double.NaN?displayProperty=nameWithType> または <xref:System.Single.NaN?displayProperty=nameWithType> の参照記事をご覧ください。

`<=` 演算子の使用例を次に示します。

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は `<=` 演算子を[オーバーロード](../keywords/operator.md)できます。 型が "次の値より小さいか等しい" 演算子 `<=` をオーバーロードする場合、["次の値より大きいか等しい" 演算子](greater-than-equal-operator.md) `>=` もオーバーロードする必要があります。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](../language-specification/index.md)に関するページの「[関係演算子と型検査演算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)」のセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [< 演算子](less-than-operator.md)
- [== 演算子](equality-operators.md#equality-operator-)
- <xref:System.IComparable%601?displayProperty=nameWithType>

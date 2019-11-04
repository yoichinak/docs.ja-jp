---
title: select 句 - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: f1bfbeccaf6c3916a591f6447760fa01c3f8a3b6
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422366"
---
# <a name="select-clause-c-reference"></a>select 句 (C# リファレンス)

クエリ式で、`select` 句は、クエリが実行されたときに生成される値の型を指定します。 結果は、以前のすべての句の評価と `select` 句自体の式に基づいています。 クエリ式は、`select` 句または [group](group-clause.md) 句のいずれかで終了する必要があります。

次の例は、クエリ式での単純な `select` 句を示したものです。

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

`select` 句によって生成されるシーケンスの型は、クエリ変数 `queryHighScores` の型を決定します。 最も簡単なケースでは、`select` 句は、範囲変数だけを指定します。 これにより、返されるシーケンスにデータ ソースと同じ型の要素が含まれます。 詳細については、「[LINQ クエリ操作での型の関係](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。 ただし、`select` 句は、ソース データを新しい型に変換する (または*投影*する) ための強力なメカニズムも提供します。 詳細については、「[LINQ によるデータ変換 (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md)」を参照してください。

## <a name="example"></a>例

次の例は、`select` 句のすべての異なる形式を示しています。 各クエリで、`select` 句と *クエリ変数* (`studentQuery1`、`studentQuery2`など) の型の関係に注意してください。

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

前の例の `studentQuery8` に示すように、返されるシーケンスの要素にソース要素のプロパティのサブセットのみを含めることもできます。 返されるシーケンスをできるだけ小さく維持することで、メモリ要件を減らし、クエリの実行の速度を向上させることができます。 これを行うには、`select` 句で匿名型を作成し、オブジェクト初期化子を使用して、ソース要素からの適切なプロパティで初期化します。 これを行う方法の例については、「[オブジェクト初期化子とコレクション初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。

## <a name="remarks"></a>コメント

コンパイル時に、`select` 句は、<xref:System.Linq.Enumerable.Select%2A> 標準クエリ演算子へのメソッドの呼び出しに変換されます。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [クエリ キーワード (LINQ)](query-keywords.md)
- [from 句](from-clause.md)
- [partial (メソッド) (C# リファレンス)](partial-method.md)
- [匿名型](../../programming-guide/classes-and-structs/anonymous-types.md)
- [C# での LINQ](../../linq/index.md)
- [C# の LINQ の概要](/dotnet/csharp/programming-guide/concepts/linq/)

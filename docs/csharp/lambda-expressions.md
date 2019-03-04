---
title: ラムダ式
description: 引数として渡すことができる実行可能コード ブロックであるラムダ式の使用方法について説明します。
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 642422a4cc077ffebb5ee6db9d7ffb937fc1e173
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212353"
---
# <a name="lambda-expressions"></a>ラムダ式

"*ラムダ式*" は、オブジェクトとして扱われるコード ブロック (式またはステートメント ブロック) です。 これは、引数としてメソッドに渡すことができるほか、メソッドの呼び出しによって返すこともできます。 ラムダ式は、次の処理によく使用されます。

- <xref:System.Threading.Tasks.Task.Run(System.Action)> など、非同期メソッドに対して実行されるコードを渡す。

- [LINQ クエリ式](linq/index.md)を記述する。

- [式ツリー](expression-trees-building.md)を作成する。

ラムダ式は、デリゲート、またはデリゲートにコンパイルされる式ツリーとして表現できるコードです。 ラムダ式の特定のデリゲート型は、パラメーターや戻り値によって異なります。 値を返さないラムダ式は、そのパラメーター数に応じて、特定の `Action` デリゲートに対応します。 値を返すラムダ式は、そのパラメーター数に応じて、特定の `Func` デリゲートに対応します。 たとえば、2 つのパラメーターがあっても値を返さないラムダ式は、<xref:System.Action%602> デリゲートに対応します。 パラメーターが 1 つあり、値を返すラムダ式は、<xref:System.Func%602> デリゲートに対応します。

ラムダ式は、`=>` ([ラムダ宣言演算子](language-reference/operators/lambda-operator.md)) を使用して、ラムダのパラメーター リストを実行可能コードから分離します。 ラムダ式を作成するには、ラムダ演算子の左側に入力パラメーター (ある場合) を指定し、反対側に式またはステートメント ブロックを置きます。 たとえば、1 行のラムダ式 `x => x * x` は、`x` という名前のパラメーターを指定し、`x` を 2 乗した値を返します。 次の例に示すように、この式をデリゲート型に割り当てることもできます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

また、メソッドの引数として直接渡すこともできます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>式形式のラムダ

 => 演算子の右辺に式があるラムダ式を "*式形式のラムダ*" と呼びます。 式形式のラムダは、[式ツリー](expression-trees.md)の構築に幅広く使用されます。 式形式のラムダは式の結果を返します。基本的な形式は次のとおりです。

```csharp
(input parameters) => expression
```

かっこはラムダの入力パラメーターが 1 つの場合のみ省略可能で、それ以外の場合は必須です。 入力パラメーターがないことを指定するには、次のように空のかっこを使用します。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

入力パラメーターが 2 つ以上ある場合は、かっこで囲んで各パラメーターをコンマで区切ります。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

通常、コンパイラは、パラメーターの型を判定する際に型の推定を使用します。 ただし、コンパイラが入力の型を推定するのが困難または不可能な場合もあります。 このような場合は、次の例に示すように、型を明示的に指定できます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

この例では、式形式のラムダの本体をメソッド呼び出しで構成できることに注目してください。 ただし、SQL Server や Entity Framework (EF) など、.NET Framework の外部で評価される式ツリーを作成する場合は、ラムダ式内でメソッド呼び出しを使用することを控える必要があります。これは、.NET 実装のコンテキストの外部では、これらのメソッドが通用しない可能性があるためです。 この状況でメソッド呼び出しを使用する場合は、メソッド呼び出しを正常に解決できるように必ず徹底的にテストしてください。

## <a name="statement-lambdas"></a>ステートメント形式のラムダ

ステートメント形式のラムダは式形式のラムダに似ていますが、ステートメントが中かっこで囲まれる点が異なります。

```csharp
(input parameters) => { statement; }
```

ステートメント形式のラムダの本体は任意の数のステートメントで構成できますが、実際面では通常、2、3 個以下にします。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

匿名メソッドと同様、ステートメント形式のラムダを使用して式ツリーを作成することはできません。

## <a name="async-lambdas"></a>非同期ラムダ

[async](language-reference/keywords/async.md) キーワードと [await](language-reference/keywords/await.md) キーワードを使用すると、非同期処理を組み込んだラムダ式およびステートメントを簡単に作成できます。 たとえば、この例では、非同期に実行される `ShowSquares` メソッドを呼び出します。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

非同期メソッドの作成および使用方法の詳細については、「[Async および Await を使用した非同期プログラミング](programming-guide/concepts/async/index.md)」を参照してください。

## <a name="lambda-expressions-and-tuples"></a>ラムダ式とタプル

C# 7.0 以降、C# 言語はタプルの組み込みサポートを提供します。 タプルは、ラムダ式への引数として指定できるほか、ラムダ式で返すこともできます。 場合によっては、C# コンパイラは、型の推定を使用して、タプル コンポーネントの型を判定することもあります。

タプルを定義するには、そのコンポーネントのコンマ区切りリストをかっこで囲みます。 次の例では、5 つのコンポーネントを持つタプルを使用して、ラムダ式に連続した数値を渡します。このラムダ式により、各値が 2 倍になり、乗算の結果を格納する 5 つのコンポーネントを持つタプルが返されます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

通常、タプルのフィールド名は `Item1`、`Item2` のようになります。ただし、次の例のとおり、名前付きのコンポーネントを持つタプルを定義することができます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

C# におけるタプルのサポートの詳細については、「[C# Tuple types (C# のタプル型)](tuples.md)」を参照してください。

## <a name="lambdas-with-the-standard-query-operators"></a>標準クエリ演算子を使用したラムダ

いくつかある実装の中で特に、LINQ to Objects は、汎用デリゲートの <xref:System.Func%601> ファミリに属する型の入力パラメーターを持ちます。 これらのデリゲートは、型パラメーターを使用して、入力パラメーターの数と型に加え、デリゲートの戻り値の型を定義します。 `Func` デリゲートは、ソース データのセット内の各要素に適用されるユーザー定義の式をカプセル化する場合に非常に便利です。 たとえば、<xref:System.Func%601> デリゲートを考えてみます。この構文は次のとおりです。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

このデリゲートのインスタンスは、次のようなコードを使用して作成できます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

この場合、`int` は入力パラメーター、`bool` は戻り値です。 戻り値は必ず最後の型パラメーターで指定されます。 次の `Func` デリゲートを呼び出すと、入力パラメーターが 5 に等しいかどうかを示す true または false が返されます。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

たとえば、<xref:System.Linq.Queryable> 型で定義された標準クエリ演算子において、引数型が <xref:System.Linq.Expressions.Expression%601> の場合もラムダ式を使用できます。 <xref:System.Linq.Expressions.Expression%601> 引数を指定すると、ラムダは式ツリーにコンパイルされます。 次の例では、[System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) 標準クエリ演算子を使用します。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

入力パラメーターの型はコンパイラが推論できますが、明示的に指定することもできます。 この特定のラムダ式は、2 で除算したときに剰余が 1 になる整数 (`n`) をカウントします。

次の例では、`numbers` 配列内で 9 より前にある要素をすべて含むシーケンスを作成します。これは、9 がシーケンス内で条件を満たさない最初の数値であるためです。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

次の例では、複数の入力パラメーターをかっこで囲んで指定します。 このメソッドは、値が numbers 配列内のその位置を表す序数よりも小さい数値が出現するまで、その配列に含まれるすべての要素を返します。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>ラムダ式の型の推定

ラムダを記述する際、多くの場合は入力パラメーターの型を指定する必要はありません。これは、ラムダ本体やパラメーターの型など C# 言語仕様に記述されている要素に基づいて、コンパイラが型を推定できるためです。 ほとんどの標準クエリ演算子では、最初の入力がソース シーケンス内の要素の型です。 `IEnumerable<Customer>` を問い合わせると、入力変数は `Customer` オブジェクトであると推論されます。これは、そのメソッドとプロパティにアクセスできることを意味します。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

ラムダの型の推定の一般規則は、次のとおりです。

- ラムダにはデリゲート型と同じ数のパラメーターが含まれていなければなりません。

- ラムダに含まれる各入力引数は、対応するデリゲート パラメーターに暗黙的に変換できなければなりません。

- ラムダの戻り値 (ある場合) は、デリゲートの戻り値の型に暗黙的に変換できなければなりません。

共通型システムには "ラムダ式" の概念が組み込まれていないため、ラムダ式自体は型を持ちません。 しかし、変則的ではあってもラムダ式の "型" を表現できると都合が良い場合もあります。 このような場合の型は、ラムダ式の変換後のデリゲート型または <xref:System.Linq.Expressions.Expression> 型を指します。

## <a name="variable-scope-in-lambda-expressions"></a>ラムダ式における変数のスコープ

ラムダは、"*外部変数*" を参照できます (「[匿名メソッド](programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照)。外部変数とは、ラムダ関数を定義するメソッド内のスコープ、またはラムダ式を含む型のスコープに存在する変数のことです。 こうして取り込まれた変数は、ラムダ式で使用するために格納されます。これは、変数がスコープ外に出てガベージ コレクトされる場合でも変わりません。 外部変数は、ラムダ式で使用される前に明示的に代入する必要があります。 次の例は、こうした規則を示しています。

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 ラムダ式における変数のスコープには、次の規則が適用されます。

- 取り込まれた変数は、その変数を参照するデリゲートがガベージ コレクションの対象になるまでガベージ コレクトされません。

- ラムダ式内に導入された変数は、外側のメソッドでは参照できません。

- ラムダ式は、外側のメソッドの `in`、`ref`、`out` パラメーターを直接取り込むことはできません。

- ラムダ式に含まれる return ステートメントで外側のメソッドを戻すことはありません。

- ラムダ式には、 `goto` ステートメント、 `break` ステートメント、およびジャンプ ステートメントのジャンプ先がブロック外である場合はラムダ式の内部にある `continue` ステートメントを含めることはできません。 また、ジャンプ先がブロックの内部にある場合は、ラムダ式の外部でジャンプ ステートメントを使用するとエラーになります。

## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ)](../standard/using-linq.md)
- [匿名メソッド](programming-guide/statements-expressions-operators/anonymous-methods.md)
- [式ツリー](expression-trees.md)

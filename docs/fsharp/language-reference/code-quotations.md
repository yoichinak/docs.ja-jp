---
title: コード クォート
description: 言語機能を生成し、プログラムで F# コード式を処理することができますが、F# コード クォートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5523d54a271ad1c53c6de85f37f261e0ecf6cced
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490794"
---
# <a name="code-quotations"></a>コード クォート

> [!NOTE]
> API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

このトピックで説明*コード クォート*、言語機能を生成し、プログラムで F# コード式を処理することができます。 この機能を使用して、F# コードを表す抽象構文ツリーを生成できます。 抽象構文ツリーを走査し、アプリケーションのニーズに合わせて処理します。 たとえば、F# コードを生成または他の言語でコードを生成するツリーを使用できます。

## <a name="quoted-expressions"></a>引用符で囲まれた式

A*式を引用符で囲まれた*F# 式では、プログラムの一部としてコンパイルされていない方法で区切られますが、代わりに、F# の式を表すオブジェクトにコンパイルするコードです。 2 つの方法のいずれかで引用符で囲まれた式をマークすることができます。 型情報、または、型情報のいずれか。 記号を使用する型情報を含める場合は、`<@`と`@>`を引用符で囲まれた式を区切るためにします。 記号を使用する場合、型情報を使用する必要はありません、`<@@`と`@@>`します。 次のコードでは、型指定された、型指定されていない見積を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

大規模な式ツリーの走査は、高速は、型情報が含まれていない場合です。 型指定されたシンボルを使用した引用符で囲まれた式の結果の型が`Expr<'T>`、型パラメーターが F# コンパイラの型推論アルゴリズムによって決定される式の型。 引用符で囲まれた式の型は、非ジェネリック型で型情報がないコード クォートを使用して、 [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)します。 呼び出すことができます、 [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)プロパティを型指定された`Expr`クラスを取得、型指定されていない`Expr`オブジェクト。

さまざまな F# の式オブジェクトでプログラムを生成するための静的メソッドがある、`Expr`クラスを使用せずに引用式。

コード クォートが完全な式を含める必要がありますに注意してください。 `let`バインド、たとえば、する必要があるバインドの名前と、バインディングを使用する追加の式の両方の定義。 これに続く式である詳細な構文で、`in`キーワード。 トップレベル モジュール内では、これは、モジュールの次の式だけですが、引用符内では明示的に必要です。

そのため、次の式が無効です。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

次の式は無効です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

するF#引用符で囲んでが使用する必要があります、 [ F#引用符エバリュエーター](https://github.com/fsprojects/FSharp.Quotations.Evaluator)します。 評価して、実行のサポートを提供F#式オブジェクト。

## <a name="expr-type"></a>Expr 型

インスタンス、`Expr`型が F# の式を表します。 ジェネリックと非ジェネリック`Expr`型が F# ライブラリのドキュメントに記載されています。 詳細については、次を参照してください。 [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)と[Quotations.Expr クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)します。

## <a name="splicing-operators"></a>演算子のスプライス

スプライスするには、プログラムから、または別のコード クォートから作成した式のリテラル コード クォートを結合することができます。 `%`と`%%`演算子を使用すると、コード クォートに F# の式オブジェクトを追加します。 使用する、`%`型指定された引用符に型指定された式のオブジェクトを挿入する演算子です。 使用する、`%%`演算子に型指定されていないの引用符に型指定されていない式オブジェクトを挿入します。 両方の演算子は、単項前置演算子です。 そのため場合`expr`型指定されていない型の式は、 `Expr`、次のコードは無効です。

```fsharp
<@@ 1 + %%expr @@>
```

場合`expr`型の型指定された引用符が`Expr<int>`、次のコードは無効です。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、式オブジェクトに F# コードを配置し、式を表す F# コードを印刷するコード クォートの使用を示します。 関数`println`が定義されている再帰関数を格納している`print`F# の式オブジェクトを表示する (型の`Expr`) を見やすい形式でします。 いくつかのアクティブなパターンがない、 [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)と[Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)モジュール式オブジェクトを分析するために使用できます。 この例では、F# の式が表示されるすべてのパターンは含まれません。 ワイルドカード パターンに一致するものをトリガーするパターン認識されていないいずれか (`_`) を使用して表示されると、`ToString`メソッドであり、上、`Expr`型を match 式に追加するアクティブ パターンを確認できます。

### <a name="code"></a>コード

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>出力

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>例

### <a name="description"></a>説明

次の 3 つのアクティブなパターンを使用することもできます、 [ExprShape モジュール](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)少ないアクティブ パターン式ツリーを走査します。 これらのアクティブ パターンは、ツリーを走査したいが、ほとんどのノード内のすべての情報が不要な場合に役立ちます。 これらのパターンを使用する場合は次の 3 つのパターンのいずれかの任意の F# の式と一致する:`ShapeVar`式が、変数の場合`ShapeLambda`場合は、式はラムダ式、または`ShapeCombination`式が何である場合。 前のコード例のようにアクティブ パターンを使用して式ツリーを走査する場合はすべて可能な F# 式の型を処理するために多くのより多くのパターンを使用する必要が、コードが複雑になります。 詳細については、次を参照してください。 [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination アクティブ パターン](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)します。

次のコード例より複雑なトラバーサルの基礎として使用できます。 このコードで式ツリーは、関数呼び出しを含む式の作成`add`です。 [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)アクティブ パターンを使用して、任意の呼び出しを検出`add`式ツリー。 このアクティブ パターンへの呼び出しの引数の代入、`exprList`値。 この場合が 2 つだけため、これらが引き出されていると、関数には、引数に再帰的には呼び出されます。 呼び出しを表すコード クォートに結果が挿入されます`mul`スプライス演算子を使用して (`%%`)。 `println`前の例の関数を使用して、結果を表示します。

結果の式でのみ変更がから変更にアクティブ パターンの他の分岐でコードが、同じ式ツリーにだけ再生成`add`に`mul`します。

### <a name="code"></a>コード

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Output

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)

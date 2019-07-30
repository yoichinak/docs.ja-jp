---
title: コード クォート
description: 言語機能を生成し、プログラムで F# コード式を処理することができますが、F# コード クォートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630418"
---
# <a name="code-quotations"></a>コード クォート

> [!NOTE]
> API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

このトピックで説明*コード クォート*、言語機能を生成し、プログラムで F# コード式を処理することができます。 この機能を使用して、F# コードを表す抽象構文ツリーを生成できます。 次に、アプリケーションのニーズに応じて、抽象構文ツリーを走査して処理できます。 たとえば、F# コードを生成または他の言語でコードを生成するツリーを使用できます。

## <a name="quoted-expressions"></a>引用符で囲まれた式

A*式を引用符で囲まれた*F# 式では、プログラムの一部としてコンパイルされていない方法で区切られますが、代わりに、F# の式を表すオブジェクトにコンパイルするコードです。 引用符で囲まれた式は、型情報を持つか、型情報のない2つの方法のいずれかでマークできます。 型情報を含める場合は、記号`<@`と`@>`を使用して、引用符で囲まれた式を区切ります。 型情報が不要な場合は、と`<@@` `@@>`の記号を使用します。 次のコードは、型指定された型指定のない引用符を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

型情報を含めないと、大きな式ツリーを走査する方が高速になります。 型指定されたシンボルを使用した引用符で囲まれた式の結果の型が`Expr<'T>`、型パラメーターが F# コンパイラの型推論アルゴリズムによって決定される式の型。 型情報を含まないコード引用符を使用する場合、引用符で囲まれた式の型は非ジェネリック型の[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)になります。 型指定されたクラスで[Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)プロパティ`Expr`を呼び出して、型`Expr`指定のないオブジェクトを取得できます。

さまざまな F# の式オブジェクトでプログラムを生成するための静的メソッドがある、`Expr`クラスを使用せずに引用式。

コード引用符には完全な式を含める必要があることに注意してください。 `let`たとえば、バインドの場合、バインドされた名前の定義とバインドを使用する追加の式の両方が必要です。 Verbose 構文では、これは`in`キーワードに続く式です。 モジュールの最上位レベルでは、これはモジュール内の次の式にすぎませんが、引用符で囲まれている必要があります。

したがって、次の式は無効です。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

ただし、次の式は有効です。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

見積もりをF#評価するには、 [ F#見積もりエバリュエーター](https://github.com/fsprojects/FSharp.Quotations.Evaluator)を使用する必要があります。 式オブジェクトの評価と実行F#のサポートを提供します。

## <a name="expr-type"></a>Expr 型

インスタンス、`Expr`型が F# の式を表します。 ジェネリックと非ジェネリック`Expr`型が F# ライブラリのドキュメントに記載されています。 詳細については、「 [Fsharp.core 名前空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)と[引用クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)」を参照してください。

## <a name="splicing-operators"></a>スプライス演算子

スプライスを使用すると、リテラルコードの引用符を、プログラムまたは別のコード引用符から作成した式と組み合わせることができます。 `%`と`%%`演算子を使用すると、コード クォートに F# の式オブジェクトを追加します。 型指定さ`%`れた式オブジェクトを型指定された引用符に挿入するに`%%`は、演算子を使用します。型指定されていない式オブジェクトを型指定された引用符に挿入するには、演算子を使用します。 どちらの演算子も、単項前置演算子です。 このため`expr` 、が型の型`Expr`指定されていない式である場合、次のコードは有効です。

```fsharp
<@@ 1 + %%expr @@>
```

また、 `expr`が型の型`Expr<int>`指定された引用符である場合、次のコードが有効です。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、式オブジェクトに F# コードを配置し、式を表す F# コードを印刷するコード クォートの使用を示します。 関数`println`が定義されている再帰関数を格納している`print`F# の式オブジェクトを表示する (型の`Expr`) を見やすい形式でします。 [Fsharp.core](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)および[fsharp.core](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)モジュールには、式オブジェクトの分析に使用できるアクティブなパターンがいくつかありますが、これらはいくつか存在します。 この例では、F# の式が表示されるすべてのパターンは含まれません。 認識されていないパターンは、ワイルドカード`_`パターン () との一致を`ToString`トリガーし、メソッドを使用`Expr`して表示します。このメソッドを使用すると、一致式に追加するアクティブパターンを知ることができます。

### <a name="code"></a>コード

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>出力

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>例

### <a name="description"></a>説明

また、 [Exprshape モジュール](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)内の3つのアクティブパターンを使用して、アクティブなパターンが少数の式ツリーを走査することもできます。 これらのアクティブなパターンは、ツリーを走査するときに、ほとんどのノードの情報をすべて必要としない場合に便利です。 これらのパターンを使用する場合は次の 3 つのパターンのいずれかの任意の F# の式と一致する:`ShapeVar`式が、変数の場合`ShapeLambda`場合は、式はラムダ式、または`ShapeCombination`式が何である場合。 前のコード例のようにアクティブ パターンを使用して式ツリーを走査する場合はすべて可能な F# 式の型を処理するために多くのより多くのパターンを使用する必要が、コードが複雑になります。 詳細については、「 [Exprshape. スナップショット&#124;&#124;](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)」を参照してください。

次のコード例は、より複雑なトラバーサルの基礎として使用できます。 このコードでは、関数呼び出し`add`を含む式に対して式ツリーが作成されます。 特定の[呼び出し](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)のアクティブパターンは、式ツリー内の`add`への呼び出しを検出するために使用されます。 このアクティブパターンは、呼び出しの引数を`exprList`値に割り当てます。 この場合は、2つしか存在しないため、これらの関数は引数に対して再帰的に呼び出されます。 結果は、スプライス演算子 ( `mul` `%%`) を使用したへの呼び出しを表すコード引用符に挿入されます。 前の例の関数は、結果を表示するために使用されます。`println`

もう一方のアクティブパターン分岐のコードは同じ式ツリーを再生成するだけなので、結果として得ら`add`れる`mul`式の変更はからに変更されるだけです。

### <a name="code"></a>コード

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Output

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)

---
title: コンピュテーション式
description: 制御フローの構造とバインディングを使用してF#シーケンス処理および結合できる、で計算を記述するための便利な構文を作成する方法について説明します。
ms.date: 03/15/2019
ms.openlocfilehash: bca328a09ff61fb76d30960221ee3350fcc25fc1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106571"
---
# <a name="computation-expressions"></a>コンピュテーション式

のF#コンピュテーション式は、制御フローの構造とバインディングを使用して、シーケンス処理および結合できる計算を作成するための便利な構文を提供します。 計算式の種類によっては、monads、モノ id、monads トランスフォーマー、およびアプリケーションを表現する方法と考えることができます。 ただし、Haskell のような他の言語とは異なり、それらは1つの抽象化に関連付けられておらず、マクロやその他の形式のメタプログラミングに依存せず、便利で状況依存の構文を実現できません。

## <a name="overview"></a>概要

計算には多くの形式が必要です。 最も一般的な計算形式は、簡単に理解して変更できるシングルスレッド実行です。 ただし、すべての形式の計算は、シングルスレッド実行と単純なものではありません。 次に、それらの例の一部を示します。

- 非決定的な計算
- 非同期計算
- Effectful の計算
- 注釈の計算

一般に、アプリケーションの特定の部分で実行する必要がある*状況依存*の計算があります。 コンテキストに依存するコードを記述することは困難な場合があります。これは、特定のコンテキストの外では、抽象化を行わずに "リーク" の計算を簡単に行うことができるためです。 これらの抽象化は、自分が F# には、実行する一般的な方法と呼ばれるものを記述する多くの場合、時間がかかります**コンピュテーション式**します。

コンピュテーション式は、文脈に依存した計算をエンコードするための統一された構文と抽象化モデルを提供します。

すべての計算式は、*ビルダー*型によってサポートされます。 ビルダーの型は、コンピュテーション式で使用できる操作を定義します。 「[コンピュテーション式の新しい型の作成](computation-expressions.md#creating-a-new-type-of-computation-expression)」を参照してください。これは、カスタム計算式の作成方法を示しています。

### <a name="syntax-overview"></a>構文の概要

すべての計算式の形式は次のとおりです。

```
builder-expr { cexper }
```

ここ`builder-expr`で、はコンピュテーション式`cexper`を定義するビルダー型の名前、はコンピュテーション式の式本体です。 たとえば、 `async`コンピュテーション式のコードは次のようになります。

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

前の例で示したように、コンピュテーション式内で使用できる特殊な追加の構文があります。 コンピュテーション式では、次の式の形式を使用できます。

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

これらのキーワードおよびその他の標準の F# キーワードの各はバッキング ビルダー型で定義されている場合のみコンピュテーション式で使用できます。 唯一の`match!` `let!`例外は、を使用するための構文砂糖です。その後、結果にパターン一致を指定します。

ビルダーの型は、コンピュテーション式のフラグメントの結合方法を制御する特殊なメソッドを定義するオブジェクトです。つまり、そのメソッドは、コンピュテーション式の動作を制御します。 ビルダー クラスを記述する別の方法は、多く F# の構成要素、ループやバインドなどの操作をカスタマイズできるには。

### `let!`

キーワード`let!`は、別のコンピュテーション式への呼び出しの結果を名前にバインドします。

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

を使用`let`してコンピュテーション式に呼び出しをバインドすると、コンピュテーション式の結果は得られません。 代わりに、そのコンピュテーション式に対して、*実現*されていない呼び出しの値をバインドします。 を`let!`使用して、結果にバインドします。

`let!`は、 `Bind(x, f)`ビルダー型のメンバーによって定義されます。

### `do!`

キーワードは、(ビルダーの`Zero`メンバーによって定義`unit`された) like 型を返すコンピュテーション式を呼び出すためのものです。 `do!`

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

[非同期ワークフロー](asynchronous-workflows.md)の場合、この型は`Async<unit>`です。 その他の計算式の場合、型はに`CExpType<unit>`なる可能性があります。

`do!`は、ビルダー型`Bind(x, f)`のメンバーによって定義さ`f`れます`unit`。ここで、はを生成します。

### `yield`

キーワードは、計算式から値を返して、 <xref:System.Collections.Generic.IEnumerable%601>として使用できるようにするためのものです。 `yield`

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

[ C#で yield キーワード](../../csharp/language-reference/keywords/yield.md)を使用する場合と同様に、コンピュテーション式の各要素は反復処理されるときに返されます。

`yield`は、ビルダーの`Yield(x)`型のメンバーによって定義`x`されます。ここで、は、返される項目です。

### `yield!`

キーワード`yield!`は、コンピュテーション式から値のコレクションをフラット化するためのものです。

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

評価されると、によって`yield!`呼び出されるコンピュテーション式の項目は1つずつ返され、結果がフラット化されます。

`yield!`は、ビルダーの`YieldFrom(x)`型のメンバーによって定義`x`されます。ここで、は値のコレクションです。

### `return`

キーワード`return`は、コンピュテーション式に対応する型の値をラップします。 を使用し`yield`た計算式とは別に、計算式を "完了" するために使用されます。

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`は、ビルダーの`Return(x)`型のメンバーによって定義`x`されます。ここで、はラップする項目です。

### `return!`

キーワード`return!`は、コンピュテーション式の値を認識し、その結果を、コンピュテーション式に対応する型にラップします。

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`は、ビルダーの`ReturnFrom(x)`型のメンバーによって定義`x`されます。ここで、は別のコンピュテーション式です。

### `match!`

F# 4.5 以降では、 `match!`キーワードを使用して別のコンピュテーション式の呼び出しをインライン化し、結果にパターン一致を行うことができます。

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

で`match!`コンピュテーション式を呼び出すと、のような`let!`呼び出しの結果が認識されます。 これは、通常、結果が[省略可能](options.md)であるコンピュテーション式を呼び出すときに使用されます。

## <a name="built-in-computation-expressions"></a>組み込みのコンピュテーション式

コアF#ライブラリでは、次の3つの組み込みのコンピュテーション式が定義されています。[シーケンス式](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[クエリ式](query-expressions.md)。

## <a name="creating-a-new-type-of-computation-expression"></a>新しい種類のコンピュテーション式の作成

ビルダークラスを作成し、クラスに特定の特別なメソッドを定義することで、独自のコンピュテーション式の特性を定義できます。 ビルダークラスでは、次の表に示すように、必要に応じてメソッドを定義できます。

次の表では、ワークフロービルダークラスで使用できるメソッドについて説明します。

|**メソッド**|**一般的な署名**|**説明**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|コンピュテーション式`let!`で`do!`およびに対して呼び出されます。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|計算式を関数としてラップします。|
|`Return`|`'T -> M<'T>`|コンピュテーション式`return`でに対して呼び出されます。|
|`ReturnFrom`|`M<'T> -> M<'T>`|コンピュテーション式`return!`でに対して呼び出されます。|
|`Run`|`M<'T> -> M<'T>` または<br /><br />`M<'T> -> 'T`|コンピュテーション式を実行します。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` または<br /><br />`M<unit> * M<'T> -> M<'T>`|コンピュテーション式でシーケンス処理を行うために呼び出されます。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` または<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|コンピュテーション式`for...do`の式に対して呼び出されます。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|コンピュテーション式`try...finally`の式に対して呼び出されます。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|コンピュテーション式`try...with`の式に対して呼び出されます。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|コンピュテーション式`use`の束縛に対して呼び出されます。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|コンピュテーション式`while...do`の式に対して呼び出されます。|
|`Yield`|`'T -> M<'T>`|コンピュテーション式`yield`の式に対して呼び出されます。|
|`YieldFrom`|`M<'T> -> M<'T>`|コンピュテーション式`yield!`の式に対して呼び出されます。|
|`Zero`|`unit -> M<'T>`|コンピュテーション式の`else`式の`if...then`空の分岐に対して呼び出されます。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|コンピュテーション式が`Run`メンバーに引用符として渡されることを示します。 計算のすべてのインスタンスを引用符に変換します。|

ビルダークラスのメソッドの多くは、 `M<'T>`構造体を使用して返します。通常、これは、非同期ワークフローやなど、結合`Async<'T>`する計算の種類を特徴と`Seq<'T>`する個別に定義された型です。シーケンスワークフローの場合。 これらのメソッドのシグネチャを使用すると、1つのコンストラクトから返されるワークフローオブジェクトを次の構造体に渡すことができるように、それらを組み合わせて入れ子にすることができます。 コンパイラは、コンピュテーション式を解析するときに、前の表のメソッドとコンピュテーション式のコードを使用して、一連の入れ子になった関数呼び出しに式を変換します。

入れ子になった式の形式は次のとおりです。

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

上記のコードでは、コンピュテーション式`Run`ビルダー `Delay`クラスでが定義されていない場合、およびの呼び出しは省略されます。 ここではと示されて`{| cexpr |}`いるコンピュテーション式の本体は、次の表で説明する変換によって、ビルダークラスのメソッドを含む呼び出しに変換されます。 コンピュテーション式`{| cexpr |}`に従ってこれらの変換を再帰的に定義されているは、 `expr` F# の式と`cexpr`計算式です。

|正規表現|変換|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

前の表では`other-expr` 、表に記載されていない式について説明します。 ビルダークラスは、すべてのメソッドを実装する必要はなく、前の表に一覧表示されているすべての変換をサポートします。 実装されていない構造体は、その型のコンピュテーション式では使用できません。 たとえば、計算式で`use`キーワードをサポートしない場合は、の`Use`定義をビルダークラスで省略できます。

次のコード例は、一度に1ステップずつ評価できる一連のステップとして計算をカプセル化するコンピュテーション式を示しています。 判別共用体型`OkOrException`は、これまでに評価された式のエラー状態をエンコードします。 このコードは、いくつかのビルダーメソッドの定型的な実装など、計算式で使用できる一般的なパターンを示しています。

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step 
```

コンピュテーション式には基になる型があり、この式はを返します。 基になる型は、計算された結果または実行可能な遅延計算を表すことができます。また、一部の型のコレクションを反復処理する方法を提供する場合もあります。 前の例では、基になる型は**最終的**にでした。 シーケンス式の場合、基になる型<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>はです。 クエリ式の場合、基になる型<xref:System.Linq.IQueryable?displayProperty=nameWithType>はです。 非同期ワークフローの場合、基になる型[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)はです。 オブジェクト`Async`は、結果を計算するために実行する作業を表します。 たとえば、を呼び出し[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)て計算を実行し、その結果を返します。

## <a name="custom-operations"></a>カスタム操作

コンピュテーション式でカスタム操作を定義し、コンピュテーション式で演算子としてカスタム操作を使用することができます。 たとえば、クエリ式にクエリ演算子を含めることができます。 カスタム操作を定義する場合は、コンピュテーション式の Yield メソッドと For メソッドを定義する必要があります。 カスタム操作を定義するには、それをコンピュテーション式のビルダークラスに配置し、を適用[`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)します。 この属性は、引数として文字列を受け取ります。これはカスタム操作で使用される名前です。 この名前は、コンピュテーション式の左中かっこの先頭にあるスコープに含まれます。 したがって、このブロック内のカスタム操作と同じ名前を持つ識別子は使用しないでください。 たとえば、クエリ式で`all`や`last`などの識別子を使用しないようにします。

### <a name="extending-existing-builders-with-new-custom-operations"></a>新しいカスタム操作を使用した既存のビルダーの拡張

既にビルダークラスがある場合は、そのカスタム操作をこのビルダークラスの外部から拡張できます。 拡張機能はモジュール内で宣言する必要があります。 名前空間には、同じファイルと、型が定義されている同じ名前空間宣言グループ以外の拡張メンバーを含めることはできません。

次の例は、既存`Microsoft.FSharp.Linq.QueryBuilder`のクラスの拡張を示しています。

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [非同期ワークフロー](asynchronous-workflows.md)
- [シーケンス](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [クエリ式](query-expressions.md)

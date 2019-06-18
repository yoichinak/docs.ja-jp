---
title: コンピュテーション式
description: 計算を作成するための便利な構文を作成する方法についてF#、制御できることがシーケンス処理されたと結合を使用してフローの作成とバインドします。
ms.date: 03/15/2019
ms.openlocfilehash: b352c5541bc31b5c583904b99651de9180c8afb3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152030"
---
# <a name="computation-expressions"></a>コンピュテーション式

コンピュテーション式でF#シーケンス処理できるし、制御フローの作成とバインドを使用して結合する計算を作成するための便利な構文を提供します。 コンピュテーション式の種類、に応じてには、モナド、monoids、monad トランスフォーマー、および適用したファンクターを表現する手段として、考えるができます。 その他の言語とは異なり、(など*do 表記*Haskell で)、単一の抽象化に関連付けられていない、マクロやその他の形式に依存しないメタプログラミングを便利で状況依存の構文を実現します。

## <a name="overview"></a>概要

計算には、多くの形式を取ります。 計算の最も一般的な形式は、シングル スレッド実行は簡単に理解して変更できます。 ただし、すべての形態の計算はシングル スレッド実行するように単純です。 次に、それらの例の一部を示します。

* 非決定論的な計算
* 非同期計算
* Effectful 計算
* 当初の計算

一般的には、ある*状況に応じた*計算アプリケーションの特定の部分で実行する必要があります。 状況依存のコードの記述はそうことを防止するための抽象化せず、特定のコンテキストの外部で「リーク」計算を簡単に難しいことができます。 これらの抽象化は、自分が F# には、実行する一般的な方法と呼ばれるものを記述する多くの場合、時間がかかります**コンピュテーション式**します。

コンピュテーション式では、状況依存の計算をエンコードするための統一された構文と抽象化モデルを提供します。

すべての計算式を支え、*ビルダー*型。 ビルダーの型は、そのコンピュテーション式で利用可能な操作を定義します。 参照してください[コンピュテーション式の新しい型を作成する](computation-expressions.md#creating-a-new-type-of-computation-expression)、カスタム計算式を作成する方法します。

### <a name="syntax-overview"></a>構文の概要

すべての計算式では、次の形式があります。

```
builder-expr { cexper }
```

場所`builder-expr`そのコンピュテーション式を定義するビルダー型の名前を指定および`cexper`コンピュテーション式の式の本文です。 たとえば、`async`式のコードを計算できるようになります。

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

その他の特別な構文、コンピュテーション式内で使用可能な前の例で示すように。 次の式のフォームがコンピュテーション式と考えられます。

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

これらのキーワードおよびその他の標準の F# キーワードの各はバッキング ビルダー型で定義されている場合のみコンピュテーション式で使用できます。 唯一の例外は`match!`、糖衣構文の使用は`let!`結果で、パターン一致の後にします。

ビルダーの型はコンピュテーション式のフラグメントを結合する方法を制御する特殊なメソッドを定義するオブジェクトです。つまり、そのメソッドは、コンピュテーション式の動作方法を制御します。 ビルダー クラスを記述する別の方法は、多く F# の構成要素、ループやバインドなどの操作をカスタマイズできるには。

### `let!`

`let!`キーワード名に別のコンピュテーション式の呼び出しの結果をバインドします。

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

コンピュテーション式での呼び出しをバインドするかどうかは`let`コンピュテーション式の結果は表示されません。 代わりにバインドしてからの値、*実現されていない*そのコンピュテーション式を呼び出します。 使用`let!`結果にバインドします。

`let!` `Bind(x, f)`ビルダー型のメンバー。

### `do!`

`do!`キーワードはコンピュテーション式の呼び出しを返します、 `unit`-などの型 (によって定義された、`Zero`ビルダーでのメンバー)。

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

[非同期ワークフロー](asynchronous-workflows.md)、この型は`Async<unit>`します。 その他のコンピュテーション式の型がある可能性があります`CExpType<unit>`します。

`do!` によって定義されます、`Bind(x, f)`ビルダーの型のメンバー、`f`生成、`unit`します。

### `yield`

`yield`として利用できるように、コンピュテーション式から値を返すためのキーワードは、 <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

同様、 [yield キーワード (C#)](../../csharp/language-reference/keywords/yield.md)、それが反復処理にそのコンピュテーション式内の各要素が返されます。

`yield` によって定義されます、`Yield(x)`ビルダーの型のメンバー、`x`はバックアップを生成する項目です。

### `yield!`

`yield!`キーワードがコンピュテーション式から値のコレクションをフラット化するためには。

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

そのコンピュテーション式と呼ばれる評価されると、`yield!`がその項目になり、戻る 1 つずつ、結果をフラット化します。

`yield!` によって定義されます、`YieldFrom(x)`ビルダーの型のメンバー、`x`値のコレクションです。

### `return`

`return`キーワード コンピュテーション式に対応する型の値をラップします。 使用して計算式とは別に`yield`コンピュテーション式を「完了」に使用されます。

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` によって定義されます、`Return(x)`ビルダーの型のメンバー、`x`をラップする項目。

### `return!`

`return!`キーワード コンピュテーション式の値を認識およびコンピュテーション式に対応する型でその結果をラップします。

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` によって定義されます、`ReturnFrom(x)`ビルダーの型のメンバー、`x`別の計算式です。

### `match!`

以降でF#、4.5、`match!`キーワードを使用するインラインを別の計算式とパターン一致の結果への呼び出し。

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

計算式を呼び出すときに`match!`のような呼び出しの結果を実現は`let!`します。 これは、多くの場合、使用結果がコンピュテーション式を呼び出すときに、[省略可能な](options.md)します。

## <a name="built-in-computation-expressions"></a>組み込みのコンピュテーション式

F#コア ライブラリが 3 つの組み込みのコンピュテーション式を定義します。[シーケンス式](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[クエリ式](query-expressions.md)します。

## <a name="creating-a-new-type-of-computation-expression"></a>コンピュテーション式の新しい型を作成します。

ビルダー クラスを作成し、クラスの特定の特殊なメソッドを定義することは、独自のコンピュテーション式の特性を定義できます。 必要に応じて、ビルダー クラスは、次の表に記載されている、メソッドを定義します。

次の表では、ワークフロー ビルダー クラスで使用できるメソッドについて説明します。

|**メソッド**|**通常のシグネチャ**|**説明**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|に対して呼び出されて`let!`と`do!`コンピュテーション式で。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|コンピュテーション式として関数をラップします。|
|`Return`|`'T -> M<'T>`|に対して呼び出されて`return`コンピュテーション式で。|
|`ReturnFrom`|`M<'T> -> M<'T>`|に対して呼び出されて`return!`コンピュテーション式で。|
|`Run`|`M<'T> -> M<'T>` または<br /><br />`M<'T> -> 'T`|コンピュテーション式を実行します。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` または<br /><br />`M<unit> * M<'T> -> M<'T>`|コンピュテーション式でシーケンス処理と呼ばれます。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` または<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|に対して呼び出されて`for...do`コンピュテーション式内の式。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|に対して呼び出されて`try...finally`コンピュテーション式内の式。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|に対して呼び出されて`try...with`コンピュテーション式内の式。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|に対して呼び出されて`use`コンピュテーション式でバインドします。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|に対して呼び出されて`while...do`コンピュテーション式内の式。|
|`Yield`|`'T -> M<'T>`|に対して呼び出されて`yield`コンピュテーション式内の式。|
|`YieldFrom`|`M<'T> -> M<'T>`|に対して呼び出されて`yield!`コンピュテーション式内の式。|
|`Zero`|`unit -> M<'T>`|空のという`else`の分岐`if...then`コンピュテーション式内の式。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|コンピュテーション式に渡されることを示します、`Run`引用符としてメンバー。 見積に計算のすべてのインスタンスを変換します。|

ビルダー クラスのメソッドの多くを使用し、返す、`M<'T>`コンス トラクターは、たとえば、結合している計算の種類の特性を設定するとは別に定義されている型は通常、`Async<'T>`ための非同期ワークフローと`Seq<'T>`ワークフローのシーケンス。 これらのメソッドのシグネチャは、1 つの構築から返されるワークフロー オブジェクトは、次に渡すことができるようにそれらを結合し、相互に入れ子に有効にします。 計算式を解析するとき、コンパイラは、上記の表に、メソッドとそのコンピュテーション式のコードを使用して、一連の入れ子になった関数呼び出しに式を変換します。

入れ子になった式は、次の形式では。

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

上記のコードへの呼び出しで`Run`と`Delay`計算式ビルダー クラスで定義されていない場合は省略します。 としてここで示される、計算式の本体`{| cexpr |}`は、次の表で説明されている翻訳によってビルダー クラスのメソッドに関連する呼び出しに変換されます。 コンピュテーション式`{| cexpr |}`に従ってこれらの変換を再帰的に定義されているは、 `expr` F# の式と`cexpr`計算式です。

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

前の表に`other-expr`それ以外の場合、表に一覧表示されない式について説明します。 ビルダー クラスは、すべてのメソッドを実装し、前の表に、翻訳のすべてをサポートする必要はありません。 実装されていないこれらのコンストラクトでは、その型のコンピュテーション式で使用できません。 例では、サポートしない場合、 `use` 、コンピュテーション式、キーワードの定義を省略できます`Use`ビルダー クラスにします。

次のコード例では、一連のことができる手順を一度に 1 つのステップを評価すると、計算をカプセル化する計算式を示します。 A 判別共用体型、 `OkOrException`、これまでに評価された式のエラー状態をエンコードします。 このコードは、ビルダー メソッドのいくつかの定型実装など、コンピュテーション式で使用できるいくつかの一般的なパターンを示しています。

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

コンピュテーション式には、式から返される、基になる型があります。 計算の結果または遅延の計算を実行できる、基になる型を表すことがあります。 または何らかの種類のコレクションを反復処理する方法を提供できます。 前の例では、基になる型が**最終的に**します。 シーケンス式では、基になる型は<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>します。 クエリ式では、基になる型は<xref:System.Linq.IQueryable?displayProperty=nameWithType>します。 非同期ワークフローでは、基になる型は[ `Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)します。 `Async`オブジェクトは、結果を計算するために実行する作業を表します。 たとえば、呼び出す[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)計算を実行し、結果が返されます。

## <a name="custom-operations"></a>カスタム操作

コンピュテーション式のカスタム処理を定義し、オペレーターはコンピュテーション式でカスタム操作を使用できます。 たとえば、クエリ式でクエリ演算子を含めることができます。 カスタム操作を定義するときに、Yield を定義する必要がありますとコンピュテーション式内のメソッド。 カスタム操作を定義するには、そのコンピュテーション式のビルダー クラスに配置し、適用、 [ `CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)します。 この属性は、カスタム操作で使用する名前を引数として文字列を受け取ります。 この名前は、そのコンピュテーション式の中かっこの開始時のスコープに渡されます。 そのため、このブロックでカスタム操作と同じ名前を指定する識別子を使用しないでください。 たとえばなどの識別子の使用を避ける`all`または`last`クエリ式で。

### <a name="extending-existing-builders-with-new-custom-operations"></a>新しいカスタム操作で既存のビルダーを拡張します。

ビルダー クラスは、既にある場合は、このビルダー クラスの外部からのカスタム操作が拡張できます。 拡張機能は、モジュール内で宣言する必要があります。 名前空間には、同じファイルで、型が定義されている同じ名前空間宣言のグループを除く拡張メンバーを含めることはできません。

次の例は、既存の拡張機能`Microsoft.FSharp.Linq.QueryBuilder`クラス。

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

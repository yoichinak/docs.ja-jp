---

title: F# での非同期プログラミング
description: F#がコア関数型プログラミングの概念から派生した言語レベルのプログラミングモデルに基づいて、非同期性のクリーンなサポートを提供する方法について説明します。

ms.date: 12/17/2018
ms.openlocfilehash: 1ede4a5c1e26df271ac94f9b2c216ac84fb38f59
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395790"
---
# <a name="async-programming-in-f"></a>F#での非同期プログラミング

非同期プログラミングは、さまざまな理由で、最新のアプリケーションに不可欠なメカニズムです。 ほとんどの開発者が直面する主なユースケースには、次の2つがあります。

- 多数の同時受信要求を処理できるサーバープロセスを提供する一方で、要求の処理中に使用されるシステムリソースを最小限に抑えながら、そのプロセスの外部のシステムまたはサービスからの入力を待機する
- バックグラウンド作業の同時進行中に応答性の高い UI またはメインスレッドを維持する

多くの場合、バックグラウンド作業には複数のスレッドの使用が含まれますが、非同期性とマルチスレッドの概念を個別に考慮することが重要です。 実際、別々の検討事項であり、互いに他社を意味する訳ではありません。 この記事では、この事についてさらに詳しく説明します。

## <a name="asynchrony-defined"></a>非同期性の定義

非同期性はマルチスレッドの利用と独立である、という点に関してもう少し説明しておいた方が良いでしょう。 関連することがある3つの概念がありますが、これらは厳密には独立した概念です。

- 並行処理: 複数の計算がオーバーラップする時間帯に実行される。
- 並列処理: 複数の計算または一つの計算の複数の部分が厳密の同じ時間に実行される。
- 非同期処理: メインのプログラムとは別に、一つ以上の計算が実行される。

これら3つは直交概念ですが、一緒に用いてしてしまうと簡単に混同してしまう場合があります。たとえば、複数の非同期計算を並行して実行することが必要になる場合があります。 これは、並列処理または非同期処理が互いを意味するという意味ではありません。

"非同期" という語の語源を考慮すると、次の2つの部分が関係します。

- 「ない」を意味する"a"
- 「同時に」を意味する"synchronous"

これらの2つの用語をまとめると、"非同期" とは "同時に実行しない" ことを意味します。 たったこれだけです！この定義には、並行処理も並列処理もありません。 このことは実際にも当てはまるのです。

実際には、F#の非同期計算処理はメインプログラムフローとは別に実行するようにスケジューリングされます。 これは、並行処理も並列処理も意味しません。 また、常にバックグラウンドで処理される事も意味しません。 実際、非同期計算処理は、計算処理の性質と計算処理が実行されている環境によっては同期的に実行される事もあり得ます。

重要なことは、非同期計算はメインプログラムフローと独立していることです。 非同期計算がいつまたはどのように実行されるかに関する保証はほとんどありませんが、それらを調整しスケジューリングするためのアプローチがいくつかあります。 この記事の残りの部分では、 F#の非同期処理に関する主要な概念と、F#に組み込まれている型、関数、および式の使用方法について説明します。

## <a name="core-concepts"></a>主要な概念

F#では、非同期プログラミングは次の3つの主要な概念を中心にしています。

- `Async<'T>`型。これは、コンポーザブルな非同期計算を表します。
- `Async`モジュール関数。これを使用すると、非同期処理のスケジューリング、非同期計算の作成、および非同期結果の変換を実行できます。
- `async { }`[コンピュテーション式](../../language-reference/computation-expressions.md)。非同期計算を構築および制御するための便利な構文を提供します。

これら3つの概念を次の例で確認する事ができます。

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

この例では、`printTotalFileBytes` 関数の型は `string -> Async<unit>` です。 関数を呼び出すだけでは、実際には非同期計算は実行されません。 その代わりに、非同期処理の *仕様* として機能する `Async<unit>` を返します。 このメソッドは、本文で `Async.AwaitTask` を呼び出します。これにより、<xref:System.IO.File.WriteAllBytesAsync> が呼び出された時に、その結果が適切な型に変換されます。

もう1つの重要な行は `Async.RunSynchronously` の呼び出しです。 これは、 F#の非同期計算を実際に実行する際に呼び出す必要のある Asyncモジュール開始関数の1つです。

これはC#/VB スタイルの `async` プログラミングとの根本的に異なる点です。 F#では、非同期計算は**コールド(冷たい)タスク**として考えることができます。 これらを実際に実行するには、明示的に開始する必要があります。 これには、C#/VBよりもはるかに簡単に非同期作業を組み合わせることができるという利点があります。

## <a name="combining-asynchronous-computations"></a>非同期計算の組み合わせ

次に、上記の例をもとに計算処理を組み合わせる例を示します。

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

ご覧のように、`main` 関数には、さらに多くの呼び出しが行われています。 概念的には、次のことが行われます。

1. `Array.map` でコマンドライン引数を `Array<unit>` 型の計算に変換します。
2. 実行時に `printTotalFileBytes` の計算を並列でスケジューリングして処理するように `Async<'T[]>` を生成します。
3. `Array<unit>` を生成しますが、これは並列計算を実行してその結果を無視します。
4. `Async.RunSynchronously` で最後の計算を明示的に実行し、完了するまでブロックします。

このプログラムを実行すると、コマンドライン引数ごとに `printTotalFileBytes` が並列実行されます。 非同期計算はプログラムフローとは無関係に実行されるため、それぞれ情報を出力して終了すのに順序は決まりません。 計算処理は並列にスケジューリングされるが、その実行順序は保証されないのです。

## <a name="sequencing-asynchronous-computations"></a>非同期計算の順序処理

`Array<'T>` は既に実行されているタスクというよりはむしろ作業の仕様を表しているので、より複雑な変換を簡単に実行する事ができます。 一連の非同期計算を順序化して、1つずつ実行する例を次に示します。

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.RunSynchronously
    |> ignore
```

この例では `printTotalFileBytes` が `argv` の要素の順序で実行されるようにスケジューリングされます。並列でスケジューリングする必要はありません。 次の項目は、最後の計算の実行が完了するまではスケジューリングされないので、一連の計算は実行時間が重複しないようにシーケンス処理されます。

## <a name="important-async-module-functions"></a>重要なAsyncモジュール関数

F#で非同期コードを記述する時、通常は計算のスケジューリングを自動的に行うフレームワークを用います。 ただし、これは常にであるとは限りません。そのため、非同期処理をスケジューリングするためのさまざまな開始関数について学習することをお勧めします。

F#の非同期計算は、既に実行されている作業を表すのではなく、作業の_仕様_を表しているので、開始関数を使用して明示的に開始する必要があります。 さまざまなコンテキストで役に立つ[Async開始関数](https://msdn.microsoft.com/library/ee370232.aspx)が多数あります。 次のセクションでは、より一般的な開始関数のいくつかについて説明します。

### <a name="asyncstartchild"></a>Async.StartChild

非同期計算内で子計算を開始します。 これを用いて複数の非同期計算を同時に実行する事ができます。 子の計算では、キャンセルトークンを親計算と共有しています。 親の計算が取り消された場合は、子の計算も取り消されます。

型シグニチャ:

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

いつ使うか:

- 一度に1つずつではなく、複数の非同期計算を同時に実行するが、並列でスケジューリングされない場合。
- 子計算の有効期間を親計算の有効期間に関連付ける場合。

注意事項:

- `Async.StartChild` を使用して複数の計算を開始することは、並列にスケジューリングすることと同等ではありません。 計算を並列でスケジューリングするには、`Async.Parallel` を使用します。
- 親計算を取り消すと、開始したすべての子計算の取り消しをトリガーします。

### <a name="asyncstartimmediate"></a>Async.StartImmediate

現在のOSのスレッドですぐに開始して非同期計算を実行します。 これは、計算中に呼び出し元のスレッドで何かを更新する必要がある場合に便利です。 たとえば、非同期計算で UI を更新する必要がある場合 (進行状況バーを更新するなど)、`Async.StartImmediate` を使用する必要があります。

型シグニチャ:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

いつ使うか:

- 非同期計算の途中で、呼び出し元のスレッドで何かを更新する必要がある場合。

注意事項:

- 非同期計算のコードは、スケジューリングされている任意のスレッドで実行されます。 これは、そのスレッドが UI スレッドなど、何らかの方法で重要な場合に問題になることがあります。 このような場合は、`Async.StartImmediate` を使用するのが不適切である可能性があります。

### <a name="asyncstartastask"></a>Async.StartAsTask

スレッドプールで計算を実行します。 計算が終了した後、対応する状態で完了する `Task<TResult>` を返します (結果を生成するか、例外をスローするか、または取り消されます)。 キャンセルトークンが指定されていない場合は、デフォルトのキャンセルトークンが使用されます。

型シグニチャ:

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

いつ使うか:

- 非同期計算の結果として `Task<TResult>` を想定する .NET API を呼び出す必要がある場合。

注意事項:

- この呼び出しでは、追加の `Task` オブジェクトを割り当てます。よってこれを頻繁に使用される場合にオーバーヘッドが増加する可能性があります。

### <a name="asyncparallel"></a>Async.Parallel

並列で実行される一連の非同期計算をスケジューリングします。 `maxDegreesOfParallelism` パラメーターを指定することによって、必要に応じて並列処理の次数をチューニング/調整できます。

型シグニチャ:

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

いつ使うか:

- 一連の計算を同時に実行する必要があるが、実行の順序に依存しない場合。
- すべてが完了するまで並列でスケジューリングされた計算結果を必要としない場合。

注意事項:

- すべての計算が完了するまで、結果として得られる値の配列にアクセスできません。
- 計算は実行されますが、スケジュールが設定されます。 つまり、実行の順序に依存することはできません。

### <a name="asyncsequential"></a>Async.Sequential

一連の非同期計算を渡された順序で実行されるようにスケジューリングします。 最初の計算を実行し、その後、その次という具合です。 計算は並列実行されません。

型シグニチャ:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

いつ使うか:

- 複数の計算を順番に実行する必要がある場合。

注意事項:

- すべての計算が完了するまで、結果として得られる値の配列にアクセスできません。
- 計算は、この関数に渡される順序で実行されます。そのため、結果が返されるまでに時間がかかることがあります。

### <a name="asyncawaittask"></a>Async.AwaitTask

指定された <xref:System.Threading.Tasks.Task> が完了するまで待機し、その結果を `Async<'T>` として返すような非同期計算を返します。

型シグニチャ:

```fsharp
task: Task<'T>  -> Async<'T>
```

いつ使うか:

- F#の非同期計算内で <xref:System.Threading.Tasks.Task-1>  を返す .NET API を使用する場合。

注意事項:

- 例外は、タスク並列ライブラリ(Task Parallel Library)の規則に従って <xref:System.AggregateException> でラップされます。これは、 F#の非同期における例外の処理方法と異なります。

### <a name="asynccatch"></a>Async.Catch

指定された `Async<'T>` を実行する非同期計算を作成し、`Async<Choice<'T, exn>>` を返します。 指定された `Async<'T>` が正常に完了した場合、結果の値と共に `Choice1Of2` が返されます。 完了前に例外がスローされた場合は、発生した例外と共に `Choice2of2` が返されます。 多くの計算で構成され、その計算の1つが例外をスローするような非同期計算で使用された場合、外側の計算は完全に停止されます。

型シグニチャ:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

いつ使うか:

- 例外によって失敗する可能性があり、呼び出し元でその例外を処理する必要がある非同期処理を実行する場合。

注意事項:

- 結合またはシーケンスされた非同期計算を使用する場合、その "内部" 計算の1つが例外をスローすると、外側の計算が完全に停止します。

### <a name="asyncignore"></a>Async.Ignore

指定された計算を実行するが、その結果を無視する非同期計算を作成します。

型シグニチャ:

```fsharp
computation: Async<'T> -> Async<unit>
```

いつ使うか:

- 結果が不要な非同期計算がある場合。 これは、非非同期コードの `ignore` に似ています。

注意事項:

- `Async.Start` を使用したり `Async<unit>` を必要とする別の関数を使用するために、これを使用する必要がある場合は、結果が破棄されて良いか検討してください。 型シグネチャに一致するように結果を破棄することは、通常はするべきではありません。

### <a name="asyncrunsynchronously"></a>Async.RunSynchronously

非同期計算を実行し、呼び出し元のスレッドでその結果を待機します。 これはブロッキングする呼び出しです。

型シグニチャ:

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

いつ使うか:

- 必要な場合、アプリケーション内で1回だけ使用します。実行可能ファイルのエントリポイントで。
- パフォーマンスを気にせずに、他の一連の非同期操作を一度に実行する場合。

注意事項:

- `Async.RunSynchronously` の呼び出しによって、実行が完了するまで呼び出し元のスレッドがブロックされます。

### <a name="asyncstart"></a>Async.Start

`unit` を返すスレッドプール内の非同期計算を開始します。 結果を待ちません。 入れ子になった `Async.Start` で始まる計算は、呼び出し元の親計算とは無関係に完全に開始されます。 それぞれの計算の有効期間は、どの親計算にも結び付けられていません。 親計算が取り消された場合も、子計算は取り消されないのです。

型シグニチャ:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

次の場合にのみ使用します。

- 非同期計算による結果が得られない、かつ/またはその結果を処理する必要がない。
- 非同期計算がいつ完了するかを知る必要がない。
- 非同期計算が実行されるスレッドを認識する必要がない。
- タスクの結果として発生した例外を認識したり、報告したりする必要がない。

注意事項:

- `Async.Start` で開始された計算によって発生した例外は、呼び出し元に反映されません。 呼び出し履歴はまったく傷つきません。
- `Async.Start`で開始されたどのような副作用のある処理(`printfn` の呼び出しなど)も、プログラムの実行のメインスレッドでは副作用を生じません。

## <a name="interoperating-with-net"></a>.NET との相互運用

C#の[async/await](../../../standard/async.md)スタイルの非同期プログラミングを使用する .NET ライブラリまたはコードベースを使用する場合があるでしょう。 C#と大半の .NET ライブラリは、<xref:System.Threading.Tasks.Task-1> と `Task` 型を `Async<'T>` ではなくコアの抽象化として使用するため、これら2つの非同期処理の境界を乗り越える必要があります。

### <a name="how-to-work-with-net-async-and-taskt"></a>.NET async と Task<T> を使用する方法

<xref:System.Threading.Tasks.Task-1> (つまり、戻り値を持つ非同期計算) を使用する .NET 非同期ライブラリおよびコードベースを操作するのは簡単であり、F#には組み込みのサポート機能があります。

`Async.AwaitTask` 関数によって、.NET の非同期計算を待機する事ができます。

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

`Async.StartAsTask` 関数により、非同期計算を .NET 呼び出し元に渡すことができます。

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>.NET async と Task を使用する方法

<xref:System.Threading.Tasks.Task> (つまり、値を返さない .NET 非同期計算) を使用する API を操作するには、`Async<'T>` を <xref:System.Threading.Tasks.Task> に変換する関数を追加することが必要になる場合があります。

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<xref:System.Threading.Tasks.Task> を入力として受け取る `Async.AwaitTask` が既にあります。 これと以前に定義した `startTaskFromAsyncUnit` 関数を使用する事で、 F#の非同期計算から <xref:System.Threading.Tasks.Task> 型を開始して待機する事ができます。

## <a name="relationship-to-multithreading"></a>マルチスレッドとの関係

この記事ではスレッド処理について説明していますが、次の2つの重要な点に注意してください。

1. 現在のスレッドで明示的に開始されている場合を除き、非同期計算とスレッド間の関係はありません。
1. F#での非同期プログラミングは、マルチスレッドを抽象的したものではありません。

たとえば、計算処理は作業の性質によっては実際には呼び出し元のスレッドで実行される場合があります。 また、計算処理がスレッド間を "ジャンプ" して、"待機中" の少しの時間 (ネットワーク呼び出しが転送中の場合など) の間に有用な作業を行う事もあります。

F#には現在のスレッド(または現在のスレッド以外)で 非同期計算を開始する機能を提供していますが、一般的には非同期処理は特定のスレッド処理方法に関連付けられません。

## <a name="see-also"></a>関連項目

- [F#非同期プログラミングモデル](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet.com のF#非同期ガイド](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F#の楽しく得するの非同期プログラミングガイド](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C#とF#における非同期処理: C#の非同期処理の注意事項](http://tomasp.net/blog/csharp-async-gotchas.aspx/)

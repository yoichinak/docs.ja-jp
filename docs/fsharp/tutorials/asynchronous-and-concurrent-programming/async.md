---
title: 非同期プログラミング
description: 学習方法F#非同期プログラミングが言語レベルのプログラミング モデルを簡単に使用し、自然言語を使用して実現されます。
ms.date: 06/20/2016
ms.openlocfilehash: 18ba4873cd3dba6d9548a07c4487306d96adab61
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980088"
---
# <a name="async-programming-in-f"></a>F での非同期プログラミング\#

> [!NOTE]
> この記事では、いくつか誤りが検出されました。  書き換えられます。  参照してください[問題 #666](https://github.com/dotnet/docs/issues/666)への変更について説明します。

非同期のプログラミングF#言語レベルのプログラミング モデルが使いやすく、自然言語にするように設計を行います。

非同期のプログラミングの中核となるF#は`Async<'T>`に、バック グラウンドで実行される作業の表現を`'T`特殊を介して、いずれかの型が返されます`return`キーワードまたは`unit`場合、非同期ワークフロー返される結果がありません。

キーの概念を理解するが非同期式の型があること`Async<'T>`、これは単に、_仕様_非同期のコンテキストで実行する作業の。 開始関数のいずれかで明示的に開始されるまでは実行されません (など`Async.RunSynchronously`)。 作業についての考え方を別の方法ですが、実際には非常に簡単に終了します。

たとえば、メイン スレッドをブロックすることがなく dotnetfoundation.org から HTML をダウンロードしたいとします。 このようなことを行うことができます。

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

以上です。 使用を除き`async`、 `let!`、および`return`、これはごく普通F#コード。

注目すべきである、いくつかの構文構造があります。

*   `let!` (別のコンテキストで実行) される非同期式の結果にバインドします。
*   `use!` 同様の機能`let!`がスコープ外になったときに、そのバインドされているリソースを破棄します。
*   `do!` 何も返しませんが、非同期ワークフローを待機します。
*   `return` 単に非同期式から結果を返します。
*   `return!` 別の非同期ワークフローを実行し、結果としてその戻り値を返します。

さらに、通常`let`、 `use`、および`do`キーワードは、通常の関数内にある場合と同様、非同期バージョンと共に使用できます。

## <a name="how-to-start-async-code-in-f"></a>F での非同期コードを起動する方法\#

前述のように、非同期コードを明示的に開始する必要がある別のコンテキストで実行する作業の仕様です。 これを実現する 2 つの主な方法を次に示します。

1.  `Async.RunSynchronously` 別のスレッドで非同期ワークフローを開始し、その結果を待機します。

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  `Async.Start` 別のスレッドで非同期ワークフローが開始され、**いない**その結果を待機します。

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

具体的なシナリオで使用可能な非同期ワークフローを開始するには、その他の方法はあります。 詳細については[非同期リファレンス](https://msdn.microsoft.com/library/ee370232.aspx)します。

### <a name="a-note-on-threads"></a>スレッドに関する注意事項

別のスレッド"の"という語句は、上記のように、ことを把握することが重要**非同期ワークフローのためのファサードであるわけではないマルチ スレッド**します。 ワークフロー実際に「移動」有益な処理の実行時間の短時間にそれらを借りて、スレッド間でします。 非同期ワークフローは実質的に「待機中に」(たとえば、何かを返すネットワーク呼び出しの待機など)、まで他の有益な処理を移動操作を実行時にそれを借りてが任意のスレッドが解放されます。 これにより、非同期ワークフローで、できるだけ効率的に実行されるシステムを利用して大量の I/O シナリオの特に強力になります。

## <a name="how-to-add-parallelism-to-async-code"></a>非同期コードを並列処理を追加する方法

場合があります可能性があります必要がありますを並列では、複数の非同期ジョブを実行する、その結果を収集し、何らかの方法で解釈します。 `Async.Parallel` これを強制的に変換しなくても含まれるタスク並列ライブラリを使用することがなく実行できる`Task<'T>`と`Async<'T>`型。

次の例を使用して`Async.Parallel`を並列で 4 つの人気のあるサイトから HTML をダウンロードするこれらのタスクを完了するまで待機し、ダウンロードされた HTML を印刷します。

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>重要な情報とアドバイス

*   使用するすべての関数の最後に"Async"を追加します。

 これは単なる名前付け規則が、これはやすく API の発見など。 同じルーチンの同期および非同期のバージョンがある場合に特には、明示的に名前を使用して非同期であることをお勧めです。

*   コンパイラをリッスンします。

 F#コンパイラは非常に厳格な"async"コードを同期的に実行を行うような問題とされることはほぼ不可能です。 警告に遭遇した場合はどのように考えるかをコードが実行されません記号です。 コンパイラを満足することができますと、ほとんどの場合に、コードは、想定どおりに実行されます。

## <a name="for-the-cvb-programmer-looking-into-f"></a>C#または VB プログラマが F を見る\#

このセクションでは、非同期モデルに使い慣れている前提としていますC#/VB。 そうでない場合[での非同期プログラミングC#](../../../csharp/async.md)は開始点です。

基本的な違いは、C#または VB の非同期モデルとF#非同期モデル。

返す関数を呼び出すと、`Task`または`Task<'T>`、そのジョブがすでに実行を開始します。 返されたハンドルは、既に実行中の非同期ジョブを表します。 非同期関数を呼び出すこととこれに対し、 F#、`Async<'a>`返されるとなるジョブを表す**生成**時点。 非同期ジョブのために強力ですが、このモデルを理解することがF#を連結して、簡単に条件付きで実行され、コントロールの細かい粒度で開始します。

その他のいくつかの類似点と注目すべき違いがあります。

### <a name="similarities"></a>類似点

*   `let!`、 `use!`、および`do!`に似ています`await`内から、非同期ジョブを呼び出すときに、`async{ }`ブロックします。

 次の 3 つのキーワードは内でのみ使用できます、`async { }`ブロック、方法と似ています`await`内で呼び出すことができますのみ、`async`メソッド。 つまり、`let!`キャプチャし、結果を使用する場合に`use!`は同じですが、何かのリソースが使用すると、後にクリーンアップする必要がありますと`do!`戻り値を完了する非同期ワークフローを待機する場合に続行する前にします。

*   F#同様の方法でデータを並列化をサポートしています。

 非常に異なる方法で動作が`Async.Parallel`に対応する`Task.WhenAll`をすべて終了すると、一連の非同期ジョブの結果としているシナリオでは。

### <a name="differences"></a>相違点

*   入れ子になった`let!`いないは許可されているとは異なり、入れ子になった `await`

 異なり`await`、無期限にネストできます`let!`ことはできませんし、その結果を別の内部で使用する前にバインドされている必要があります`let!`、 `do!`、または`use!`します。

*   キャンセルのサポートは、非常に簡単F#よりもC#/VB.

 タスクの途中での実行でのキャンセルをサポートしているC#または VB では、チェックが必要、`IsCancellationRequested`プロパティまたは呼び出す`ThrowIfCancellationRequested()`上、`CancellationToken`非同期メソッドに渡されるオブジェクト。

これに対し、F#非同期ワークフローがより自然にキャンセル可能です。 キャンセルは、単純な 3 段階のプロセスです。

1.  新規の `CancellationTokenSource` を作成します。
2.  開始関数に渡します。
3.  呼び出す`Cancel`トークンにします。

例:

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

以上です。

## <a name="further-resources"></a>他のリソース:

*   [MSDN での非同期ワークフロー](https://msdn.microsoft.com/library/dd233250.aspx)
*   [非同期のシーケンスF#](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F#データを HTTP ユーティリティ](https://fsharp.github.io/FSharp.Data/library/Http.html)
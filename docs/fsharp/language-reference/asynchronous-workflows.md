---
title: 非同期ワークフロー
description: サポートについて F# プログラミング言語、非同期的に計算を実行するための他の作業の実行をブロックせずに実行します。
ms.date: 05/16/2016
ms.openlocfilehash: 2d967f6bfe46b4f3916648b3063210d1ba1c210f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630001"
---
# <a name="asynchronous-workflows"></a>非同期ワークフロー

> [!NOTE]
> API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

このトピックでは、計算を実行する、非同期的には、他の作業の実行をブロックすることがなく F# でのサポートについて説明します。 たとえば、非同期計算を使用して、アプリケーションが他の作業を実行するときにユーザーに応答し続ける Ui を持つアプリケーションを作成できます。

## <a name="syntax"></a>構文

```fsharp
async { expression }
```

## <a name="remarks"></a>Remarks

前の構文では、によって`expression`表される計算が非同期的に実行されるように設定されています。つまり、非同期スリープ操作、i/o、およびその他の非同期操作が実行されるときに、現在の計算スレッドをブロックしません。 非同期計算は、多くの場合、現在のスレッドで実行を継続しながらバックグラウンドスレッドで開始されます。 式の型はです`Async<'T>`。ここ`'T`で、は、 `return`キーワードが使用されている場合に、式によって返される型です。 このような式のコードは、*非同期ブロック*または非同期*ブロック*と呼ばれます。

非同期プログラミングにはさまざまな方法があり、クラスに[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)はいくつかのシナリオをサポートするメソッドが用意されています。 一般的な方法では、 `Async`非同期的に実行する計算または計算を表すオブジェクトを作成し、トリガー関数のいずれかを使用して、これらの計算を開始します。 さまざまなトリガー関数は、非同期計算を実行するさまざまな方法を提供します。どちらを使用するかは、現在のスレッド、バックグラウンドスレッド、.NET Framework タスクオブジェクトを使用するかどうか、および継続があるかどうかによって異なります。計算が終了したときに実行する必要がある関数。 たとえば、現在のスレッドで非同期計算を開始するには、を使用[`Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3)します。 UI スレッドから非同期計算を開始する場合は、キーストロークやマウスアクティビティなどのユーザー操作を処理するメインイベントループをブロックしないため、アプリケーションの応答性が維持されます。

## <a name="asynchronous-binding-by-using-let"></a>Let を使用した非同期バインド

非同期ワークフローでは、一部の式と操作は同期的であり、一部の式と操作は、非同期的に結果を返すように設計された、より長い計算です。 通常`let`のバインディングではなく、メソッドを非同期的に呼び出す場合は`let!`、を使用します。 の`let!`効果は、計算の実行中に、他の計算やスレッドで実行を継続できるようにすることです。 `let!`バインディングの右側から制御が戻った後、非同期ワークフローの残りの部分は実行を再開します。

次のコードは、 `let`と`let!`の違いを示しています。 を使用`let`するコード行で`Async.StartImmediate`は、または[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)などを使用して後で実行できるオブジェクトとして非同期計算を作成します。 を使用`let!`するコード行によって計算が開始され、その後、結果が使用可能になるまでスレッドが中断されます。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

に`let!`加えて、を使用`use!`して非同期バインディングを実行することもできます。 `let!` `let` と`use`の違いは、との違いと同じです。 `use!` の`use!`場合、オブジェクトは現在のスコープの終了時に破棄されます。 現在のリリースF#のでは、 `use!` `use`がの場合でも、では値を null に初期化することはできないことに注意してください。

## <a name="asynchronous-primitives"></a>非同期プリミティブ

1つの非同期タスクを実行し、その結果を返すメソッドは、*非同期プリミティブ*と呼ばれ、専用`let!`に設計されています。 複数の非同期プリミティブは、F# コア ライブラリで定義されます。 このような Web アプリケーションの2つのメソッドは[`Microsoft.FSharp.Control.WebExtensions`](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003) [`WebRequest.AsyncGetResponse`](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) 、 [`WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)モジュールで定義されています。 どちらのプリミティブも、URL を指定して Web ページからデータをダウンロードします。 `AsyncGetResponse`オブジェクトを生成し、 `AsyncDownloadString` Web ページの HTML を表す文字列を生成します。 `System.Net.WebResponse`

非同期 i/o 操作のためのいくつかのプリミティブは、 [`Microsoft.FSharp.Control.CommonExtensions`](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396)モジュールに含まれています。 `System.IO.Stream`クラスの拡張メソッドは[`Stream.AsyncRead`](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) 、と[`Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618)です。

また、完全な本文が非同期ブロックで囲まれた関数を定義することで、独自の非同期プリミティブを作成することもできます。

返す、F# の関数を作成する F# 非同期プログラミング モデルとその他の非同期モデルのように設計された .NET Framework の非同期のメソッドを使用する`Async`オブジェクト。 ライブラリF#には、これを簡単に実行できるようにする機能があります。

非同期ワークフローの使用例を次に示します。[非同期クラス](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)のメソッドに関するドキュメントには、他にも多くのものがあります。

この例では、非同期ワークフローを使用して並列で計算を実行する方法を示します。

次のコード例では、関数`fetchAsync`は Web 要求から返された HTML テキストを取得します。 関数`fetchAsync`には、非同期のコードブロックが含まれています。 非同期プリミティブの結果にバインドする場合は、次[`AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)のようにします。 let ではなくを使用します。

関数[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)を使用して非同期操作を実行し、その結果を待機します。 例として、関数を[`Async.Parallel`](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) `Async.RunSynchronously`関数と共に使用することで、複数の非同期操作を並列で実行できます。 関数`Async.Parallel`は、 `Async`オブジェクトの一覧を取得し、各`Async`タスクオブジェクトのコードを並列で実行`Async`するように設定し、並列計算を表すオブジェクトを返します。 1回の操作と同じように、 `Async.RunSynchronously`を呼び出して実行を開始します。

関数`runAll`は、3つの非同期ワークフローを並列で起動し、すべてが完了するまで待機します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [コンピュテーション式](computation-expressions.md)
- [Control. Async クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)

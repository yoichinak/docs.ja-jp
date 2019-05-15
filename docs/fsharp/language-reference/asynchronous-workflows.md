---
title: 非同期ワークフロー
description: サポートについて F# プログラミング言語、非同期的に計算を実行するための他の作業の実行をブロックせずに実行します。
ms.date: 05/16/2016
ms.openlocfilehash: 87d4c927be89bbb404a087091eed8c4cae167f0f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645514"
---
# <a name="asynchronous-workflows"></a>非同期ワークフロー

> [!NOTE]
> API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

このトピックでは、計算を実行する、非同期的には、他の作業の実行をブロックすることがなく F# でのサポートについて説明します。 たとえば、アプリケーションで他の作業を実行するようユーザーに応答性を維持するための Ui があるアプリケーションを作成する非同期計算を使用できます。

## <a name="syntax"></a>構文

```fsharp
async { expression }
```

## <a name="remarks"></a>Remarks

前の構文では、によって表される、計算`expression`は、スリープ状態の非同期操作、I/O、および他の非同期操作を実行すると、計算の現在のスレッドをブロックすることがなく、非同期的に実行するように設定します。 非同期計算を現在のスレッドで実行が続けながら、多くの場合、バック グラウンド スレッドで開始されます。 式の型が`Async<'T>`ここで、`'T`式によって返される型は、ときに、`return`キーワードを使用します。 このような式のコードと呼ばれます、*非同期ブロック*、または*非同期ブロック*します。

さまざまな非同期プログラミングの方法があると、 [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)クラスがいくつかのシナリオをサポートするメソッドを提供します。 一般的な方法は、作成する`Async`計算や、非同期的に実行する計算を表すオブジェクトのトリガーを起動する関数のいずれかを使用してこれらの計算を開始します。 さまざまなトリガーを起動する関数が、非同期計算を実行中のさまざまな方法を提供し、現在のスレッドやバック グラウンド スレッドでは、.NET Framework タスク オブジェクトでは、使用するかどうかに依存する 1 つを使用して、継続があるかどうか関数の計算が終了するときに実行する必要があります。 たとえば、現在のスレッドで非同期計算を開始することができますを使用する[ `Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3)します。 UI スレッドから非同期計算を開始する場合、キーストロークやマウスのアクティビティなどのユーザー アクションを処理するため、アプリケーションは応答をメイン イベント ループはブロックされません。

## <a name="asynchronous-binding-by-using-let"></a>Let を使用して非同期のバインド。

非同期のワークフローでは、いくつかの式と操作は、同期、し、いくつか非同期的に結果を返すように設計された長い計算します。 メソッドを呼び出す場合、非同期的に、通常ではなく`let`使用するバインディング、`let!`します。 効果`let!`は計算が実行されているその他の計算またはスレッドで継続して実行できるようにします。 後の右側にある、`let!`バインディングを返します、非同期のワークフローの残りの部分が実行を再開します。

次のコードは、違いを示しています。`let`と`let!`します。 使用するコードの行`let`だけ実行できる後で使用すると、たとえば、オブジェクトとして非同期計算を作成`Async.StartImmediate`または[ `Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)します。 使用するコードの行`let!`計算を開始し、スレッドは、結果が入手可能にするポイントの実行が続行されるまで中断します。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

ほかに`let!`、使用することができます`use!`非同期バインドを実行します。 間の差`let!`と`use!`の違いと同じ`let`と`use`します。 `use!`、現在のスコープの終了時、オブジェクトが破棄されます。 解放を現在のことに注意してください、F#言語`use!`場合でも、null に初期化された値を許可しない`use`は。

## <a name="asynchronous-primitives"></a>非同期プリミティブ

1 つの非同期タスクを実行し、結果を返すメソッドが呼び出された、*非同期プリミティブ*で使用するために設計されていますがこれらと`let!`します。 複数の非同期プリミティブは、F# コア ライブラリで定義されます。 Web アプリケーションのような 2 つのメソッドは、モジュールで定義されて[ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c)と[ `WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)します。 両方のプリミティブは、Web ページで、指定された URL からデータをダウンロードします。 `AsyncGetResponse` 生成、`System.Net.WebResponse`オブジェクト、および`AsyncDownloadString`Web ページの HTML を表す文字列を生成します。

非同期 I/O 操作の複数のプリミティブに含まれる、 [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396)モジュール。 これらの拡張メソッドの`System.IO.Stream`クラスは、 [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e)と[ `Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618)します。

完成した body が非同期ブロックで囲まれている関数を定義することで、独自の非同期プリミティブを記述することもできます。

返す、F# の関数を作成する F# 非同期プログラミング モデルとその他の非同期モデルのように設計された .NET Framework の非同期のメソッドを使用する`Async`オブジェクト。 F#ライブラリが簡単に実行する関数。

非同期ワークフローを使用する 1 つの例は、ここでは含まれていますメソッドのドキュメントにあるその他の多く、 [Async クラス](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)します。

この例では、非同期ワークフローを使用して並列で計算を実行する方法を示します。

次のコード例は、関数で`fetchAsync`Web 要求から返される HTML テキストを取得します。 `fetchAsync`関数には、非同期コードのブロックが含まれています。 バインディングがここでは、非同期プリミティブでの結果に行われる場合[ `AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)ことができます。 let の代わりに使用されます。

関数を使用する[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)を非同期操作を実行し、結果を待機します。 たとえば、する複数の非同期操作を並列実行できるを使用して、 [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4)関数と組み合わせて、`Async.RunSynchronously`関数。 `Async.Parallel`関数の一覧には、`Async`オブジェクトは、各コードは、設定`Async`タスク オブジェクトを返します、並列で実行する、`Async`並列計算を表すオブジェクト。 1 つの操作と同じ動作を呼び出す`Async.RunSynchronously`実行を開始します。

`runAll`関数は、次の 3 つの非同期ワークフローを並列でを起動し、これらがすべて完了するまで待機します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [コンピュテーション式](computation-expressions.md)
- [Control.Async クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)

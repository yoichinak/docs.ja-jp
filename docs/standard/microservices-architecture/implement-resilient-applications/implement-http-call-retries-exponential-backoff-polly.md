---
title: Polly で指数バックオフを含む HTTP 呼び出しの再試行を実装する
description: HTTP エラーを Polly と HttpClientFactory で処理する方法について説明します
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: d031ca9b7c46f02cd9e22ae91fb20f281ebb47a2
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612060"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>HttpClientFactory ポリシーと Polly ポリシーで指数バックオフを含む HTTP 呼び出しの再試行を実装する

指数のバックオフでの再試行のためのアプローチとしては、オープン ソースである [Polly ライブラリ](https://github.com/App-vNext/Polly)のような高度な .NET ライブラリを利用することをお勧めします。

Polly とは、回復機能と一時的な障害処理の機能を提供する .NET ライブラリです。 このような機能は、再試行、遮断器、バルクヘッド分離、タイムアウト、フォールバックなどの Polly ポリシーを適用することで実装できます。 Polly は .NET 4.x および .NET Standard ライブラリ 1.0 (.NET Core をサポート) を対象にしています。

ただし、HttpClient を含む独自のコードで Polly のライブラリを使用することは非常に複雑になる可能性があります。 eShopOnContainers の最初のバージョンでは、[ResilientHttpClient ビルディングブロック](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs)が Polly を基盤としていました。 しかしながら、HttpClientFactory が公開され、回復力のある HTTP 通信が簡単に実装できるようになり、eShopOnContainers ではビルディングブロックが非推奨になりました。 

次の手順では、前のセクションで説明した、HttpClientFactory に統合された Polly で HTTP 再試行を使用する方法を示します。

**ASP.NET Core 2.2 パッケージを参照する**

`HttpClientFactory` は .NET Core 2.1 以降で使用できますが、最新の ASP.NET Core 2.2 パッケージを NuGet から入手し、プロジェクトで使用することをお勧めします。 通常、`AspNetCore` メタパッケージと拡張パッケージ `Microsoft.Extensions.Http.Polly` が必要になります。

**Startup で、Polly の再試行ポリシーでクライアントを構成する**

前のセクションで示したように、標準の Startup.ConfigureServices(...) メソッドで、名前または型が指定された HttpClient 構成を定義する必要がありますが、今後は以下のように、指数バックオフを含む HTTP 再試行のポリシーを指定し、増分コードを追加します。

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** メソッドは、使用する `HttpClient` オブジェクトにポリシーを追加します。 この場合、指数バックオフを含む HTTP 再試行に対して Polly のポリシーが追加されます。

手法のモジュール性を高めるために、次のコードで示すように、`Startup.cs` ファイル内の個別メソッドに HTTP 再試行ポリシーを定義できます。

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Polly では、再試行回数を指定した再試行ポリシー、指数バックオフの構成、HTTP 例外が発生した場合に実行するアクション (エラーの記録など) を定義できます。 上記のコードでは、指数関数的再試行で (最初は 2 秒) 6 回試すようにポリシーが構成されています。 

つまり、6 回試すとき、再試行間の秒数が指数関数的に後退します (最初は 2 秒)。

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>再試行ポリシーにジッタ方式を追加する

通常の再試行ポリシーは、コンカレンシーやスケーラビリティが高い場合や、高競合状態下でシステムに影響を及ぼすことがあります。 部分的な停止の場合に多くのクライアントから来る同様の再試行のピークを乗り越えるための賢い回避策は、ジッタ方式を再試行アルゴリズムまたはポリシーに追加することです。 これにより、急増するバックオフにランダム性を加えることで、エンドツーエンド システム全体のパフォーマンスを向上できます。 こうすれば、問題が発生した際のスパイクを分散できます。 平易な Polly ポリシーを使用する場合、ジッタを実装するコードは次の例のようになります。

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>その他の技術情報

- **再試行パターン**\
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly と HttpClientFactory**\
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET の復元および一時的な障害処理ライブラリ)**\
  <https://github.com/App-vNext/Polly>

- **Marc Brooker.ジッタ:ランダム性を使って状況を改善する**\
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[前へ](explore-custom-http-call-retries-exponential-backoff.md)
>[次へ](implement-circuit-breaker-pattern.md)

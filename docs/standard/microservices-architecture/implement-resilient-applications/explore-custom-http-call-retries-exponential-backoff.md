---
title: カスタム HTTP 呼び出しの指数バックオフを含む再試行について
description: 考えられる HTTP 障害シナリオを処理するため、ゼロからカスタム HTTP 呼び出しの指数バックオフを含む再試行を実装する方法について説明します。
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644737"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>カスタム HTTP 呼び出しの指数バックオフを含む再試行について

回復力のあるマイクロサービスを作成するには、考えられる HTTP 障害シナリオに対処する必要があります。 これらの障害に対処する 1 つの方法として (ただし推奨されません)、指数バックオフを含む再試行の実装を作成します。

**重要な注意事項:** このセクションでは、HTTP 呼び出しの再試行を実装するカスタム コードを作成する方法を示します。 ただし、これをユーザーが独自に行うことは推奨されていませんが、.NET Core 2.1 以降で使用可能なより強力で信頼性が高いながらもよりシンプルなメカニズム (Polly での `HttpClientFactory` など) を使用することが推奨されています。 これらの推奨アプローチについては、以降のセクションで説明します。

最初の考察として、[RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260) にあるような指数バックオフ用のユーティリティ クラスを使用した独自のコードに加えて、次に示すようなコードを実装することも可能です。

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

クライアント C\# アプリケーション (別の Web API クライアント マイクロサービス、ASP.NET MVC アプリケーション、または C\# Xamarin アプリケーション) でこのコードを使用することは簡単です。 次の例は、HttpClient クラスの使い方を示しています。

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

このコードは概念の実証用にのみ使用してください。 次のセクションでは、HttpClientFactory を使用して、よりシンプルでありながらより高度なアプローチを使用する方法について説明します。 HttpClientFactory は、Polly のような回復性が実証されているライブラリを持つ、.NET Core 2.1 以降で使用できます。

>[!div class="step-by-step"]
>[前へ](implement-resilient-entity-framework-core-sql-connections.md)
>[次へ](use-httpclientfactory-to-implement-resilient-http-requests.md)

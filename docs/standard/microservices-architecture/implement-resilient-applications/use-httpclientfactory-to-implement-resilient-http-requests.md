---
title: HttpClientFactory を使用して回復力の高い HTTP 要求を実装する
description: .NET Core 2.1 以降で使用できる HttpClientFactory を使用して、`HttpClient` インスタンスを作成し、それをアプリケーションで簡単に使用できるようにする方法について説明します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 679de8577d1ce876823954cb7917c50daae9e230
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348714"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>HttpClientFactory を使用して回復力の高い HTTP 要求を実装する

`HttpClientFactory` は、自己主張性の強いファクトリで、アプリケーションに使用する <xref:System.Net.Http.HttpClient> インスタンスを作成するため、.NET Core 2.1 以降で使用できます。

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core で使用可能な元の HttpClient クラスに関する問題

よく知られている元の [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) クラスは、簡単に使用できますが、多くの開発者によって適切に使用されていない場合もあります。 

1 つ目の問題は、このクラスは破棄可能ですが、`HttpClient` オブジェクトを破棄しても、基になるソケットがすぐに解放されず、'ソケットの枯渇' という重大な問題が発生する場合があるため、`using` ステートメントで使用するのは最適な選択ではないということです。 この問題の詳細については、ブログ記事「[You're using HttpClient wrong and it is destabilizing your software (HttpClient の誤った使い方がソフトウェアを不安定にする)](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)」を参照してください。

そのため、`HttpClient` は一度インスタンス化されたら、アプリケーションの有効期間にわたって再利用されることを目的としています。 すべての要求に対して `HttpClient` クラスをインスタンス化すると、高負荷の下で使用可能なソケットの数が枯渇してしまいます。 この問題により、`SocketException` エラーが発生します。 この問題を解決するために可能なアプローチは、HttpClient クライアントの使用に関するこの [Microsoft の記事](/dotnet/csharp/tutorials/console-webapiclient)で説明されているように、`HttpClient` オブジェクトをシングルトンまたは静的として作成することに基づいています。 

しかし、`HttpClient` には、シングルトンまたは静的オブジェクトとして使用した場合に発生する可能性がある 2 つ目の問題があります。 この場合、[.NET Core GitHub リポジトリでこの問題](https://github.com/dotnet/corefx/issues/11224)について説明されているように、シングルトンまたは静的 `HttpClient` は、DNS の変更を尊重しません。 

これらの問題に対処し、`HttpClient` インスタンスの管理を容易にするため、.NET Core 2.1 では、新しい `HttpClientFactory` が導入されています。これは、Polly を統合することで、回復力のある HTTP 呼び出しを実装するためにも使用できます。   

## <a name="what-is-httpclientfactory"></a>HttpClientFactory とは

`HttpClientFactory` は次の目的のために設計されています。

- 論理 HttpClients の名前付けと構成を一元化します。 たとえば、特定のマイクロサービスにアクセスするために事前に構成されているクライアント (サービス エージェント) を構成できます。
- `HttpClient` でのハンドラーのデリゲートにより送信ミドルウェアの概念を体系化し、Polly ベースのミドルウェアを実装して、回復性のための Polly のポリシーを利用します。
- `HttpClient` は既に、送信 HTTP 要求用にリンクできるハンドラーのデリゲートの概念を備えています。 ファクトリに http クライアントを登録できるほか、再試行、サーキット ブレーカーなどに Polly ポリシーが使えるようになる Polly ハンドラーを使用することができます。
- HttpClientMessageHandler の有効期間を管理して、`HttpClient` の有効期間を自分で管理する際に発生する可能性がある上記の問題を回避します。 

## <a name="multiple-ways-to-use-httpclientfactory"></a>HttpClientFactory を使用する複数の方法

アプリケーションで `HttpClientFactory` を使用するには、複数の方法があります。

- `HttpClientFactory` を直接使用する
- 名前付きクライアントを使用する
- 型指定されたクライアントを使用する
- 生成されたクライアントを使用する

説明を簡潔にするため、このガイダンスでは、型指定されたクライアント (サービス エージェント パターン) を使用するための `HttpClientFactory` を使用する最も体系化されている方法を示します。ただし、すべてのオプションは文書化されており、現在、[HttpClientFactory の使用方法を説明しているこの記事](/aspnet/core/fundamentals/http-requests?#consumption-patterns)に一覧があります。  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>HttpClientFactory で型指定されたクライアントを使用する方法

それでは、"型指定されたクライアント" とは何でしょうか。 これは、挿入時に `DefaultHttpClientFactory` によって構成される単なる `HttpClient` です。

次の図は、`HttpClientFactory` で型指定されたクライアントを使用する方法を示しています。

![(コントローラーまたはクライアント コードによって使用される) ClientService には、登録済みの IHttpClientFactory によって作成された HttpClient が使用されます。 このファクトリでは、HttpClient と、それが管理するプールの HttpClient を割り当てています。 拡張メソッド AddHttpClient を使用して IHttpClientFactory を DI コンテナーに登録するときに、Polly のポリシーを使用して HttpClient を構成できます。](./media/image3.5.png)

**図 8-4** 型指定されたクライアント クラスで HttpClientFactory を使用する。

まず、アプリケーションに `HttpClientFactory` を設定し、`IServiceCollection` の `AddHttpClient()` 拡張メソッドを含む `Microsoft.Extensions.Http` パッケージへの参照を追加します。 この拡張メソッドは、インターフェイス `IHttpClientFactory` のシングルトンとして使用される `DefaultHttpClientFactory` を登録します。 これは `HttpMessageHandlerBuilder` の一時的な構成を定義します。 プールから取得されたこのメッセージ ハンドラー (`HttpMessageHandler` オブジェクト) は、ファクトリから返された `HttpClient` によって使用されます。

次のコードで、`AddHttpClient()` を使用して、`HttpClient` を使用する必要がある型指定されたクライアント (エージェント サービス) を登録する方法を確認できます。

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

前のコードに示すようにクライアント サービスを登録し、次の段落で説明するように、各サービスに合わせて構成された `HttpClient` を `DefaultClientFactory` で作成します。

クライアント サービス クラスを `AddHttpClient()` に登録するだけで、クラスに挿入される `HttpClient` オブジェクトには、登録時に提供される構成とポリシーが使用されるようになります。 以降のセクションでは、Polly の再試行またはサーキット ブレーカーのような、これらのポリシーを確認します。

### <a name="httpclient-lifetimes"></a>HttpClient の有効期間

`IHttpClientFactory` から `HttpClient` オブジェクトを取得するたび、新しいインスタンスが返されます。 ただし、各 `HttpClient` では、`HttpMessageHandler` の有効期間が切れていない限り、リソースの消費量を減らすために `IHttpClientFactory` によってプールおよび再利用されている `HttpMessageHandler` を使用します。

通常各ハンドラーは基になる HTTP 接続を独自に管理しており、必要以上に多くのハンドラーを作成すると接続が遅延する可能性があるため、ハンドラーをプールするのは望ましい方法です。 また、一部のハンドラーは接続を無期限に開いており、DNS の変更にハンドラーが対応できないことがあります。

プール内の `HttpMessageHandler` オブジェクトには、有効期間があります。この有効期間は、プール内の `HttpMessageHandler` インスタンスを再利用できる期間です。 既定値は 2 分ですが、型指定されたクライアントごとにオーバーライドできます。 オーバーライドするには、次のコードに示すように、クライアント作成時に返された `IHttpClientBuilder` で `SetHandlerLifetime()` を呼び出します。

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

型指定された各クライアントには、独自の構成済みハンドラーの有効期間の値を設定できます。 ハンドラーの有効期限を無効にするには、有効期間を `InfiniteTimeSpan` に設定します。

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>挿入された構成済みの HttpClient を使用する、型指定されたクライアント クラスを実装する

前の手順では、型指定されたクライアント クラス (サンプル コードにある、'BasketService'、'CatalogService'、'OrderingService' のようなクラスなど) が定義されている必要がありました。型指定されたクライアントは、(そのコンストラクターを通じて挿入された) `HttpClient` オブジェクトを受け取り、それを使用していくつかのリモート HTTP サービスを呼び出すクラスです。 次に例を示します。

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

型指定されたクライアント (この例では CatalogService) は、依存関係の挿入 (DI) によってアクティブ化されます。つまり HttpClient だけでなく、そのコンストラクター内に登録されている任意のサービスを受け取ることができます。

型指定されたクライアントは、実際には、一時的なオブジェクトです。つまり、新しいインスタンスは必要になるたびに作成され、新しい `HttpClient` インスタンスが構築されるたびにそれを受け取ります。 ただし、プール内の HttpMessageHandler オブジェクトは、複数の Http 要求で再利用されるオブジェクトです。

### <a name="use-your-typed-client-classes"></a>型指定されたクライアント クラスを使用する

最後に、型クラスを実装し、それを AddHttpClient() に登録すると、DI によって挿入されたサービスがある任意の場所でそれを使用できます。たとえば、次の eShopOnContainers のコードのように、任意の Razor ページ コードや、MVC Web アプリの任意のコントローラーで使用できます。

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) => 
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied, 
                                               int? TypesFilterApplied, 
                                               int? page, 
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0, 
                                                            itemsPage, 
                                                            BrandFilterApplied, 
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

この時点までは、示されているコードは、通常の Http 要求を実行するだけですが、次のセクションでは、不思議なことが起こります。ポリシーを追加して、ハンドラーを登録済みの型指定されているクライアントにデリゲートするだけで、`HttpClient` によって実行されるすべての HTTP 要求が、指数バックオフを含む再試行、サーキット ブレーカー、またはその他の任意のカスタム デリゲート ハンドラーなど、回復力のあるポリシーを考慮して、追加のセキュリティ機能 (認証トークンの使用など) やその他のカスタム機能を実装するようになります。 

## <a name="additional-resources"></a>その他の技術情報

- **.NET Core で HttpClientFactory を使用する**\
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **HttpClientFactory GitHub リポジトリ**\
  [*https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory*](https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory)

>[!div class="step-by-step"]
>[前へ](explore-custom-http-call-retries-exponential-backoff.md)
>[次へ](implement-http-call-retries-exponential-backoff-polly.md)

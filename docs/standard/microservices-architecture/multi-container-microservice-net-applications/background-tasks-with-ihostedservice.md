---
title: IHostedService と BackgroundService クラスを使ってマイクロサービスのバックグラウンド タスクを実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービスの .NET Core でバックグラウンド タスクを実装する IHostedService と BackgroundService を使用する新しいオプションについて理解します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 638c9b9bae97b90b94c0ca9b421bc20cd3eb41ee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967192"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>IHostedService と BackgroundService クラスを使ってマイクロサービスのバックグラウンド タスクを実装する

バックグラウンド タスクとスケジュールされたジョブは、最終的にはマイクロサービス ベースのアプリケーションまたはあらゆる種類のアプリケーションで、実装する必要がある可能性があるものです。 マイクロサービス アーキテクチャを使用した場合の違いは、これらのバックグラウンド タスクをホストするために単一のマイクロサービスのプロセス/コンテナーを実装できるため、必要に応じてスケールダウンまたはスケールアップしたり、そのマイクロサービスのプロセス/コンテナーの単一のインスタンスを確実に実行させたりすることができることです。

これらの種類のタスクは、ホスト、アプリケーション、マイクロサービス内でホストするサービス、ロジックであるため、全体的な観点から、.NET Core では*ホステッド サービス*と呼びます。 このケースでは、ホステッド サービスは、単にバックグラウンド タスク ロジックを持つクラスを意味していることに注意してください。

.NET Core 2.0 以降では、ホステッド サービスを簡単に実装できるようにする <xref:Microsoft.Extensions.Hosting.IHostedService> という名前の新しいインターフェイスが、フレームワークによって提供されています。 基本的な考え方は、図 6-26 に示すように、ご利用の Web ホストまたはホストが実装されているときに、バックグラウンドで実行される複数のバックグラウンド タスク (ホステッド サービス) を登録できることです。

![ASP.NET Core 1.x と 2.x は、Web アプリのバックグラウンド プロセスで IWebHost をサポートしており、.NET Core 2 と 1 は、プレーンなコンソール アプリでのバックグラウンド処理に IHost をサポートしています。](./media/image26.png)

**図 6-26**。 WebHost と Host で IHostedService を使用した場合の比較

`WebHost` と `Host` の違いに注目してください。 

ASP.NET Core 2.0 の `WebHost` (`IWebHost` を実装する基底クラス) は、MVC Web アプリや Web API サービスを実装している場合など、HTTP サーバー機能をプロセスに提供するために使用するインフラストラクチャ成果物です。 ASP.NET Core での新しいインフラストラクチャのすべての長所を提供することで、依存関係の挿入を使用、要求パイプラインなどへのミドルウェアの挿入、およびこれらの `IHostedServices` をバックグラウンド タスクに正確に使用することを可能にします。

`Host` (`IHost` を実装する基底クラス) は .NET Core 2.1 で実装されました。 基本的に、`Host` を使用すると、`WebHost` を使用した場合と同様のインフラストラクチャ (依存関係の挿入、ホステッド サービスなど) ができますが、このケースでは、ホストとしてシンプルでより軽量なプロセスが必要なだけで、MVC、Web API または HTTP サーバー機能は関係ありません。

そのため、IHost を使用して特殊化されたホスト プロセスを作成してホステッド サービス以外 (`IHostedServices` をホスティングするためだけに作成されたマイクロサービスなど) は処理しないことを選択するか、または代わりに既存の ASP.NET Core `WebHost` (既存の ASP.NET Core Web API または MVC アプリ) を拡張することを選択できます。 

ビジネスと拡張性のニーズに応じて、いずれの方法にも長所と短所があります。 つまり、基本的には、バックグラウンド タスクが HTTP (IWebHost) と関係ない場合、IHost を使用する必要があります。

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>WebHost または Host でホステッド サービスを登録する

`IHostedService` インターフェイスの使用は、`WebHost` と `Host`で非常に似ているので、詳しく見てみましょう。 

SignalR はホステッド サービスを使用している成果物の一例ですが、次のようなより単純なことにも使用することができます。

-   変更を検索するデータベースをポーリングするバックグラウンド タスク。
-   いくつかのキャッシュを定期的に更新するスケジュールされたタスク。
-   タスクをバックグラウンド スレッドで実行することを可能にする QueueBackgroundWorkItem の実装。
-   `ILogger` などの共通サービスを共有しながら、Web アプリのバックグラウンドでメッセージ キューからのメッセージの処理。
-   `Task.Run()` で開始されるバックグラウンド タスク。

基本的に、IHostedService に基づいて、これらのアクションのいずれかをバックグラウンド タスクにオフロードできます。

1 つまたは複数の `IHostedServices` を `WebHost` または `Host` に追加するには、ASP.NET Core `WebHost` で標準的な DI (依存関係の挿入) を経由して (または .NET Core 2.1 以降の `Host` で) それらを登録します。 基本的に、次のコードのように、一般的な ASP.NET WebHost から、`Startup` クラスの使い慣れた `ConfigureServices()` メソッド内でホステッド サービスを登録する必要があります。 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

そのコードで、`GracePeriodManagerService` ホステッド サービスは eShopOnContainers の Ordering business microservice からの実際のコードですが、他の 2 つは単に追加の 2 つのサンプルです。

`IHostedService` バックグラウンド タスクの実行は、アプリケーション (さらに言えば、ホストまたはマイクロサービス) の有効期間に合わせて調整されます。 アプリケーションの起動時にタスクを登録して、いくつかの正常なアクションを行うか、アプリケーションのシャットダウン時にクリーンアップすることができます。

`IHostedService` を使用しない場合は、いつでもバックグラウンド スレッドを開始して任意のタスクを実行することができます。 正常なクリーンアップ アクションを実行する機会を持たずにスレッドが単に強制終了されるときは、差はちょうどアプリのシャットダウン時間になります。

## <a name="the-ihostedservice-interface"></a>IHostedService インターフェイス

`IHostedService` を登録すると、アプリケーションの起動時と停止時にそれぞれ、.NET Core によって `IHostedService` 型の `StartAsync()` メソッドと `StopAsync()` メソッドが呼び出されます。 具体的には、開始は、サーバーが起動して `IApplicationLifetime.ApplicationStarted` がトリガーされた後に呼び出されます。

.NET Core で定義されたように、`IHostedService` は次のようになります。

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
ご想像のとおり、以前に示したように、IHostedService の複数の実装を作成し、`ConfigureService()` メソッドでそれらを DI コンテナーに登録することができます。 これらすべてのホステッド サービスが、アプリケーション/マイクロサービスと共に開始および停止されます。

開発者は、`StopAsync()` メソッドがホストによってトリガーされるときに、停止アクションまたはサービスを処理します。

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>BackgroundService 基底クラスから派生したカスタムのホステッド サービス クラスを使用して IHostedService を実装する

続行して、ホステッド サービスのカスタム クラスをゼロから作成し、`IHostedService` を実装します。これは .NET Core 2.0 を使用する場合に行う必要があります。 

ただし、ほとんどのバックグラウンド タスクでは、キャンセル トークンの管理およびその他の一般的な操作で同様のニーズがあるため、派生元として使用できる非常に便利な `BackgroundService` という名前の抽象基底クラスがあります (.NET Core 2.1 以降で利用できます)。

そのクラスは、バックグラウンド タスクを設定するために必要な主要な作業を提供します。

次のコードは、.NET Core に実装されている BackgroundService 抽象基底クラスです。

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0. 
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts = 
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it, 
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }
    
    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

前の抽象基底クラスから派生する場合、データベースをポーリングして、必要に応じてイベント バスに統合イベントをパブリッシュする eShopOnContainers からの簡素化された次のコードのように、継承された実装により、独自のカスタムのホステッド サービス クラスで `ExecuteAsync()` メソッドを実装するだけで済みます。

```csharp
public class GracePeriodManagerService : BackgroundService
{        
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        //Constructor’s parameters validations...       
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() => 
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table 
            // and publishing events into the Event Bus (RabbitMS / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }
            
        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

eShopOnContainers のこの特定のケースでは、特定の状態を持つ注文を検索するデータベース テーブルに対してクエリを実行するアプリケーション メソッドを実行し、変更を適用するときに、イベント バスを介して統合イベントをパブリッシュします (その下で RabbitMQ または Azure Service Bus を使用できます)。

もちろん、代わりに他の任意のビジネス バックグラウンド タスクを実行することもできます。

既定では、キャンセル トークンは 5 秒のタイムアウトで設定されていますが、この値は、`IWebHostBuilder` の `UseShutdownTimeout` 拡張機能を使用して `WebHost` をビルドする際に変更することができます。 これは、サービスが 5 秒以内にキャンセルされることが想定されていて、そうでない場合は突然強制終了される可能性が高くなることを意味します。

次のコードでは、その時間を 10 秒に変更します。

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>クラス図の概要

次の図は、IHostedServices を実装する場合のクラスとインターフェイスの概要を視覚的に示しています。
 
![クラス ダイアグラム:IWebHost と IHost は、BackgroundService から継承され、IHostedService を実装する多くのサービスをホストできます。](./media/image27.png)

**図 6-27**。 IHostedService に関連する複数のクラスとインターフェイスを示すクラス図

### <a name="deployment-considerations-and-takeaways"></a>展開に関する注意事項と習得事項

ASP.NET Core `WebHost` または .NET Core `Host` を展開する方法が最終的なソリューションに影響を与える可能性があることに注意してください。 たとえば、`WebHost` を IIS または正規の Azure App Service に展開する場合、アプリ プールのリサイクルが原因でホストがシャットダウンされる場合があります。 ただし、ホストをコンテナーとして Kubernetes や Service Fabric などのオーケストレーターに展開する場合は、ご利用のホストのライブ インスタンスの確実な数を制御することができます。 さらに、Azure Functions のように、これらのシナリオ用に特別に作成されたクラウド内で、他の方法を検討することができます。 最後になりますが、サービスを常時実行する必要があるとき、および Windows Server にデプロイする場合、Windows Service を使用できることがあります。

ただし、アプリ プールに展開された `WebHost` に対しても、適用可能なアプリケーションのメモリ内キャッシュの再作成またはフラッシュのようなシナリオがあります。

`IHostedService` インターフェイスでは、(.NET Core 2.0 の) ASP.NET Core Web アプリケーションで、または (`IHost` を使用して .NET Core 2.1 で開始する) 任意のプロセス/ホストでバックグラウンド タスクを開始する便利な方法が提供されます。 その主な利点は、ホスト自体がシャットダウンするときに、バックグラウンド タスクのコードをクリーンアップするため、適切にキャンセルする機会が得られることです。

#### <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Core/Standard 2.0 でスケジュールされたタスクをビルドする** <br/>
    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **ASP.NET Core 2.0 で IHostedService を実装する** <br/>
    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **ASP.NET Core 2.1 を使用した GenericHost サンプル** <br/>
    [*https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample)

>[!div class="step-by-step"]
>[前へ](test-aspnet-core-services-web-apps.md)
>[次へ](implement-api-gateways-with-ocelot.md)

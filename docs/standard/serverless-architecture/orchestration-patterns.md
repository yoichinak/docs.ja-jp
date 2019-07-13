---
title: オーケストレーション パターン - サーバーレス アプリ
description: Azure の Durable functions の pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638803"
---
# <a name="orchestration-patterns"></a>オーケストレーション パターン

Durable Functions は、サーバーレス環境で、個別の実行時間の長いアクティビティで構成されるステートフルなワークフローの作成を容易にします。 Durable Functions では、実行履歴のワークフローと定期的にチェックポイントの進行状況を追跡できます、ために適しているいくつかの興味深いパターンを実装します。

## <a name="function-chaining"></a>関数チェーン

通常の順次プロセス アクティビティを特定の順序で 1 つずつ実行する必要があります。 必要に応じて、今後のアクティビティには、前の関数の出力が必要です。 アクティビティの順序付けにおけるこの依存関係は、実行の関数チェーンを作成します。

このワークフロー パターンを実装するために Durable Functions を使用する利点は、チェックポイント処理を実行するには、その能力から取得されます。 サーバーがクラッシュした場合、ネットワークがタイムアウトになるまたはその他の問題が発生した、Durable functions は、最後の既知の状態から再開し、別のサーバー上にある場合でも、ワークフローの実行を続行します。

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

上記のコード サンプル、`CallActivityAsync`関数は、データ センター内の仮想マシンで、特定のアクティビティを実行する責任を負います。 Await 返し、基になるタスクが完了したら、実行は、履歴テーブルに記録されます。 オーケストレーター関数のコードと、タスク並列ライブラリと async/await キーワードのおなじみの構成要素のいずれかを使用します。

次のコードは簡略化された例のような`ProcessPayment`メソッドのようになります。

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a>非同期 HTTP Api

ワークフローのアクティビティを完了するまでに比較的長い時間がかかることがあります。 Blob ストレージにファイルにこのメディアのバックアップを開始するプロセスを想像してください。 このバックアップ プロセスは、サイズとメディア ファイルの数量に応じて、完了までに時間をかかる場合があります。

このシナリオで、`DurableOrchestrationClient`の実行中のワークフローの状態を確認する機能が便利になります。 使用する場合、 `HttpTrigger` 、ワークフローを開始する、`CreateCheckStatusResponse`メソッドを使用してのインスタンスを返す`HttpResponseMessage`します。 この応答は、実行中のプロセスの状態を確認に使用できるペイロードの URI を持つクライアントを提供します。

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

次のサンプルの結果は、応答ペイロードの構造を示します。

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

優先する HTTP クライアントを使用して、GET 要求できる statusQueryGetUri で URI に実行中のワークフローの状態を検査します。 返された状態の応答は次のコードのようになります。

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

状態の応答がいずれかに変更は、プロセスでは、 **Failed**または**完了**します。 正常に完了、**出力**ペイロード内のプロパティは、返されるデータが格納されます。

## <a name="monitoring"></a>監視

単純な定期的なタスクでは、Azure Functions の提供、 `TimerTrigger` CRON 式に基づくをスケジュールすることができます。 タイマーは、単純な有効期間の短いタスクに適してより柔軟なスケジューリング機能が必要な場所のシナリオが発生する可能性があります。 このシナリオ、監視パターンと永続的な関数が役立つ場合です。

Durable Functions は、柔軟なスケジュールの間隔、有効期間管理、および 1 つのオーケストレーション関数からの複数のモニター プロセスを作成できます。 この機能の 1 つのユース ケースは、特定のしきい値が満たされると終了の株価の変更の監視を作成することです。

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

`DurableOrchestrationContext``CreateTimer`の株価の変更を確認するメソッドが、ループの次の呼び出しに対して、スケジュールを設定します。 `DurableOrchestrationContext` また、 `CurrentUtcDateTime` UTC で現在の DateTime 値を取得するプロパティ。 このプロパティの代わりに使用することをお勧め`DateTime.UtcNow`のため、テスト、モックは簡単にします。

## <a name="recommended-resources"></a>推奨リソース

* [Azure の Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [.NET Core と .NET Standard の単体テスト](../../core/testing/index.md)

>[!div class="step-by-step"]
>[前へ](durable-azure-functions.md)
>[次へ](serverless-business-scenarios.md)

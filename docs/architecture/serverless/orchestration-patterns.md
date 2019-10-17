---
title: オーケストレーションパターン-サーバーレスアプリ
description: Azure の持続性のある関数 pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522638"
---
# <a name="orchestration-patterns"></a>オーケストレーションパターン

Durable Functions を使用すると、サーバーレス環境で実行時間の長い個別のアクティビティで構成されるステートフルワークフローを簡単に作成できます。 Durable Functions はワークフローの進行状況を追跡して、実行履歴を定期的にチェックポイントするため、いくつかの興味深いパターンを実装するのに役立ちます。

## <a name="function-chaining"></a>関数チェーン

一般的なシーケンシャルプロセスでは、アクティビティは、特定の順序で1つずつ実行する必要があります。 必要に応じて、次のアクティビティでは、前の関数からの出力が必要になる場合があります。 アクティビティの順序に依存することで、実行の関数チェーンが作成されます。

このワークフローパターンを実装するために Durable Functions を使用する利点は、チェックポイント処理を実行できることです。 サーバーがクラッシュした場合、ネットワークがタイムアウトした場合、またはその他の問題が発生した場合、持続性のある関数は、最後の既知の状態から再開し、別のサーバー上にある場合でもワークフローの実行を継続できます。

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

前のコードサンプルでは、@no__t 0 関数は、データセンター内の仮想マシンで特定のアクティビティを実行します。 Await が返され、基になるタスクが完了すると、実行は履歴テーブルに記録されます。 Orchestrator 関数のコードでは、タスク並列ライブラリの使い慣れた構造と async/await キーワードを利用できます。

次のコードは、@no__t 0 のメソッドがどのようになるかを示す簡単な例です。

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

場合によっては、ワークフローに含まれるアクティビティが、完了するのに比較的長い時間がかかることがあります。 メディアファイルのバックアップを blob storage に開始するプロセスを考えてみましょう。 メディアファイルのサイズと数量によっては、このバックアッププロセスが完了するまでに数時間かかることがあります。

このシナリオでは、実行中のワークフローの状態を確認するための @no__t 0 の機能が有効になります。 @No__t-0 を使用してワークフローを開始する場合は、`CreateCheckStatusResponse` メソッドを使用して、`HttpResponseMessage` のインスタンスを返すことができます。 この応答は、実行中のプロセスの状態を確認するために使用できるペイロードの URI をクライアントに提供します。

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

次のサンプル結果は、応答ペイロードの構造を示しています。

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

優先 HTTP クライアントを使用して、statusQueryGetUri の URI に GET 要求を作成し、実行中のワークフローの状態を調べることができます。 返される状態の応答は、次のコードのようになります。

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

プロセスが続行されると、状態の応答は **[失敗]** または **[完了]** に変わります。 正常に完了すると、ペイロードの**出力**プロパティに返されるデータがすべて含まれます。

## <a name="monitoring"></a>監視

単純な定期的なタスクの場合、Azure Functions は CRON 式に基づいてスケジュールできる @no__t 0 を提供します。 タイマーは、単純で短時間のタスクに適していますが、より柔軟なスケジュール設定が必要なシナリオもあります。 このシナリオは、監視パターンと Durable Functions が役に立ちます。

Durable Functions を使用すると、柔軟なスケジュール間隔、有効期間の管理、および1つのオーケストレーション機能からの複数の監視プロセスの作成が可能になります。 この機能のユースケースの1つとして、特定のしきい値が満たされた後に完了する株価の変更に対してウォッチャーを作成することが考えられます。

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

`DurableOrchestrationContext` の @no__t メソッドは、株価の変化を確認するために、次にループを起動するスケジュールを設定します。 `DurableOrchestrationContext` には、現在の DateTime 値を UTC で取得するための `CurrentUtcDateTime` プロパティもあります。 テスト用に簡単にモックできるため、`DateTime.UtcNow` の代わりにこのプロパティを使用することをお勧めします。

## <a name="recommended-resources"></a>推奨されるリソース

- [Azure Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [.NET Core と .NET Standard の単体テスト](../../core/testing/index.md)

>[!div class="step-by-step"]
>[前へ](durable-azure-functions.md)
>[次へ](serverless-business-scenarios.md)

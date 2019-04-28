---
title: 持続性のある Azure functions でサーバーレス アプリ
description: 持続性のある Azure functions では、コード内のステートフルなワークフローを有効にする Azure Functions ランタイムを拡張します。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8ad354e1708eb88f016130f8235f534b967eb122
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776013"
---
# <a name="durable-azure-functions"></a>永続的な Azure Functions

Azure Functions でサーバーレス アプリケーションを作成するときに、オペレーション通常ステートレスな方法で実行する設計されています。 この設計の選択の理由としてのプラットフォームのスケールがでコードが実行されているどのサーバーがわかりにくいためにです。 難しく特定の時点でアクティブなインスタンスの数を把握します。 ただし、これには既知であるプロセスの現在の状態を必要とするアプリケーションのクラスがあります。 オンライン ストアへの注文を送信するプロセスを検討してください。 チェック アウト操作には、ワークフロー、プロセスの状態を確認する必要がある複数の操作を構成している可能性があります。 お客様は、クレジット カードの処理の結果と自分のアカウントでは、上の任意のクレジットを持っている場合、このような情報は、製品在庫を含めることができます。 これらの操作は、独自の内部ワークフローまたはサード パーティ システムからもサービスに簡単になります。

さまざまなパターンは、内部および外部のシステム間でアプリケーションの状態の調整時に役立つ今日存在します。 一元化されたキュー システム、分散キー値ストア、またはその状態を管理する共有データベースに依存するソリューション全体が一般的です。 ただし、これらは、ここでプロビジョニングし、管理する必要がある他のすべてのリソースです。 サーバーレス環境でコードを手動でこれらのリソースと調整しようとしています。 面倒になる可能性があります。 Azure Functions では、Durable Functions と呼ばれるステートフル関数を作成するための代替を提供します。

Durable Functions では、コード内のステートフルなワークフローの定義をできるようにする Azure Functions ランタイムの拡張機能です。 Durable Functions 拡張機能が状態を管理できますをアクティビティにワークフローを分解することによってには、進行状況のチェックポイントを作成して、サーバー間で関数呼び出しの配布を処理します。 バック グラウンドでの Azure Storage アカウントを使用して実行履歴が保持、アクティビティ関数をスケジュールし、応答の取得になります。 サーバーレス コードを使用して、そのストレージ アカウントに永続化された情報ことはありません対話する必要がありますでは通常ありません、開発者は対話する必要があります。

## <a name="triggering-a-stateful-workflow"></a>ステートフルなワークフローをトリガーします。

Durable Functions のステートフルなワークフローを 2 つの組み込みコンポーネント; に細分化できます。オーケストレーションとアクティビティがトリガーされます。 トリガーとバインドは、Azure Functions でサーバーレス関数を開始して受信するには、次のように入力、および結果を返すときに通知を有効にするために使用するコア コンポーネントです。

### <a name="working-with-the-orchestration-client"></a>オーケストレーション クライアントの使用

オーケストレーションは、Azure Functions でトリガーされた操作の他のスタイルと比較した場合に一意です。 Durable Functions では、時間がかかる場合があります、または完了するまで関数を実行できるようにします。 その種類の動作を実行中のオーケストレーションの状態を確認することが必要事前終了、または外部イベントの通知を送信します。

このような場合は、Durable Functions 拡張機能を提供します、`DurableOrchestrationClient`と対話できるクラスは、関数を調整します。 使用して、オーケストレーション クライアントにアクセスすること、`OrchestrationClientAttribute`バインドします。 一般に、するはこの属性を含めるもう 1 つのトリガーの種類をなど、`HttpTrigger`または`ServiceBusTrigger`します。 ソース関数がトリガーされると後、は、オーケストレーター関数を開始するオーケストレーション クライアントを使用できます。

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a>オーケストレーター関数

注釈を付けることで Azure Functions OrchestrationTriggerAttribute で関数をその関数、オーケストレーター関数として。 ステートフルなワークフローを構成するさまざまなアクティビティの管理を担当します。

オーケストレーター関数は、作成することはできません、OrchestrationTriggerAttribute 以外のバインディングを使用します。 この属性は、DurableOrchestrationContext のパラメーターの型でのみ使用できます。 関数シグネチャ内で入力の逆シリアル化がサポートされていないために、他の入力は使用されません。 オーケストレーション クライアント、GetInput によって指定された入力を取得する\<T\>メソッドを使用する必要があります。

また、オーケストレーション関数の戻り値の型がある必要がありますか void、タスク、または JSON のシリアル化可能な値。

> *エラー処理コードが簡潔にするため省略してをいます*

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

オーケストレーションの複数のインスタンスは、同時に開始され、実行中にすることができます。 呼び出す、`StartNewAsync`メソッドを`DurableOrchestrationClient`オーケストレーションの新しいインスタンスを起動します。 メソッドを返します、`Task<string>`オーケストレーションが開始されたときに完了します。 型の例外`TimeoutException`30 秒以内に、オーケストレーションが開始されていない場合にスローされます。

完成した`Task<string>`から`StartNewAsync`オーケストレーション インスタンスの一意の ID を含める必要があります。 このインスタンス ID は、その特定のオーケストレーションでの操作の呼び出しに使用できます。 オーケストレーションの状態の照会またはイベント通知を送信できます。

### <a name="the-activity-functions"></a>アクティビティ関数

アクティビティ関数は、個別の操作をまとめて、ワークフローを作成するオーケストレーション関数内で、構成を取得します。 実際の作業のほとんどが行う場所を示します。 ビジネス ロジックを表す、実行中のプロセス、および大規模なソリューションにパズルのピースを長いが。

`ActivityTriggerAttribute`型の関数パラメーターの注釈を設定するために使用`DurableActivityContext`します。 注釈を使用して通知、ランタイム関数はアクティビティ関数として使用するものであります。 使用してアクティビティ関数の入力値を取得、`GetInput<T>`のメソッド、`DurableActivityContext`パラメーター。

オーケストレーション関数と同様に、アクティビティ関数の戻り値の型がである void、タスク、または JSON のシリアル化可能な値。

アクティビティ関数内でスローされる例外を呼び出し元のオーケストレーター関数に送信されとして示されますが取得、`TaskFailedException`します。 この時点では、エラーをキャッチして、orchestrator のログに記録でき、アクティビティを再試行することができます。

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>推奨リソース

* [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Durable Functions のバインド](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Durable Functions でのインスタンスを管理します。](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[前へ](event-grid.md)
>[次へ](orchestration-patterns.md)
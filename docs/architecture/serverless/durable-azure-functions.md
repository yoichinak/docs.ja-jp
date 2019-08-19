---
title: 持続性のある Azure functions-サーバーレスアプリ
description: 持続性のある Azure functions により、Azure Functions ランタイムが拡張され、コードでステートフルワークフローが有効になります。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: f7ee74926d6658042120113b49dc763383881423
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577515"
---
# <a name="durable-azure-functions"></a>永続的な Azure Functions

Azure Functions でサーバーレスアプリケーションを作成する場合、通常、操作はステートレスな方法で実行するように設計されています。 この設計を選択する理由は、プラットフォームの規模が拡大するにつれて、コードが実行されているサーバーを把握するのが困難になるためです。 また、特定の時点でアクティブになっているインスタンスの数を把握することも困難になります。 ただし、プロセスの現在の状態を把握しておく必要があるアプリケーションのクラスがあります。 オンラインストアに注文を送信するプロセスを検討します。 チェックアウト操作は、プロセスの状態を知る必要がある複数の操作で構成されるワークフローである可能性があります。 このような情報には、顧客が自分のアカウントにクレジットを持っている場合や、クレジットカードを処理した結果が含まれる場合があります。 これらの操作は、独自の内部ワークフローや、サードパーティのシステムからのサービスとして簡単に行うことができます。

現在、内部システムと外部システムの間でのアプリケーションの状態の調整に役立つさまざまなパターンが用意されています。 集中管理されたキューシステム、分散キー値ストア、または共有データベースを使用してその状態を管理するソリューションによって、一般的に発生します。 ただし、これらは、プロビジョニングと管理が必要なすべての追加リソースです。 サーバーレス環境では、これらのリソースを手動で調整しようとすると、コードが煩雑になる可能性があります。 Azure Functions には、Durable Functions と呼ばれるステートフル関数を作成するための代替手段が用意されています。

Durable Functions は、コードでステートフルワークフローを定義できるようにする、Azure Functions ランタイムの拡張機能です。 ワークフローをアクティビティに分割することにより、Durable Functions の拡張機能は、状態の管理、進行状況のチェックポイントの作成、およびサーバー間での関数呼び出しの分散の処理を行うことができます。 バックグラウンドでは、Azure Storage アカウントを使用して、実行履歴の保持、アクティビティ関数のスケジュール設定、および応答の取得を行います。 サーバーレスコードは、そのストレージアカウント内の永続化された情報と対話することはできません。通常、開発者が操作する必要のあるものではありません。

## <a name="triggering-a-stateful-workflow"></a>ステートフルワークフローのトリガー

Durable Functions のステートフルワークフローは、次の2つの組み込みコンポーネントに分けることができます。オーケストレーショントリガーとアクティビティトリガー。 トリガーとバインドは、Azure Functions によって使用されるコアコンポーネントであり、サーバーレス関数が、開始、入力の受信、および結果を返すときに通知を受け取ることができるようにします。

### <a name="working-with-the-orchestration-client"></a>Orchestration クライアントの操作

オーケストレーションは、Azure Functions でトリガーされた操作の他のスタイルと比較した場合に一意です。 Durable Functions では、完了までに数時間または数日かかる可能性のある関数を実行できます。 この種類の動作には、実行中のオーケストレーションの状態を確認したり、事前にを終了したり、外部イベントの通知を送信したりできる必要があります。

このような場合、Durable Functions 拡張機能は`DurableOrchestrationClient` 、調整された関数と対話できるようにするクラスを提供します。 オーケストレーションクライアントにアクセスするには、 `OrchestrationClientAttribute`バインドを使用します。 通常、この属性は、 `HttpTrigger`や`ServiceBusTrigger`などの別のトリガーの種類と共に追加します。 ソース関数がトリガーされたら、オーケストレーションクライアントを使用して orchestrator 関数を開始できます。

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

### <a name="the-orchestrator-function"></a>Orchestrator 関数

Azure Functions マークの OrchestrationTriggerAttribute を使用して関数に注釈を付けると、orchestrator 関数として機能します。 ステートフルワークフローを構成するさまざまなアクティビティを管理する責任があります。

Orchestrator 関数で、OrchestrationTriggerAttribute 以外のバインドを使用することはできません。 この属性は、パラメーターの型が DurableOrchestrationContext の場合にのみ使用できます。 関数シグネチャの入力の逆シリアル化がサポートされていないため、他の入力を使用することはできません。 Orchestration クライアントによって提供される入力を取得する\<に\>は、getinput T メソッドを使用する必要があります。

また、オーケストレーション関数の戻り値の型は、void、Task、または JSON のシリアル化可能な値のいずれかである必要があります。

> *簡潔にするためにエラー処理コードが残されました*

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

オーケストレーションの複数のインスタンスを同時に開始して実行できます。 でメソッド`StartNewAsync`を呼び出すと、オーケストレーションの新しいインスタンスが起動されます。`DurableOrchestrationClient` メソッドは、オーケストレーション`Task<string>`が開始されたときに完了するを返します。 オーケストレーションが30秒`TimeoutException`以内に開始しなかった場合、型の例外がスローされます。

`Task<string>` 完了`StartNewAsync`したには、オーケストレーションインスタンスの一意の ID が含まれている必要があります。 このインスタンス ID を使用して、その特定のオーケストレーションに対する操作を呼び出すことができます。 オーケストレーションの状態を照会したり、イベント通知を送信したりすることができます。

### <a name="the-activity-functions"></a>アクティビティ関数

アクティビティ関数は、ワークフローを作成するためにオーケストレーション関数内にまとめて構成される個別の操作です。 ここでは、実際の作業のほとんどが行われます。 これらは、ビジネスロジック、長時間実行されるプロセス、およびパズルの部分を大規模なソリューションに表します。

は`ActivityTriggerAttribute` 、型`DurableActivityContext`の関数パラメーターに注釈を付けるために使用されます。 注釈を使用すると、関数がアクティビティ関数として使用されることをランタイムに通知します。 アクティビティ関数へ`DurableActivityContext`の入力値は、パラメーター `GetInput<T>`のメソッドを使用して取得されます。

オーケストレーション関数と同様に、アクティビティ関数の戻り値の型は、void、Task、または JSON のシリアル化可能な値のいずれかである必要があります。

アクティビティ関数内でスローされた未処理の例外は、呼び出し元の orchestrator 関数に送信され`TaskFailedException`、として表示されます。 この時点で、エラーが検出され、orchestrator に記録され、アクティビティを再試行できます。

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>推奨されるリソース

* [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Durable Functions のバインド](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Durable Functions でのインスタンスの管理](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[前へ](event-grid.md)
>[次へ](orchestration-patterns.md)

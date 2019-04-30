---
title: Azure Event Grid - サーバーレス アプリ
description: Azure Event Grid には、信頼性の高いイベントの配信と、イベントごとに従量課金モデルに非常に大きなスケールでのルーティング、サーバーレス ソリューションです。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4970130ede0c96c645129ee6c8c7d54cb1114042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959387"
---
# <a name="event-grid"></a>イベント グリッド

[Azure Event Grid](/azure/event-grid/overview)サーバーレス インフラストラクチャ イベント ベースのアプリケーションを提供します。 任意のソースからイベント グリッドに発行し、任意のプラットフォームからのメッセージを使用できます。 Event Grid では、組み込みのサポートをアプリケーションとの統合を効率化する Azure リソースからのイベントもあります。 たとえば、ファイルをアップロードするときに、アプリに通知する blob storage イベントにサブスクライブできます。 アプリケーションは、他のクラウドによって消費されるか、オンプレミスのアプリケーションをカスタム イベント グリッドのメッセージを公開できます。 Event Grid は、非常に大きなスケールを確実に処理するために構築されました。 発行およびサブスクライブを設定するために必要なインフラストラクチャのオーバーヘッドなしのメッセージのメリットを享受します。

![イベント グリッドのロゴ](./media/event-grid-logo.png)

Event grid の主要な機能は次のとおりです。

* 完全に管理されたイベントをルーティングします。
* ほぼリアルタイムのイベント配信します。
* Azure の内外両方の広範なカバレッジ。

## <a name="scenarios"></a>シナリオ

Event Grid は、複数の異なるシナリオを説明します。 このセクションでは、3 つの最も一般的なものについて説明します。

### <a name="ops-automation"></a>操作の自動化

![操作の自動化](./media/ops-automation.png)

Event Grid は速度の自動化を支援して、ポリシーの適用を通知することにより簡素化[Azure Automation](https://docs.microsoft.com/azure/automation)インフラストラクチャのプロビジョニング時にします。

### <a name="application-integration"></a>アプリケーションの統合

![アプリケーションの統合](./media/app-integration.png)

Event Grid を使用すると、アプリの他のサービスに接続します。 標準の HTTP プロトコルを使用しても従来のアプリに簡単に変更できます Event Grid メッセージを発行します。 Web フックの他のサービスと Event Grid メッセージを使用するプラットフォームを利用できます。

### <a name="serverless-apps"></a>サーバーレス アプリ

![サーバーレス アプリ](./media/serverless-apps.png)

Event Grid には、Azure Functions、Logic Apps、または独自のカスタム コードをトリガーできます。 Event Grid の使用の大きな利点は、使用するという、*プッシュ*イベントが発生したときにメッセージを送信するためのメカニズムです。 プッシュ アーキテクチャがより少ないリソースを消費しよりの方がスケーラビリティ*ポーリング*メカニズム。 ポーリングは、一定の間隔で更新プログラムを確認する必要があります。

## <a name="event-grid-vs-other-azure-messaging-services"></a>他の Azure メッセージング サービスとのイベント グリッド

Azure など、いくつかのメッセージング サービスを提供する[Event Hubs](https://docs.microsoft.com/azure/event-hubs)と[Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)します。 特定の一連のユース ケースに対処する各設計されています。 次の図では、サービスの違いの概要を提供します。

![Azure メッセージングの比較](./media/azure-messaging-services.png)

詳細な比較を参照してください。[メッセージング サービスの比較](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)します。

## <a name="performance-targets"></a>パフォーマンスのターゲット

次のパフォーマンスの利用、Event Grid の使用を保証します。

* 99 パーセン タイルでエンド ツー エンドの待機時間を未満にします。
* 99.99% の可用性。
* リージョンごとの 1 秒あたり 10,000, 000 イベント。
* リージョンあたり 1億サブスクリプション。
* パブリッシャーの待機時間の 50 ms。
* 24 時間は 1 日のウィンドウで保証された配信の指数のバックオフで再試行してください。
* 透過的な地域フェールオーバーします。

## <a name="event-grid-schema"></a>Event Grid スキーマ

Event Grid は、カスタム イベントをラップするのに標準スキーマを使用します。 スキーマは、カスタム データ要素をラップするエンベロープ似ています。 Event Grid メッセージの例を次に示します。

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

除く標準のすべてのメッセージについては、`data`プロパティ。 メッセージを検査して、使用することができます、`eventType`と`dataVersion`ペイロードのカスタム部分を逆シリアル化できません。

## <a name="azure-resources"></a>管理

Event Grid の使用の大きな利点は、Azure によって生成された自動メッセージです。 Azure では、リソースに自動で発行、*トピック*さまざまなイベントをサブスクライブすることができます。 次の表には、リソースの種類、メッセージの種類、および自動的に利用できるイベントが一覧表示します。

| Azure リソース | イベントの種類 | 説明 |
| -------------- | ---------- | ----------- |
| Azure サブスクリプション | Microsoft.Resources.ResourceWriteSuccess | 発生したときに、リソースの作成または更新操作は成功します。 |
| | Microsoft.Resources.ResourceWriteFailure | リソースの作成または更新操作が失敗したときに発生します。 |
| | Microsoft.Resources.ResourceWriteCancel | リソースが作成または更新操作が取り消された発生します。 |
|  | Microsoft.Resources.ResourceDeleteSuccess | リソースの削除操作が成功したときに発生します。 |
|  | Microsoft.Resources.ResourceDeleteFailure | リソースの削除操作が失敗したときに発生します。 |
| | Microsoft.Resources.ResourceDeleteCancel | リソースの削除操作が取り消されたときに発生します。 このイベントは、テンプレートのデプロイが取り消されたときに発生します。 |
| BLOB ストレージ | Microsoft.Storage.BlobCreated | Blob が作成されたときに発生します。 |
| | Microsoft.Storage.BlobDeleted | Blob が削除されたときに発生します。 |
| イベント ハブ | Microsoft.EventHub.CaptureFileCreated | キャプチャ ファイルが作成されたときに発生します。
| IoT Hub | Microsoft.Devices.DeviceCreated | デバイスが IoT hub に登録されているときに発行します。 |
| | Microsoft.Devices.DeviceDeleted | デバイスが IoT hub から削除されたときに発行します。 |
| リソース グループ | Microsoft.Resources.ResourceWriteSuccess | 発生したときに、リソースの作成または更新操作は成功します。 |
| | Microsoft.Resources.ResourceWriteFailure | リソースの作成または更新操作が失敗したときに発生します。 |
| | Microsoft.Resources.ResourceWriteCancel | リソースが作成または更新操作が取り消された発生します。 |
| | Microsoft.Resources.ResourceDeleteSuccess | リソースの削除操作が成功したときに発生します。 |
| | Microsoft.Resources.ResourceDeleteFailure | リソースの削除操作が失敗したときに発生します。 |
| | Microsoft.Resources.ResourceDeleteCancel | リソースの削除操作が取り消されたときに発生します。 このイベントは、テンプレートのデプロイが取り消されたときに発生します。 |

詳細については、次を参照してください。 [Azure Event Grid イベント スキーマ](https://docs.microsoft.com/azure/event-grid/event-schema)します。

Event Grid は、あらゆる種類のオンプレミスで実行されるものも含めて、アプリケーションからアクセスできます。

## <a name="conclusion"></a>まとめ

この章では、Azure Functions、Logic Apps、および Event Grid を構成している Azure のサーバーレス プラットフォームについて説明しました。 これらのリソースを使用して、すべてサーバーレス アプリケーション アーキテクチャを構築するまたは他のクラウド リソースと対話し、オンプレミス サーバーをハイブリッド ソリューションを作成できます。 などのサーバーレス データ プラットフォームと組み合わせて[Azure SQL](https://docs.microsoft.com/azure/sql-database)または[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)、完全に管理されたクラウド ネイティブ アプリケーションを構築できます。

## <a name="recommended-resources"></a>推奨リソース

* [App service プラン](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Application Insights Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure:サーバーレス Azure Functions を使用してクラウドにアプリを表示します。](https://channel9.msdn.com/events/Connect/2017/E102)
* [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure Event Grid イベント スキーマ](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
* [Azure Functions のドキュメント](https://docs.microsoft.com/azure/azure-functions)
* [Azure Functions のトリガーとバインドの概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
* [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
* [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [1.x と 2.x の比較関数](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [Azure をオンプレミス データ ゲートウェイとオンプレミス データ ソースに接続します。](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [Azure portal で初めての関数を作成します。](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [Azure CLI を使用した初めての関数を作成します。](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [Visual Studio を使用した初めての関数を作成します。](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [関数がサポートされている言語](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [Azure Functions を監視](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [Azure Functions プロキシを操作します。](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[前へ](logic-apps.md)
>[次へ](durable-azure-functions.md)

---
title: Azure Event Grid サーバーレスアプリ
description: Azure Event Grid は、信頼性の高いイベント配信と、イベントごとの従量課金モデルでの大規模なルーティングを実現するサーバーレスソリューションです。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522718"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview)は、イベントベースのアプリケーションのサーバーレスインフラストラクチャを提供します。 任意のソースから Event Grid に発行し、任意のプラットフォームからのメッセージを使用できます。 また Event Grid には、アプリケーションとの統合を効率化するために、Azure リソースからのイベントが組み込まれています。 たとえば、blob storage イベントをサブスクライブして、ファイルがアップロードされたときにアプリに通知することができます。 その後、アプリケーションは、他のクラウドまたはオンプレミスアプリケーションで使用されるカスタムの event grid メッセージを公開できます。 Event Grid は、大規模な処理を確実に処理するように構築されました。 必要なインフラストラクチャを設定するオーバーヘッドを発生させることなく、メッセージの公開とサブスクライブの利点を得ることができます。

![Event Grid ロゴ](./media/event-grid-logo.png)

Event grid の主な特徴は次のとおりです。

- 完全に管理されたイベントルーティング。
- 大規模なリアルタイムのイベント配信。
- Azure の内部と外部の両方で幅広くカバーされています。

## <a name="scenarios"></a>監視プロセス

Event Grid は、いくつかの異なるシナリオに対処します。 このセクションでは、最も一般的な3つの方法について説明します。

### <a name="ops-automation"></a>Ops の自動化

![Ops の自動化](./media/ops-automation.png)

Event Grid は、インフラストラクチャがプロビジョニングされたときに[Azure Automation](https://docs.microsoft.com/azure/automation)に通知することで、自動化を高速化し、ポリシーの適用を簡略化するのに役立ちます。

### <a name="application-integration"></a>アプリケーションの統合

![アプリケーションの統合](./media/app-integration.png)

Event Grid を使用して、アプリを他のサービスに接続することができます。 標準の HTTP プロトコルを使用すると、従来のアプリでも、Event Grid メッセージを発行するように簡単に変更できます。 Web フックは、他のサービスやプラットフォームが Event Grid メッセージを使用するために使用できます。

### <a name="serverless-apps"></a>サーバーレスアプリ

![サーバーレスアプリ](./media/serverless-apps.png)

Event Grid は、Azure Functions、Logic Apps、または独自のカスタムコードをトリガーできます。 Event Grid を使用する主な利点は、イベントの発生時に*プッシュ*メカニズムを使用してメッセージを送信することです。 プッシュアーキテクチャは、使用するリソースが減り、*ポーリング*メカニズムよりもパフォーマンスが向上します。 ポーリングでは、定期的に更新プログラムを確認する必要があります。

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid とその他の Azure メッセージングサービス

Azure には、 [Event Hubs](https://docs.microsoft.com/azure/event-hubs)や[Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)など、いくつかのメッセージングサービスが用意されています。 各は、特定のユースケースのセットに対応するように設計されています。 次の図は、サービス間の相違点の概要を示しています。

![Azure メッセージングの比較](./media/azure-messaging-services.png)

詳細な比較については、「 [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)」を参照してください。

## <a name="performance-targets"></a>パフォーマンスターゲット

Event Grid を使用すると、次のパフォーマンスの保証を活用できます。

- 秒未満は99パーセンタイルでエンドツーエンドの待機時間を短縮します。
- 99.99% の可用性。
- リージョンごとに1000万イベント/秒。
- リージョンごとの1億サブスクリプション。
- 50-ms パブリッシャーの待機時間。
- 1日のウィンドウで保証された配信を行うための指数バックオフによる24時間の再試行。
- 透過的なリージョン内フェールオーバー。

## <a name="event-grid-schema"></a>Event Grid スキーマ

Event Grid は、標準スキーマを使用してカスタムイベントをラップします。 スキーマは、カスタムデータ要素をラップするエンベロープに似ています。 Event Grid メッセージの例を次に示します。

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

メッセージに関するすべてのものは、`data` プロパティを除き、標準です。 メッセージを検査し、`eventType` と `dataVersion` を使用して、ペイロードのカスタム部分を逆シリアル化することができます。

## <a name="azure-resources"></a>管理

Event Grid を使用する主な利点は、Azure によって生成される自動メッセージです。 Azure では、さまざまなイベントをサブスクライブするための*トピック*にリソースが自動的に発行されます。 次の表に、自動的に使用できるリソースの種類、メッセージの種類、およびイベントを示します。

| Azure リソース | イベントの種類 | 説明 |
| -------------- | ---------- | ----------- |
| Azure サブスクリプション | ResourceWriteSuccess | リソースの作成または更新操作が成功したときに発生します。 |
| | Microsoft .Resources エラー | リソースの作成または更新操作が失敗したときに発生します。 |
| | Microsoft.resources.resourcewritecancel | リソースの作成または更新操作が取り消されたときに発生します。 |
|  | Microsoft.resources.resourcedeletesuccess | リソースの削除操作が成功したときに発生します。 |
|  | Microsoft .Resources. ResourceDeleteFailure | リソースの削除操作が失敗したときに発生します。 |
| | Microsoft.resources.resourcedeletecancel | リソースの削除操作が取り消されたときに発生します。 このイベントは、テンプレートのデプロイが取り消されたときに発生します。 |
| BLOB ストレージ | Microsoft. ストレージが作成されました | Blob が作成されたときに発生します。 |
| | Microsoft. ストレージが削除されました | Blob が削除されたときに発生します。 |
| イベントハブ | CaptureFileCreated | キャプチャファイルが作成されたときに発生します。
| IoT Hub | DeviceCreated | デバイスが IoT hub に登録されると発行されます。 |
| | Microsoft デバイス. DeviceDeleted | IoT hub からデバイスが削除されたときに発行されます。 |
| リソースグループ | ResourceWriteSuccess | リソースの作成または更新操作が成功したときに発生します。 |
| | Microsoft .Resources エラー | リソースの作成または更新操作が失敗したときに発生します。 |
| | Microsoft.resources.resourcewritecancel | リソースの作成または更新操作が取り消されたときに発生します。 |
| | Microsoft.resources.resourcedeletesuccess | リソースの削除操作が成功したときに発生します。 |
| | Microsoft .Resources. ResourceDeleteFailure | リソースの削除操作が失敗したときに発生します。 |
| | Microsoft.resources.resourcedeletecancel | リソースの削除操作が取り消されたときに発生します。 このイベントは、テンプレートのデプロイが取り消されたときに発生します。 |

詳細については、「 [Azure Event Grid イベントスキーマ](https://docs.microsoft.com/azure/event-grid/event-schema)」を参照してください。

オンプレミスで実行されているアプリケーションであっても、任意の種類のアプリケーションから Event Grid にアクセスできます。

## <a name="conclusion"></a>まとめ

この章では、Azure Functions、Logic Apps、および Event Grid で構成される Azure サーバーレスプラットフォームについて学習しました。 これらのリソースを使用して、完全なサーバーレスアプリアーキテクチャを構築したり、他のクラウドリソースやオンプレミスサーバーと対話するハイブリッドソリューションを作成したりすることができます。 [AZURE SQL](https://docs.microsoft.com/azure/sql-database)や[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)などのサーバーレスデータプラットフォームと組み合わせることで、完全に管理されたクラウドネイティブアプリケーションを構築できます。

## <a name="recommended-resources"></a>推奨されるリソース

- [App service プラン](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Application Insights Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure: サーバーレス Azure Functions を使用してアプリをクラウドに持ち込む](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Grid イベントスキーマ](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
- [Azure Functions のドキュメント](https://docs.microsoft.com/azure/azure-functions)
- [Azure Functions のトリガーとバインドの概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
- [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Functions 1.x と2.x を比較します。](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Azure のオンプレミスデータゲートウェイを使用したオンプレミスのデータソースへの接続](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Azure portal に最初の関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Azure CLI を使用して最初の関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Visual Studio を使用して初めての関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Functions でサポートされる言語](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Azure Functions の監視](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Azure Functions プロキシの操作](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[前へ](logic-apps.md)
>[次へ](durable-azure-functions.md)

---
title: Application Insights サーバーレスアプリ
description: Application Insights は、開発者が web アプリ、モバイルアプリ、デスクトップアプリ、およびマイクロサービスの問題を検出、トリアージ、および診断できるようにする、サーバーレス診断プラットフォームです。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 1f5b99fba448c2c1c12139524ffdcd3708b3c956
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577725"
---
# <a name="telemetry-with-application-insights"></a>Application Insights を使用したテレメトリ

[Application Insights](https://docs.microsoft.com/azure/application-insights)は、開発者が web アプリ、モバイルアプリ、デスクトップアプリ、およびマイクロサービスの問題を検出、トリアージ、および診断できるようにする、サーバーレス診断プラットフォームです。 ポータルでスイッチを反転するだけで、関数アプリの Application Insights を有効にすることができます。 Application Insights には、サーバーを構成したり、独自のデータベースをセットアップしたりすることなく、これらすべての機能が提供されます。 すべての Application Insights の機能は、アプリと自動的に統合されるサービスとして提供されます。

![Application Insights ロゴ](./media/application-insights-logo.png)

既存のアプリに Application Insights を追加することは、アプリケーションの設定にインストルメンテーションキーを追加するのと同じほど簡単です。 Application Insights では、次のことができます。

* 関数呼び出しの数、関数の実行にかかる時間、例外などのメトリックに基づいて、カスタムのグラフと警告を作成します。
* エラーとサーバーの例外を分析する
* 操作によってパフォーマンスを掘り下げ、サードパーティの依存関係の呼び出しにかかる時間を測定する
* 関数アプリをホストするすべてのサーバーの CPU 使用率、メモリ、および率を監視します
* 関数アプリの要求数や待機時間など、メトリックのライブストリームを表示します
* [分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)を使用して関数データの検索、クエリ、およびカスタムグラフの作成を行う

![メトリックスエクスプローラー](./media/metrics-explorer.png)

組み込みのテレメトリに加えて、カスタムテレメトリを生成することもできます。 次のコードスニペットは、関数アプリ用に設定されたインストルメンテーションキーを使用して、カスタムテレメトリクライアントを作成します。

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

次のコードは、 [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)インスタンスに新しい行を挿入するのにかかる時間を測定します。

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

結果のパフォーマンスグラフが表示されます。

![カスタムテレメトリ](./media/custom-telemetry.png)

カスタムテレメトリは、新しい行の挿入にかかる平均時間が32.6 ミリ秒であることを示しています。

Application Insights には、サーバーレスアプリケーションに関する詳細なテレメトリをログに記録するための強力で便利な方法が用意されています。 提供されているトレースとログ記録のレベルを完全に制御できます。 イベント、依存関係、ページビューなどのカスタム統計情報を追跡できます。 さらに、強力な分析により、重要な質問をしてグラフや高度な洞察を生成するクエリを作成できます。

詳細については、「 [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)」を参照してください。

>[!div class="step-by-step"]
>[前へ](azure-functions.md)
>[次へ](logic-apps.md)

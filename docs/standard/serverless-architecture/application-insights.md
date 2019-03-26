---
title: Application Insights - サーバーレス アプリ
description: Application Insights は、サーバーレス診断プラットフォーム開発者を検出、トリアージ、および web アプリ、モバイル アプリ、デスクトップ アプリ、マイクロ サービスでの問題を診断できます。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4884d483de07c1c2077f7280b6b77c6059572c0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154263"
---
# <a name="telemetry-with-application-insights"></a>Application Insights のテレメトリ

[Application Insights](https://docs.microsoft.com/azure/application-insights)サーバーレス診断プラットフォーム開発者を検出、トリアージ、および web アプリ、モバイル アプリ、デスクトップ アプリ、およびマイクロ サービスでの問題を診断できます。 ポータルで、スイッチを反転するだけで関数アプリで Application Insights にできます。 Application Insights では、サーバーを構成したり、独自のデータベースを設定することがなくこれらすべての機能を提供します。 すべての Application Insights の機能は、自動的に、アプリと統合されたサービスとして提供されます。

![Application Insights のロゴ](./media/application-insights-logo.png)

既存のアプリに Application Insights を追加することは、アプリケーションの設定に、インストルメンテーション キーを追加する同じくらい簡単です。 Application Insights は、次のことができます。

* カスタムのグラフと、関数、および例外の実行にかかる時間に、関数の呼び出しの数などのメトリックに基づいてアラートを作成します。
* サーバー例外とエラーを分析します。
* 操作によってパフォーマンスにドリルダウンして、サード パーティの依存関係の呼び出しにかかる時間を測定します。
* 関数アプリをホストするすべてのサーバー間での CPU 使用率、メモリ、および料金を監視します。
* 要求の数と、関数アプリの待機時間などのメトリックのライブ ストリームを表示します。
* 使用[Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)を検索するには、クエリ、および関数、データに対するカスタム グラフを作成します。

![メトリックス エクスプ ローラー](./media/metrics-explorer.png)

組み込みのテレメトリに加えて、カスタム テレメトリを生成することがもします。 次のコード スニペットは、インストルメンテーション キーを関数アプリの設定を使用してカスタムのテレメトリ クライアントを作成します。

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

次のコードに新しい行の挿入にかかる時間を測定する[Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)インスタンス。

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

結果として得られるパフォーマンス グラフが表示されます。

![カスタム テレメトリ](./media/custom-telemetry.png)

カスタムのテレメトリは、新しい行を挿入する平均時間は 32.6 (ミリ秒) が表示されます。

Application Insights では、サーバーレス アプリケーションに関する詳細な製品利用統計情報を記録する強力な便利な手段を提供します。 トレースのレベルに対するフル コントロールがあり、ログが提供されます。 イベント、依存関係、およびページ ビューなどのカスタムの統計を追跡することができます。 最後に、強力な分析では、重要な質問したり、グラフと高度な洞察を生成するクエリの作成を有効にします。

詳細については、[Azure Functions を監視](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)を参照してください。

>[!div class="step-by-step"]
>[前へ](azure-functions.md)
>[次へ](logic-apps.md)
---
title: NET 用 Azure SDK でのログ記録
description: Azure SDK for .NET クライアント ライブラリでログ記録を有効にする方法を確認する
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "81433224"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>NET 用 Azure SDK でのログ記録

[Azure SDK](https://azure.microsoft.com/downloads/) for .NET クライアント ライブラリには、クライアント ライブラリ操作をログに記録する機能が含まれています。 これにより、クライアント ライブラリが Azure サービスに対して行っている I/O 要求と応答を監視できます。 通常、ログは、通信の問題をデバッグまたは診断するために使用されます。 この記事では、Azure SDK for .NET でログを記録するための 3 つの方法について説明します。

- コンソール ウィンドウにログを記録する
- NET 診断トレースにログを記録する
- カスタム ログの構成

> [!IMPORTANT]
> この記事は、最新バージョンの Azure SDK for .NET を使用するクライアント ライブラリに適用されます。 ライブラリがサポートされているかどうかを確認するには[、Azure SDK の最新リリース](https://azure.github.io/azure-sdk/releases/latest/index.html)の一覧を参照してください。 アプリケーションで古いバージョンの Azure SDK クライアント ライブラリを使用している場合は、該当するサービス のドキュメントの特定の手順を参照してください。

## <a name="log-information"></a>ログ情報

SDK は、次の情報をログに記録し、パラメーター クエリとヘッダー値をサニタイズして個人データを削除します。

HTTP 要求ログエントリ:

- 固有の ID
- HTTP メソッド
- URI
- 送信要求ヘッダー

HTTP 応答ログ エントリ:

- I/O操作の継続時間(経過時間)
- 要求 ID
- HTTP 状態コード
- HTTP 理由句
- 応答ヘッダー
- エラー情報 (該当する場合)

要求および応答のコンテンツの場合:

- コンテンツ・ストリームは、コンテンツ・タイプ・ヘッダーに応じてテキストまたはバイトとしてストリームされます。
     > [!NOTE} コンテンツ ログは既定で無効になっています。 有効にするには、`Diagnostics.IsLoggingContentEnabled``true`に`ClientOptions`設定します。

イベント ログは、通常、次の 3 つのレベルのいずれかで出力されます。

- 要求イベントおよび応答イベントの情報提供
- エラーの警告
- 詳細メッセージとコンテンツ ログの詳細

## <a name="enable-logging-with-built-in-methods"></a>組み込みメソッドでログを有効にする

Azure SDK for .NET クライアント ライブラリは[`EventSource`、.NET](/dotnet/api/system.diagnostics.tracing.eventsource)の一般的なクラスを介してイベント トレース (ETW) にイベントを記録します。 イベント ソースを使用すると、アプリケーション コードで構造化ログを使用し、パフォーマンスのオーバーヘッドを最小限に抑えることができます。 これらのイベント ログにアクセスするには、イベント リスナーを登録する必要があります。

SDK にはクラス`Azure.Core.Diagnostics.AzureEventSourceListener`(Azure.Core NuGet パッケージで定義) が含まれており、.NET アプリケーションの包括的なログ記録`CreateConsoleLogger`を`CreateTraceLogger`簡素化する 2 つの静的メソッドが含まれています。 これらのメソッドは、ログ レベルを指定する省略可能なパラメーターを受け取ります。

### <a name="log-to-the-console-window"></a>コンソール ウィンドウにログを記録する

Azure SDK for .NET クライアント ライブラリの主要な原則は、包括的なログをリアルタイムで表示する機能を簡略化することです。 この`CreateConsoleLogger`メソッドを使用すると、1 行のコードでログをコンソール ウィンドウに送信できます。

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>診断トレースにログを記録する

トレース リスナーを実装する場合は、このメソッド`CreateTraceLogger`を使用して、標準の .NET イベント[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)トレース メカニズム ( ) にログを記録できます。 NET でのイベント トレースの詳細については、「[トレース リスナー](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners)」を参照してください。 この例では、詳細のログ レベルを指定します。

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>カスタム ログの構成

前述したように、.NET 用 Azure SDK からログ メッセージを受信するイベント リスナーを登録する必要があります。 上記の単純化されたメソッドを使用して包括的なログを実装しない場合は、`AzureEventSourceListener`クラスのインスタンスを構築し、記述したコールバック関数を渡すことができます。 このメソッドは、必要に応じて処理できるログ メッセージを受信します。 また、インスタンスを構築するときに、含めるログレベルを指定できます。

次の例では、カスタム メッセージを使用してコンソールにログを記録し、詳細レベルの Azure コア イベントにフィルター処理されるイベント リスナーを作成します。

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a>次のステップ

- [Azure App Service でのアプリの診断ログの有効化](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- [Azure のセキュリティ ログと監査](https://docs.microsoft.com/azure/security/fundamentals/log-audit)のオプションを確認する
- [Azure プラットフォーム ログ](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)の操作方法の詳細
- [NET Core のログとトレース](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)の詳細を参照してください。

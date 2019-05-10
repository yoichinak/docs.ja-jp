---
title: Azure Functions でサーバーレス アプリ
description: Azure functions は、複数の言語 (c#、JavaScript、Java) サーバーレス機能を提供し、インスタント イベント ドリブンを提供するプラットフォームは、コードを拡張します。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754232"
---
# <a name="azure-functions"></a>Azure Functions 

Azure 関数は、サーバーレス コンピューティング エクスペリエンスを提供します。 によって、関数が呼び出される、*トリガー* (など、HTTP エンドポイントまたはタイマーへのアクセス) コードまたはビジネス ロジックのブロックを実行します。 関数のサポートが特殊化も*バインド*ストレージやキューなどのリソースに接続します。

![Azure functions のロゴ](./media/azure-functions-logo.png)

Azure Functions フレームワークの 2 つのバージョンがあります。 従来のバージョンは、完全な .NET Framework をサポートしています。 新しいランタイムは、クロス プラットフォーム対応 .NET Core アプリケーションをサポートしています。 追加の言語だけでなくC#JavaScript などF#、Java がサポートされているとします。 ポータルで作成した関数では、豊富なスクリプト構文を提供します。 完全なプラットフォームのサポートと機能を持つスタンドアロン プロジェクトとして作成した関数をデプロイできます。

詳細については、次を参照してください。 [Azure Functions のドキュメント](https://docs.microsoft.com/azure/azure-functions)します。

## <a name="functions-v1-vs-v2"></a>関数の v1 と v2 の比較

Azure Functions ランタイムの 2 つのバージョンがあります。1.x と 2.x の場合は。 バージョン 1.x が一般公開 (GA) します。 ポータルまたは Windows マシンからの .NET 開発をサポートし、.NET Framework を使用します。 1.x がサポートしているC#、JavaScript、およびF#、Python、PHP、TypeScript、Batch、Bash、および PowerShell の実験的なサポートをします。

[バージョン 2.x は一般的に使用できるようになりましたことも、](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)します。 .NET Core を利用し、Windows、macOS、および Linux マシンでのクロス プラットフォーム開発をサポートしています。 2.x の Java のファースト クラスのサポートを追加しますがまだ直接サポートしていません試験段階の言語のいずれか。 バージョン 2.x のバインディングの独立したバージョン管理、プラットフォームにサード パーティ製の拡張機能を有効にする新しいバインディング拡張モデルを使用してより実行環境を簡素化します。

> **1.x の既知の問題がある[バインディング リダイレクト サポート](https://github.com/Azure/azure-functions-host/issues/992)します。** この問題は、.NET 開発に固有です。 ランタイムに含まれるライブラリから別のバージョンのライブラリへの依存関係を使用したプロジェクトが影響を受けます。 Functions チームが問題の具体的な進行状況をコミットします。 一般に入る前に、チームは 2.x でバインド リダイレクトを対処します。 チームの公式ステートメントの推奨される修正プログラムや回避策は、ここで入手できます。[Azure Functions でのアセンブリ解決](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)します。

詳細については、次を参照してください。 [1.x と 2.x の比較](https://docs.microsoft.com/azure/azure-functions/functions-versions)します。

## <a name="programming-language-support"></a>プログラミング言語のサポート

次の言語がサポートされているか、一般公開 (GA) をプレビューまたは試験用。

|言語      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |[プレビュー]  |
|**JavaScript**|GA          |[プレビュー]  |
|**F#**        |GA          |         |
|**Java**      |            |[プレビュー]  |
|**Python**    |実験用|         |
|**PHP**       |実験用|         |
|**TypeScript**|実験用|         |
|**Batch**     |実験用|         |
|**Bash**      |実験用|         |
|**PowerShell**|実験用|         |

詳細については、次を参照してください。[サポートされる言語](https://docs.microsoft.com/azure/azure-functions/supported-languages)します。

## <a name="app-service-plans"></a>App service プラン

関数が支え、 *app service プラン*します。 プランは、関数アプリで使用されるリソースを定義します。 リージョンにプランを割り当てるを使用して、価格レベルを選択する仮想マシンの数とサイズを決定できます。 True のサーバーレス アプローチでは、関数アプリを使うことが、**消費**計画します。 従量課金プランでは、バックエンドの負荷に基づいて自動的に拡大縮小されます。

詳細については、次を参照してください。 [App service プラン](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)します。

## <a name="create-your-first-function"></a>最初の関数を作成します。

関数アプリを作成する 3 つの一般的な方法はあります。

* ポータルでのスクリプト機能します。
* Azure コマンド ライン インターフェイス (CLI) を使用しているために必要なリソースを作成します。
* お気に入りの IDE を使用してローカルで関数をビルドし、それらを Azure に発行します。

ポータルでスクリプト化された関数を作成する方法の詳細については、次を参照してください。 [、Azure portal で初めての関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)します。

Azure CLI から作成するを参照してください。 [Azure CLI を使用した初めての関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)します。

Visual Studio から関数を作成するを参照してください。 [Visual Studio を使用した初めての関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)します。

## <a name="understand-triggers-and-bindings"></a>トリガーとバインドを理解します。

関数を呼び出す、*トリガー* 1 つだけ持つことができます。 関数を呼び出すだけでなく特定のトリガーはバインドとしても機能します。 複数のバインドだけでなく、トリガーを定義することもできます。 *バインド*宣言型データ、コードを接続する方法を提供します。 (入力) に渡すことができる、またはデータ (出力) を受信します。 トリガーとバインドする関数も使用する簡単にできます。 バインドは、手動で接続を作成するデータベースまたはファイル システムのオーバーヘッドを削除します。 特殊なに含まれているすべてのバインドのために必要な情報が*functions.json*スクリプトのファイルまたはコード内の属性で宣言されています。

いくつかの一般的なトリガーは次のとおりです。

* Blob Storage: は、ファイルまたはフォルダーをアップロードまたはストレージに変更されたときに、関数を呼び出します。
* HTTP: は、REST API のような関数を呼び出します。
* : キューは、キュー内の項目が存在する場合に、関数を呼び出します。
* タイマー: は、一定のリズムで関数を呼び出します。

バインドの例は次のとおりです。

* Cosmos Db: は、読み込みまたはファイルを保存するデータベースに簡単に接続します。
* テーブル ストレージ: function app からキー/値ストレージを使用します。
* Queue Storage: は簡単に、キューから項目を取得または、新しいアイテムをキューに配置します。

次の例では、 *functions.json*ファイルは、トリガーとバインドを定義します。

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

内の blob ストレージへの変更により、この例では、関数がトリガーされる、`images`コンテナー。 ファイルの情報は、トリガーは、バインディングとしても機能するために渡されます。 という名前のキューに情報を配置する別のバインドが存在する`images`します。

関数の c# スクリプトを次に示します。

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

例は、ファイルの名前を受け取る単純な関数が変更されたまたは blob storage にアップロードし、後で処理するためのキューに配置されます。

トリガーとバインドの一覧については、次を参照してください。 [Azure Functions のトリガーとバインドの概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)します。

## <a name="proxies"></a>プロキシ

プロキシは、アプリケーションのリダイレクト機能を提供します。 プロキシは、エンドポイントを公開し、そのエンドポイントを別のリソースにマップします。 プロキシは、次のことができます。

* 別のエンドポイントに受信要求を再ルーティングします。
* に沿って渡す前に、着信要求を変更します。
* 変更するか、応答を提供します。

プロキシがなどのシナリオで使用されます。

* 単純化するか、短縮するには、URL を変更します。
* 複数のバックエンド サービスへの一貫性のある API プレフィックスを提供します。
* 開発中のエンドポイントへの応答のモックを作成します。
* 既知のエンドポイントへの静的な応答を提供します。
* API エンドポイントの一致の維持、バック エンドが移動または移行中にします。

プロキシは、JSON 定義として保存されます。 次に例を示します。

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

`Domain Redirect`プロキシが簡略化されたルートに受け取り、長い関数のリソースにマップします。 変換は、ようになります。

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

`Root`プロキシはルート URL に送信されたもの (`https://--shorturl--/`) し、ドキュメント サイトにリダイレクトします。

ビデオのプロキシを使用する例が示すように[Azure:サーバーレス Azure Functions を使用してクラウドにアプリをもたらす](https://channel9.msdn.com/events/Connect/2017/E102)します。 リアルタイムでローカルの SQL Server で実行されている ASP.NET Core アプリケーションは、Azure クラウドに移行されます。 プロキシは、関数を使用する従来の Web API プロジェクトのリファクタリングのために使用されます。

プロキシの詳細については、次を参照してください。 [Azure Functions proxies 作業](https://docs.microsoft.com/azure/azure-functions/functions-proxies)します。

>[!div class="step-by-step"]
>[前へ](azure-serverless-platform.md)
>[次へ](application-insights.md)

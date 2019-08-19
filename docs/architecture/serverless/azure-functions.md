---
title: Azure Functions サーバーレスアプリ
description: Azure functions では、複数の言語 (C#、JavaScript、Java) とプラットフォームに対してサーバーレスの機能を提供し、イベントドリブンのインスタントスケールコードを提供します。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577605"
---
# <a name="azure-functions"></a>Azure Functions

Azure functions は、サーバーレスのコンピューティングエクスペリエンスを提供します。 関数は、*トリガー* (HTTP エンドポイントまたはタイマーへのアクセスなど) によって呼び出され、コードまたはビジネスロジックのブロックを実行します。 関数は、ストレージやキューなどのリソースに接続する特殊な*バインド*もサポートします。

![Azure functions のロゴ](./media/azure-functions-logo.png)

Azure Functions framework には2つのバージョンがあります。 レガシバージョンでは完全な .NET Framework がサポートされており、新しいランタイムはクロスプラットフォームの .NET Core アプリケーションをサポートしています。 JavaScript、 F#、 C# Java など、その他の言語もサポートされています。 ポータルで作成された関数は、豊富なスクリプト構文を提供します。 スタンドアロンプロジェクトとして作成された関数は、完全なプラットフォームのサポートおよび機能を使用して配置できます。

詳細については、 [Azure Functions のドキュメント](https://docs.microsoft.com/azure/azure-functions)を参照してください。

## <a name="functions-v1-vs-v2"></a>Functions v1 と v2

Azure Functions ランタイムには、次の2つのバージョンがあります。1.x および2.x。 バージョン1.x は一般公開 (GA) されています。 ポータルまたは Windows マシンからの .NET 開発をサポートし、.NET Framework を使用します。 1.x は、Python C#、PHP、TypeScript F#、Batch、Bash、および PowerShell の実験的なサポートを使用して、、JavaScript、およびをサポートしています。

[バージョン2.x も一般公開さ](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)れています。 .NET Core を活用し、Windows、macOS、Linux コンピューターでのクロスプラットフォーム開発をサポートします。 2.x では Java のファーストクラスのサポートが追加されますが、実験的な言語はまだ直接サポートされていません。 バージョン2.x では、新しいバインド拡張モデルを使用して、プラットフォームに対するサードパーティ製の拡張機能、バインドの独立したバージョン管理、より合理化された実行環境を実現しています。

> **1. x に[バインドリダイレクトをサポート](https://github.com/Azure/azure-functions-host/issues/992)する既知の問題があります。** この問題は、.NET 開発に固有のものです。 ランタイムに含まれているライブラリとは異なるバージョンのライブラリに依存しているプロジェクトが影響を受けます。 Functions チームは、問題の具体的な進行状況に取り組んでいます。 チームは、一般公開される前に、2. x のバインドリダイレクトに対応します。 修正案と回避策が記載された公式のチームステートメントについては、こちらを参照してください。[Azure Functions でのアセンブリの解決](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。

詳細については、「 [1. x と](https://docs.microsoft.com/azure/azure-functions/functions-versions)2.X を比較する」を参照してください。

## <a name="programming-language-support"></a>プログラミング言語のサポート

次の言語は、一般公開 (GA)、プレビュー、試験段階のいずれかでサポートされています。

|言語      |記憶         |2.x      |
|--------------|------------|---------|
|**C#**        |VGA          |[プレビュー]  |
|**JavaScript**|VGA          |[プレビュー]  |
|**F#**        |VGA          |         |
|**Java**      |            |[プレビュー]  |
|**Python**    |実験用|         |
|**PHP**       |実験用|         |
|**TypeScript**|実験用|         |
|**Batch**     |実験用|         |
|**Bash**      |実験用|         |
|**PowerShell**|実験用|         |

詳細については、「[サポートされる言語](https://docs.microsoft.com/azure/azure-functions/supported-languages)」を参照してください。

## <a name="app-service-plans"></a>App service プラン

関数は、 *app service プラン*によって支えられています。 このプランでは、functions アプリによって使用されるリソースを定義します。 リージョンにプランを割り当てたり、使用される仮想マシンのサイズと数を決定したり、価格レベルを選択したりできます。 真のサーバーレスアプローチの場合、関数アプリは**従量課金**プランを使用することがあります。 従量課金プランでは、負荷に基づいてバックエンドが自動的にスケールされます。

詳細については、「 [App service プラン](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)」を参照してください。

## <a name="create-your-first-function"></a>最初の関数を作成する

関数アプリを作成するには、次の3つの一般的な方法があります。

* ポータルで関数をスクリプト化します。
* Azure コマンドラインインターフェイス (CLI) を使用して必要なリソースを作成します。
* お気に入りの IDE を使用してローカルで関数をビルドし、Azure に発行します。

ポータルでスクリプト化された関数を作成する方法の詳細については、「 [Azure portal で最初の関数を作成](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)する」を参照してください。

Azure CLI から構築するには、「 [Azure CLI を使用した初め](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)ての関数の作成」を参照してください。

Visual Studio から関数を作成する方法については、「 [Visual studio を使用して初めての関数を作成](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)する」を参照してください。

## <a name="understand-triggers-and-bindings"></a>トリガーとバインドについて

関数は*トリガー*によって呼び出され、1つだけを持つことができます。 関数を呼び出すだけでなく、特定のトリガーもバインドとして機能します。 トリガーに加えて、複数のバインドを定義することもできます。 *バインディング*は、データをコードに接続するための宣言的な方法を提供します。 これらは、渡す (入力) か、データを受信する (出力) ことができます。 トリガーとバインドを使用すると、関数が簡単に操作できるようになります。 バインドによって、データベースまたはファイルシステムの接続を手動で作成するオーバーヘッドが解消されます。 バインドに必要なすべての情報は、特別な関数の json ファイルに格納されてい*ます。* スクリプトの場合や、属性を使用してコードで宣言されている場合です。

次のような一般的なトリガーがあります。

* Blob Storage: ファイルまたはフォルダーがストレージでアップロードまたは変更されたときに、関数を呼び出します。
* HTTP: REST API のように関数を呼び出します。
* Queue: キューに項目が存在する場合に関数を呼び出します。
* Timer: 関数を定期的に呼び出します。

バインディングの例を次に示します。

* CosmosDB: データベースに簡単に接続して、ファイルを読み込んだり保存したりできます。
* Table Storage: 関数アプリからキー/値のストレージを操作します。
* Queue Storage: キューから項目を簡単に取得したり、新しい項目をキューに配置したりできます。

次の関数の例では、トリガーとバインディングを定義して*います。*

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

この例では、 `images`コンテナー内の blob ストレージに対する変更によって関数がトリガーされます。 ファイルの情報が渡されるため、トリガーはバインドとしても機能します。 という名前`images`のキューに情報を格納するための別のバインディングが存在します。

関数のC#スクリプトを次に示します。

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

この例は、blob ストレージに変更またはアップロードされたファイルの名前を取得し、後で処理するためにキューに配置する単純な関数です。

トリガーとバインディングの完全な一覧については、「 [Azure Functions のトリガーとバインドの概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)」を参照してください。

## <a name="proxies"></a>プロキシ

プロキシは、アプリケーションのリダイレクト機能を提供します。 プロキシはエンドポイントを公開し、そのエンドポイントを別のリソースにマップします。 プロキシを使用すると、次のことができます。

* 受信要求を別のエンドポイントに再ルーティングします。
* 渡される前に受信要求を変更します。
* 応答を変更または提供します。

プロキシは、次のようなシナリオで使用されます。

* URL の簡略化、短縮、または変更。
* 一貫した API プレフィックスを複数のバックエンドサービスに提供します。
* 開発中のエンドポイントへの応答をモックします。
* 既知のエンドポイントへの静的な応答を提供します。
* バックエンドの移動または移行中に、API エンドポイントの整合性を維持します。

プロキシは JSON 定義として格納されます。 次に例を示します。

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

プロキシ`Domain Redirect`は、短いルートを取得し、それより長い関数リソースにマップします。 変換は次のようになります。

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

プロキシ`Root`は、ルート URL (`https://--shorturl--/`) に送信されたすべてのものを取得し、ドキュメントサイトにリダイレクトします。

プロキシの使用例については、Azure [のビデオを参照してください。サーバーレス Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)を使用して、アプリをクラウドに持ち込むことができます。 ローカル SQL Server で実行されている ASP.NET Core アプリケーションは、リアルタイムで Azure クラウドに移行されます。 プロキシは、従来の Web API プロジェクトをリファクターして関数を使用するために使用されます。

プロキシの詳細については、「 [Azure Functions プロキシの操作](https://docs.microsoft.com/azure/azure-functions/functions-proxies)」を参照してください。

>[!div class="step-by-step"]
>[前へ](azure-serverless-platform.md)
>[次へ](application-insights.md)

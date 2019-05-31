---
title: Azure Functions にモデルをデプロイする
description: Azure Functions を使用して、インターネット経由で予測用の ML.NET 感情分析機械学習モデルを提供します
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 9e62d8826227aed07451387cc733d27094327f99
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645104"
---
# <a name="deploy-a-model-to-azure-functions"></a>Azure Functions にモデルをデプロイする

Azure Functions のサーバーレス環境を介して、HTTP 経由での予測のために、事前トレーニング済みの ML.NET 機械学習モデルをデプロイする方法について説明します。

> [!NOTE]
> `PredictionEnginePool` サービスの拡張機能は、現在プレビュー段階です。

## <a name="prerequisites"></a>必須コンポーネント

- [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" ワークロードおよび "Azure 開発" とともにインストールされていること。
- [Azure Functions ツール](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- 事前トレーニング済みモデル [ML.NET Sentiment Analysis のチュートリアル](../tutorials/sentiment-analysis.md)を使用して独自のモデルを構築するか、この[事前トレーニング済みの感情分析の機械学習モデル](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)をダウンロードすること。

## <a name="create-azure-functions-project"></a>Azure Functions プロジェクトを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、 **[Visual C#]** ノードを選択し、 **[クラウド]** ノードを選択します。 次に、**Azure Functions** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「SentimentAnalysisFunctionsApp」と入力し、 **[OK]** を選択します。
1. **[新しいプロジェクト]** ダイアログで、プロジェクト オプションの上のドロップダウンを開き、 **[Azure Functions v2 (.NET Core)]** を選択します。 次に、 **[Http トリガー]** プロジェクトを選択し、 **[OK]** ボタンを選択します。
1. モデルを保存するための *MLModels* という名前のディレクトリをプロジェクト内に作成します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しいフォルダー]** を選択します。 「MLModels」と入力し、Enter キーを押します。

1. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、 **[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

1. **Microsoft.Extensions.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。 パッケージ ソースとして "nuget.org" を選択します。[参照] タブを選択し、「**Microsoft.Extensions.ML**」を検索します。一覧からそのパッケージを選択して、 **[インストール]** ボタンを選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

## <a name="add-pre-trained-model-to-project"></a>事前トレーニング済みモデルをプロジェクトに追加する

1. 構築済みのモデルを *MLModels* フォルダーにコピーします。
1. ソリューション エクスプローラーで、構築済みのモデルのファイルを右クリックし、 **[プロパティ]** を選択します。 **[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

## <a name="create-azure-function-to-analyze-sentiment"></a>Azure 関数を作成してセンチメントを分析する

センチメントを予測するクラスを作成します。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、 **[Azure 関数]** を選択し、 **[名前]** フィールドを *SentimentData.cs* に変更します。 次に、 **[追加]** を選択します。

1. **[新しい Azure 関数]** ダイアログ ボックスで、 **[Http トリガー]** を選択します。 次に、 **[OK]** ボタンを選択します。

    コード エディターに *AnalyzeSentiment.cs* ファイルが開きます。 *AnalyzeSentiment.cs* の先頭に次の `using` ステートメントを追加します。

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    既定では、`AnalyzeSentiment` クラスは `static`です。 クラス定義から `static` キーワードを必ず削除します。

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>データ モデルを作成する

入力データと予測のために、いくつかのクラスを作成する必要があります。 プロジェクトに新しいクラスを追加します。

1. データ モデルを保存するための *DataModels* という名前のディレクトリをプロジェクト内に作成します。ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[追加]、[新しいフォルダー]** の順に選択します。 「DataModels」と入力し、Enter キーを押します。
2. ソリューション エクスプローラーで、*DataModels* ディレクトリを右クリックし、 **[追加]、[新しいアイテム]** の順に選択します。
3. **[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *SentimentData.cs* に変更します。 次に、 **[追加]** を選択します。 

    コード エディターで *SentimentData.cs* ファイルが開きます。 *SentimentData.cs* の先頭に次の using ステートメントを追加します。

    ```csharp
    using Microsoft.ML.Data;
    ```

    既存のクラス定義を削除し、次のコードを *SentimentData.cs* ファイルに追加します。
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. ソリューション エクスプローラーで、*DataModels* ディレクトリを右クリックし、 **[追加]、[新しいアイテム]** の順に選択します。
5. **[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *SentimentPrediction.cs* に変更します。 次に、 **[追加]** を選択します。 コード エディターに *SentimentPrediction.cs* ファイルが開きます。 *SentimentPrediction.cs* の先頭に次の using ステートメントを追加します。

    ```csharp
    using Microsoft.ML.Data;
    ```

    既存のクラス定義を削除し、次のコードを *SentimentPrediction.cs* ファイルに追加します。

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` は `SentimentData` を継承し、モデルによって生成された出力だけでなく `SentimentText` プロパティで元のデータへのアクセスを提供します。

## <a name="register-predictionenginepool-service"></a>PredictionEnginePool サービスを登録する

1 つの予測をするためには、[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を使用します。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) をお使いのアプリケーションで使用するには、必要に応じて、作成する必要があります。 その場合、ベスト プラクティスとして、依存関係を挿入することを検討します。

依存関係の注入の詳細については、[こちらのリンク](https://en.wikipedia.org/wiki/Dependency_injection)を参照してください。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを「*Startup.cs*」に変更します。 次に、 **[追加]** を選択します。 

    コード エディターに *Startup.cs* ファイルが開きます。 *Startup.cs* の先頭に次の using ステートメントを追加します。

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    using ステートメントの下にある既存のコードを削除し、*Startup.cs* ファイルに次のコードを追加します。

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

大まかに言えば、このコードは、オブジェクトとサービスがアプリケーションによって要求されたときに、初期化を手動ではなく自動的に実行します。

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。 パフォーマンスの向上とスレッドの安全性のために、`PredictionEnginePool` サービスを使用します。これにより、アプリケーションで使用される `PredictionEngine` オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。 

## <a name="register-startup-as-an-azure-functions-extension"></a>Azure Functions の拡張機能として Startup を登録する

`Startup` をお使いのアプリケーションで使用するには、Azure Functions の拡張機能として登録する必要があります。 まだ存在しない場合は、*extensions.json* という新しいファイルをお使いのプロジェクト内に作成します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。
1. **[新しい項目]** ダイアログで、 **[Visual C#]** ノード、 **[Web]** ノードの順に選択します。 次に、 **[Json ファイル]** オプションを選択します。 **[名前]** テキスト ボックスに「extensions.json」と入力し、 **[OK]** ボタンを選択します。

    コード エディターに *extensions.json* ファイルが開きます。 次の内容を *extensions.json* に追加します。
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. ソリューション エクスプローラーで、*extensions.json* ファイルを右クリックし、 **[プロパティ]** を選択します。 **[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

## <a name="load-the-model-into-the-function"></a>関数にモデルを読み込む

次のコードを *AnalyzeSentiment* クラス内に挿入します。

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

このコードでは、依存関係の挿入を通して取得する関数のコンストラクターに渡すことで、`PredictionEnginePool` を割り当てます。

## <a name="use-the-model-to-make-predictions"></a>モデルを使用して予測を行う

*AnalyzeSentiment* クラスの *Run* メソッドの既存の実装を、次のコードに置き換えます。

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

`Run` メソッドが実行されると、HTTP 要求からの受信データが逆シリアル化されて、`PredictionEnginePool` への入力として使用されます。 その後、予測を生成してその結果をユーザーに返すために、`Predict` メソッドが呼び出されます。 

## <a name="test-locally"></a>ローカルでテストする

すべてが設定されたので、アプリケーションをテストします。

1. アプリケーションの実行
1. PowerShell を開き、プロンプトにコードを入力します。PORT は、アプリケーションが実行されているポートです。 通常、このポートは 7071 です。

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    成功した場合、出力は次のテキストのようになります。
    
    ```powershell
    Negative
    ```

おめでとうございます! Azure 関数を使用したインターネット経由での予測の実行に対して、モデルを正常に提供できました。

## <a name="next-steps"></a>次の手順

- [Azure に配置する](/azure/azure-functions/functions-develop-vs#publish-to-azure)

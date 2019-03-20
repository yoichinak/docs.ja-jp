---
title: Azure Functions に ML.NET モデルをデプロイする
description: Azure Functions を使用して、インターネット経由で予測用の ML.NET 感情分析機械学習モデルを提供します
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: db29e37660665b02ab93a07b37418f0c4c20a608
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788642"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a>方法:Azure Functions で ML.NET モデルを使用する

このハウツー記事では、Azure Functions などのサーバーレス環境で、構築済みの ML.NET 機械学習モデルをインターネット経由で使用して個々の予測を行う方法を示します。

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" ワークロードおよび "Azure 開発" とともにインストールされていること。 
- [Azure Functions ツール](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- 事前トレーニング済みモデル 
    - [ML.NET 感情分析のチュートリアル](../tutorials/sentiment-analysis.md)を使用して、独自のモデルを構築する。
    - この[事前トレーニング済みの感情分析機械学習モデル](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)をダウンロードする。

## <a name="create-azure-functions-project"></a>Azure Functions プロジェクトを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[クラウド]** ノードを選択します。 次に、**Azure Functions** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「SentimentAnalysisFunctionsApp」と入力し、**[OK]** を選択します。
1. **[新しいプロジェクト]** ダイアログで、プロジェクト オプションの上のドロップダウンを開き、**[Azure Functions v2 (.NET Core)]** を選択します。 次に、**[Http トリガー]** プロジェクトを選択し、**[OK]** ボタンを選択します。
1. モデルを保存するための *MLModels* という名前のディレクトリをプロジェクト内に作成します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「MLModels」と入力し、Enter キーを押します。

1. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

## <a name="add-pre-built-model-to-project"></a>構築済みのモデルをプロジェクトに追加する

1. 構築済みのモデルを *MLModels* フォルダーにコピーします。
1. ソリューション エクスプローラーで、構築済みのモデルのファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

## <a name="create-function-to-analyze-sentiment"></a>センチメントを分析する関数を作成する

センチメントを予測するクラスを作成します。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、**[Azure 関数]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。 次に、**[追加]** を選択します。

1. **[新しい Azure 関数]** ダイアログ ボックスで、**[Http トリガー]** を選択します。 次に、**[OK]** ボタンを選択します。

    コード エディターに *AnalyzeSentiment.cs* ファイルが開きます。 *GitHubIssueData.cs* の先頭に次の `using` ステートメントを追加します。

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
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a>データ モデルを作成する

入力データと予測のために、いくつかのクラスを作成する必要があります。 プロジェクトに新しいクラスを追加します。

1. データ モデルを保存するための *DataModels* という名前のディレクトリをプロジェクト内に作成します。ソリューション エクスプローラーで、プロジェクトを右クリックし、**[追加]、[新しいフォルダー]** の順に選択します。 「DataModels」と入力し、Enter キーを押します。
2. ソリューション エクスプローラーで、*DataModels* ディレクトリを右クリックし、**[追加]、[新しいアイテム]** の順に選択します。
3. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。 次に、**[追加]** を選択します。 コード エディターで *SentimentData.cs* ファイルが開きます。 *SentimentData.cs* の先頭に次の using ステートメントを追加します。

```csharp
using Microsoft.ML.Data;
```

既存のクラス定義を削除し、次のコードを SentimentData.cs ファイルに追加します。

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. ソリューション エクスプローラーで、*DataModels* ディレクトリを右クリックし、**[追加]、[新しいアイテム]** の順に選択します。
5. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentPrediction.cs* に変更します。 次に、**[追加]** を選択します。 コード エディターに *SentimentPrediction.cs* ファイルが開きます。 *SentimentPrediction.cs* の先頭に次の using ステートメントを追加します。

```csharp
using Microsoft.ML.Data;
```

既存のクラス定義を削除し、次のコードを *SentimentPrediction.cs* ファイルに追加します。

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a>予測ロジックを追加する

*AnalyzeSentiment* クラスの *Run* メソッドの既存の実装を、次のコードに置き換えます。

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a>ローカルでテストする

すべてが設定されたので、アプリケーションをテストします。

1. アプリケーションの実行
1. PowerShell を開き、プロンプトにコードを入力します。PORT は、アプリケーションが実行されているポートです。 通常、このポートは 7071 です。 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

成功した場合、出力は次のテキストのようになります。

```powershell
Toxic
```

おつかれさまでした。 Azure 関数を使用したインターネット経由での予測の実行に対して、モデルを正常に提供できました。

## <a name="next-steps"></a>次の手順

- [Azure に配置する](/azure/azure-functions/functions-develop-vs#publish-to-azure)
---
title: ASP.NET Core Web API で機械学習モデルを提供する
description: ASP.NET Core Web API を使用して、インターネット経由で予測用の ML.NET 感情分析機械学習モデルを提供します
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: af51ccaac263202fc34d36e746722d2da46404f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321233"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>方法: ASP.NET Core Web API を通して機械学習モデルを提供する

このハウツー記事では、構築済みの ML.NET 機械学習モデルを ASP.NET Core Web API を使用して Web に提供する方法を示します。 これを行うことで、ユーザーが標準の HTTP メソッドを使用して、予測目的の API にアクセスすることできます。

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。
- PowerShell
- 事前トレーニング済みモデル
    - [ML.NET 感情分析のチュートリアル](../tutorials/sentiment-analysis.md)を使用して、独自のモデルを構築する。
    - この[事前トレーニング済みの感情分析機械学習モデル](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)をダウンロードする。

## <a name="create-aspnet-core-web-api-project"></a>ASP.NET Core Web API プロジェクトを作成する

1. Visual Studio 2017 を開きます。 メニュー バーから、**[ファイル]、[新規]、[プロジェクト]** の順に選択します。 [新しいプロジェクト] ダイアログで、**[Visual C#]** ノードを選択し、**[Web]** ノードを選択します。 次に、**[ASP.NET Core Web アプリケーション]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「SentimentAnalysisWebAPI」と入力し、**[OK]** を選択します。
1. ASP.NET Core プロジェクトの複数の種類が表示されているウィンドウで、**[API]** を選択し、**[OK]** を選択します。
1. 構築済みの機械学習モデルを保存するための *MLModels* という名前のディレクトリをプロジェクト内に作成します。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、[追加]、[新しいフォルダー] の順に選択します。 「MLModels」と入力し、Enter キーを押します。

1. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として [nuget.org] を選択します。[参照] タブを選択し、「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、[インストール] を選択します。 **[変更のプレビュー]** ダイアログで **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、[ライセンスの同意] ダイアログの **[同意する]** を選択します。

### <a name="add-model-to-aspnet-core-web-api-project"></a>モデルを ASP.NET Core Web API プロジェクトに追加する

1. 構築済みのモデルを *MLModels* ディレクトリにコピーします。
1. ソリューション エクスプローラーで、モデルの zip ファイルを右クリックし、[プロパティ] を選択します。 [詳細設定] で、[出力ディレクトリにコピー] の値を [新しい場合はコピーする] に変更します。

## <a name="build-data-models"></a>データ モデルを構築する

入力データと予測のために、いくつかのクラスを作成する必要があります。 プロジェクトに新しいクラスを追加します。

1. データ モデルを保存するための *DataModels* という名前のディレクトリをプロジェクト内に作成します。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、[追加]、[新しいフォルダー] の順に選択します。 「DataModels」と入力し、**Enter** キーを押します。

2. ソリューション エクスプローラーで、*DataModels* ディレクトリを右クリックし、[追加]、[新しいアイテム] の順に選択します。
3. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。 次に、**[追加]** を選択します。 コード エディターで *SentimentData.cs* ファイルが開きます。 *SentimentData.cs* の先頭に次の using ステートメントを追加します。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

既存のクラス定義を削除し、次のコードを **SentimentData.cs** ファイルに追加します。

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
5. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentPrediction.cs* に変更します。 次に、[追加] を選択します。 コード エディターに *SentimentPrediction.cs* ファイルが開きます。 *SentimentPrediction.cs* の先頭に次の using ステートメントを追加します。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
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

## <a name="register-predictionengine-for-use-in-application"></a>アプリケーションで使用するための PredictionEngine を登録する

1 つの予測をするためには、`PredictionEngine` を使用できます。 アプリケーションで `PredictionEngine` を使用するには、必要になるたびにそれを作成する必要があります。 この場合のベスト プラクティスは、ASP.NET Core の依存関係の挿入を考慮することです。

依存関係の注入の詳細については、[こちらのリンク](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)を参照してください。

1. *Startup.cs* を開き、ファイルの先頭に次の using ステートメントを追加します。

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

2. *ConfigureServices* メソッドに次のコード行を追加します。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
}
```

> [!WARNING]
> `PredictionEngine` はスレッド セーフではありません。 そのサービスの有効期間を*スコープ化*することで、オブジェクト作成のコストを制限することができます。 "*スコープ*" オブジェクトは、要求内では同じですが、要求間では異なります。 [サービスの有効期間](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes)の詳細については、次のリンクを参照してください。

大まかに言えば、このコードは、オブジェクトとサービスがアプリケーションによって要求されたときに、初期化を手動ではなく自動的に実行します。

## <a name="create-predict-controller"></a>予測コントローラーを作成する

受信 HTTP 要求を処理するために、コントローラーを作成する必要があります。

1. ソリューション エクスプローラーで、*Controllers* ディレクトリを右クリックし、**[追加]、[コントローラー]** の順に選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、**[空の API コントローラー]** を選択し、**[追加]** を選択します。
1. プロンプトで、**[コントローラー名]** フィールドを*PredictController.cs* に変更します。 次に、[追加] を選択します。 コード エディターに *PredictController.cs* ファイルが開きます。 *PredictController.cs* の先頭に次の using ステートメントを追加します。

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

既存のクラス定義を削除し、次のコードを *PredictController.cs* ファイルに追加します。

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

これは、依存関係の挿入をとおして取得するコントローラーのコンストラクターに渡すことによる `PredictionEngine` の割り当てです。 これで、このコントローラーの POST メソッドの中で `PredictionEngine` を使用して予測が行われ、成功した場合はその結果がユーザーに返されます。

## <a name="test-web-api-locally"></a>Web API をローカルでテストする

すべてが設定されたので、アプリケーションをテストします。

1. アプリケーションを実行します。
1. PowerShell を開き、次のコードを入力します。PORT は、アプリケーションがリスニングしているポートです。

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

成功した場合、出力は次のテキストのようになります。

```powershell
Toxic
```

おめでとうございます!  ASP.NET Core API を使用したインターネット経由での予測の実行に対して、モデルを正常に提供できました。

## <a name="next-steps"></a>次の手順

- [Azure に配置する](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
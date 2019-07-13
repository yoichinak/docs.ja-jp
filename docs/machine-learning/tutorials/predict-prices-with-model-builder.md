---
title: モデル ビルダーで回帰を使用して価格を予測する
description: このチュートリアルでは、ML.NET モデル ビルダーを使用して、価格 (具体的にはニューヨーク市のタクシー運賃) を予測する回帰モデルを構築する方法を示します。
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539631"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>モデル ビルダーで回帰を使用して価格を予測する

ML.NET モデル ビルダーを使用して、価格を予測する[回帰モデル](../resources/glossary.md#regression)を構築する方法について説明します。  このチュートリアルで開発する .NET コンソール アプリでは、過去のニューヨーク市のタクシー運賃データに基づいてタクシー運賃を予測します。

モデル ビルダーの価格予測テンプレートは、数値による予測値を必要とするすべてのシナリオで使用できます。 シナリオの例には、住宅価格の予測、需要予測、売上予測などがあります。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * データを準備して理解する
> * シナリオを選択する
> * データを読み込む
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

> [!NOTE]
> モデル ビルダーは現在のところ、プレビュー段階です。

## <a name="pre-requisites"></a>前提条件

前提条件の一覧とインストール手順は、[モデル ビルダーのインストール ガイド](../how-to-guides/install-model-builder.md)を参照してください。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. "TaxiFarePrediction" という名前の **.NET Core コンソール アプリケーション**を作成します。

1. **Microsoft.ML** NuGet パッケージをインストールします。

    **ソリューション エクスプローラー**で、 *[TaxiFarePrediction]* プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として [nuget.org] を選択します。 **[参照]** タブを選択し、「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、 **[インストール]** ボタンを選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

## <a name="prepare-and-understand-the-data"></a>データを準備して理解する

1. プロジェクトに *Data* という名前のディレクトリを作成して、データ セットのファイルを保存します。

1. [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) データ セットをダウンロードし、前の手順で作成した *Data* フォルダーに保存します。 このデータ セットは、機械学習モデルのトレーニングと評価に使用されます。 このデータ セットは、[NYC TLC Taxi Trip データ セット](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)から取得したものです。

1. **ソリューション エクスプローラー**で、 *[taxi-fare-train.csv]* ファイルを右クリックし、 **[プロパティ]** を選択します。 **[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

`taxi-fare-train.csv` データ セットの各行に、タクシーの移動の詳細が含まれています。

1. **taxi-fare-train.csv** データ セットを開きます

    提供されているデータ セットには、次の列が含まれます。

    * **vendor_id:** タクシー会社の ID は特徴です。
    * **rate_code:** タクシー旅行のレートの種類は特徴です。
    * **passenger_count:** 旅行の乗客数は特徴です。
    * **trip_time_in_secs:** 旅行の所要時間です。 旅行が終わる前に、旅行の運賃を予測したいと考えます。 その時点では、旅行の所要時間はわかりません。 したがって、旅行の所要時間は特徴ではなく、この列はモデルから除外します。
    * **trip_distance:** 旅行距離は特徴です。
    * **payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。
    * **fare_amount:** 支払った合計タクシー運賃はラベルです。

`label` は予測する列です。 回帰タスクを実行する場合の目標は、数値を予測することです。 この価格予測シナリオでは、タクシーの乗車のコストが予測されています。 したがって、**fare_amount** がラベルです。 識別された `features` は、`label` を予測するためにモデルを指定する入力です。 この場合、残りの列は、運賃の金額を予測するための機能または入力として使用されます。

## <a name="choose-a-scenario"></a>シナリオを選択する

モデルをトレーニングするには、モデル ビルダーによって提供される機械学習シナリオの一覧から選択する必要があります。 この場合、シナリオは `Price Prediction` です。 より広範な一覧については、[モデル ビルダーの概要記事](../automate-training-with-model-builder.md#scenarios)を参照してください。

1. **ソリューション エクスプローラー**で、 *[TaxiFarePrediction]* プロジェクトを右クリックし、 **[追加]**  >  **[機械学習]** を選択します。
1. モデル ビルダー ツールのシナリオの手順で、*価格の予測*のシナリオを選択します。

## <a name="load-the-data"></a>データを読み込む

モデル ビルダーは、SQL Server データベースまたはローカル ファイル (csv または tsv ファイル) という 2 つのソースからデータを受け入れます。 データ形式の要件の詳細については、次の[リンク](../how-to-guides/install-model-builder.md#limitations)を参照してください。

1. モデル ビルダー ツールのデータの手順で、データ ソースのドロップダウンから *[ファイル]* を選択します。
1. *[ファイルの選択]* テキスト ボックスの横にあるボタンを選択し、ファイル エクスプローラーを使用して *Data* ディレクトリにある *[taxi-fare-test.csv]* を参照し、選択します
1. *[Label or Column to Predict]\(予測するラベルまたは列\)* ドロップダウンにある *[fare_amount]* を選択して、モデル ビルダー ツールのトレーニングの手順に移動します。

## <a name="train-the-model"></a>モデルをトレーニングする

このチュートリアルで、価格予測モデルのトレーニングに使用する機械学習のタスクは、回帰です。 モデルのトレーニング プロセス中、モデル ビルダーは、さまざまな回帰アルゴリズムと設定を使用して、データセットで最も良いパフォーマンスのモデルを見つける個別のモデルをトレーニングします。

モデルのトレーニングに必要な時間は、データの量に比例します。 このグラフをガイダンスとして使用して、`Time to train (seconds)` フィールドに適した値を選択してください。

*データセットのサイズ  | データセットの種類       | Avg.トレーニング時間*
------------- | ------------------ | --------------
0 - 10 Mb     | 数値とテキスト   | 10 秒
10 - 100 Mb   | 数値とテキスト   | 10 分
100 - 500 Mb  | 数値とテキスト   | 30 分
500 - 1 Gb    | 数値とテキスト   | 60 分
1 Gb 超         | 数値とテキスト   | 3 時間超

1. トレーニング データ ファイルが 10 MB を超えているため、 *[Time to train (seconds)]\(トレーニング時間 (秒)\)* の値には 600 秒 (10 分) を使用してください。
2. *[Start Training]\(トレーニング開始\)* を選択します。

トレーニング プロセスを通して、進捗データがトレーニングの手順の `Progress` セクションに表示されます。

- 状態には、トレーニング プロセスの完了ステータスが表示されます。
- [Best accuracy]\(最良の精度\) には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのモデルの精度が表示されます。 精度が高くなるほど、テスト データでモデルが正確に予測されたことになります。
- [Best algorithm]\(最良のアルゴリズム\) には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのアルゴリズムの名前が表示されます。
- [Last algorithm]\(最後のアルゴリズム\) には、モデル ビルダーがモデルのトレーニングに最近使用したアルゴリズムの名前が表示されます。

トレーニングが完了したら、評価の手順に移動します。

## <a name="evaluate-the-model"></a>モデルを評価する

トレーニングの手順の結果が、最良のパフォーマンスだった 1 つのモデルになります。 モデル ビルダー ツールの評価の手順の出力セクションには、 *[Best Model]\(最良のモデル\)* エントリの最良のパフォーマンスのモデルで使用されたアルゴリズムと、 *[Best Model Quality (RSquared)]\(最良のモデル品質 (RSquared)\)* のメトリックが含まれます。 また、概要テーブルには上位 5 つのモデルとそのメトリックが含まれています。 モデル評価メトリックの詳細については、[次のリンク](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics)を参照してください。

精度のメトリックに不満がある場合、モデルのトレーニング時間を増やすか、さらに多くのデータを使用すると、モデルの精度を簡単に高めることができます。

## <a name="use-the-model-for-predictions"></a>モデルを使用して予測を行う

トレーニング プロセスの結果として 2 つのプロジェクトが作成されます。

- TaxiFarePredictionML.ConsoleApp: モデルのトレーニングと消費コードが含まれる .NET コンソール アプリケーション。
- TaxiFarePredictionML.Model: 入出力モデル データのスキーマを定義するデータ モデルと、トレーニング中にパフォーマンスが最も良かったモデルの永続化バージョンが含まれる .NET Standard クラス ライブラリ。

1. モデル ビルダー ツールのコード セクションで **[Added Projects]\(追加されたプロジェクト\)** を選択して、プロジェクトをソリューションに追加します。
2. ソリューション エクスプローラーで、 *[TaxiFarePrediction]* プロジェクトを右クリックします。 次に、 **[追加]、[既存の項目]** の順に選択します。 [ファイルの種類] のドロップダウンで `All Files` を選択し、 *[TaxiFarePredictionML.Model]* のプロジェクト ディレクトリに移動して、`MLModel.zip` ファイルを選択します。 最近追加した `MLModel.zip` ファイルを右クリックし、 *[プロパティ]* を選択します。 [出力ディレクトリにコピー] オプションで、 *[新しい場合はコピーする]* をドロップダウンから選択します。
3. *[TaxiFarePrediction]* プロジェクトを右クリックします。 それから、 **[追加]、[参照]** の順に選択します。 **[プロジェクト]、[ソリューション]** ノードを選択し、一覧で *[TaxiFarePredictionML.Model]* プロジェクトを選択して [OK] を選択します。

4. *[TaxiFarePrediction]* プロジェクトの *[Program.cs]* ファイルを開きます。
5. 次の using ステートメントを追加します。

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. `ConsumeModel` メソッドを `Program` クラスに追加します。 `ConsumeModel` で、モデル ビルダーによって生成されたモデルに基づいて新しいデータの予測を行い、コンソールに出力する `PredictionEngine` が作成されます。

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. `Main` メソッドに次のコードを追加して、アプリケーションを実行します。

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    プログラムによって生成される出力は次のスニペットのようになります。

    ```bash
    Predicted Fare: 16.82245
    ```

別のソリューション内で後で生成されたプロジェクトを参照する必要がある場合は、`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` ディレクトリを検索することができます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * データを準備して理解する
> * シナリオを選択する
> * データを読み込む
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

モデルをデプロイする方法を学習するには、次の How-To 記事のいずれかに進んでください。

> [!div class="nextstepaction"]
> [Azure Functions にモデルをデプロイする](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [Web API にモデルをデプロイする](../how-to-guides/serve-model-web-api-ml-net.md)

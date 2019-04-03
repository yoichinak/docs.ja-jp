---
title: 回帰ラーナーと ML.NET を使用して料金を予測する
description: 回帰ラーナーと ML.NET を使用して料金を予測します。
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 0a027b3b4930f7dda48d884faf0484cf33856c8d
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307981"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a>チュートリアル: 回帰ラーナーと ML.NET を使用して料金を予測する

このチュートリアルでは、ML.NET を使用して、料金 (具体的にはニューヨーク市のタクシー運賃) を予測する[回帰モデル](../resources/glossary.md#regression)を構築する方法を示します。

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳しくは、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページをご覧ください。

このチュートリアルと関連サンプルでは、現時点では **ML.NET バージョン 0.11** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習タスクを選択する
> * データを準備して理解する
> * 学習パイプラインを作成する
> * データを読み込んで変換する
> * 学習アルゴリズムを選択する
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。

## <a name="understand-the-problem"></a>問題を把握する

この問題の中心となるのは、ニューヨーク市のタクシー旅行の運賃の予測です。 一見すると、単に乗車距離に依存すると思われるかもしれません。 しかし、ニューヨークのタクシー会社は追加の乗客数や現金でなくクレジット カードによる支払いなど、その他の要因によって請求額を変えます。

## <a name="select-the-appropriate-machine-learning-task"></a>適切な機械学習タスクを選択する

データ セットの他の要因に基づき、実際の値である、価格値を予測します。 それを行うには、[回帰](../resources/glossary.md#regression)機械学習タスクを選択します。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「TaxiFarePrediction」と入力し、**[OK]** を選択します。

1. プロジェクトに *Data* という名前のディレクトリを作成して、データ セットとモデルのファイルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

1. **Microsoft.ML** NuGet パッケージをインストールします。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、**[参照]** タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

## <a name="prepare-and-understand-the-data"></a>データを準備して理解する

1. [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) データ セットと [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) データ セットをダウンロードして、前の手順で作成済みの *Data* フォルダーに保存します。 これらのデータ セットを使用して、機械学習モデルをトレーニングし、モデルの正確度を評価します。 これらのデータ セットは、[NYC TLC Taxi Trip データ セット](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)から取得したものです。

1. **ソリューション エクスプローラー**で、各 \*.csv ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

1. **taxi-fare-train.csv** データ セットを開き、最初の行の列ヘッダーを確認します。 各列を確認してください。 データについて把握し、どの列が**特徴**で、どの列が**ラベル**であるかを確認します。

**ラベル**は、予測する列の識別子です。 識別された**特徴**は、ラベルを予測するために使用します。

提供されているデータ セットには、次の列が含まれます。

* **vendor_id:** タクシー会社の ID は特徴です。
* **rate_code:** タクシー旅行のレートの種類は特徴です。
* **passenger_count:** 旅行の乗客数は特徴です。
* **trip_time_in_secs:** 旅行の所要時間です。 旅行が終わる前に、旅行の運賃を予測したいと考えます。 その時点では、旅行の所要時間はわかりません。 したがって、旅行の所要時間は特徴ではなく、この列はモデルから除外します。
* **trip_distance:** 旅行距離は特徴です。
* **payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。
* **fare_amount:** 支払った合計タクシー運賃はラベルです。

## <a name="create-data-classes"></a>データ クラスを作成する

入力データと予測のためのクラスを作成します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TaxiTrip.cs* に変更します。 次に、**[追加]** を選択します。
1. 以下の `using` ディレクティブを新しいファイルに追加します。

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

既存のクラス定義を削除し、2 つのクラス `TaxiTrip` と `TaxiTripFarePrediction` を含む次のコードを *TaxiTrip.cs* ファイルに追加します。

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` は入力データ クラスであり、各データ セット列の定義が含まれています。 <xref:Microsoft.ML.Data.LoadColumnAttribute> 属性を使用して、データ セット内のソース列のインデックスを指定します。

`TaxiTripFarePrediction` クラスは予測結果を表します。 このクラスには、`Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 属性が適用された 1 つの浮動小数点型フィールド `FareAmount` が含まれています。 回帰タスクの場合、**Score** 列には、予測ラベル値が含まれます。

> [!NOTE]
> 入力データと予測データのクラス内の浮動小数点値を表すには、`float` 型を使います。

## <a name="define-data-and-model-paths"></a>データおよびモデルのパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

データ セットを含むファイルのパスとモデルを保存するファイルのパスを保持するための 3 つのフィールドを追加する必要があります。

* `_trainDataPath` には、モデルのトレーニングに使用するデータ セットがあるファイルへのパスが含まれます。
* `_testDataPath` には、モデルの評価に使用するデータ セットがあるファイルへのパスが含まれます。
* `_modelPath` には、トレーニング済みモデルが格納されるファイルへのパスが含まれます。

`Main` メソッドのすぐ上に次のコードを追加して、それらのパスと `_textLoader` 変数を指定します。

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

ML.NET を使用してモデルをビルドするときは、まず ML Context を作成します。 これは、概念的には Entity Framework での `DbContext` の使用に相当します。 環境によって、例外の追跡とログ記録に使用できる機械学習ジョブのコンテキストが提供されます。

### <a name="initialize-variables-in-main"></a>Main で変数を初期化する

`mlContext` という変数を作成し、`MLContext` の新しいインスタンスで初期化します。  `Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

`Main` メソッドに次のコード行を追加して、`Train` メソッドを呼び出します。

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train` メソッドは次のタスクを実行します。

* データを読み込みます。
* データを抽出して変換します。
* モデルをトレーニングする。
* モデルを .zip ファイルとして保存します。
* モデルを返します。

`Train` メソッドは、モデルをトレーニングします。 次のコードを使用して、`Main` の直下にそのメソッドを作成します。

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

`Train` メソッドに 2 つのパラメーターを渡します。つまり、コンテキスト (`mlContext`) には`MLContext`、データセット パス (`dataPath`) には文字列です。 このメソッドをデータセットの読み込みに再利用します。

## <a name="load-and-transform-data"></a>データを読み込んで変換する

[LoadFromTextFile メソッド](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) の `MLContext.Data.LoadFromTextFile` ラッパーを使用して、データを読み込みます。 <xref:Microsoft.Data.DataView.IDataView> が返されます。 

`Transforms` の入力および出力として、`DataView` は基本的なデータ パイプラインの種類であり、`LINQ` の `IEnumerable` と同等です。

ML.NET ではデータは SQL ビューに似ています。 つまり、遅延評価、体系的、異種です。 オブジェクトはパイプラインの最初の部分であり、データを読み込みます。 このチュートリアルでは、タクシーの運賃情報を含むデータセットを読み込みます。 これを使用して、モデルを作成してトレーニングします。

`Train` メソッドの最初の行として、次のコードを追加します。

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

次の手順では、`TaxiTrip` クラス内で定義された名前によって列を参照します。

モデルのトレーニングと評価が行われるとき、既定では、**Label** 列内の値が予測される適切な値と見なされます。 タクシー旅行の運賃を予測したいので、`FareAmount` 列を **Label** 列にコピーします。 これを行うには、`CopyColumnsEstimator` 変換クラスを使用して、次のコードを追加します。

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

モデルをトレーニングするアルゴリズムには、**数値**の特徴が必要であるため、カテゴリ データ (`VendorId`、`RateCode`、および `PaymentType`) の値を数値 (`VendorIdEncoded`、`RateCodeEncoded`、および`PaymentTypeEncoded`) に変換する必要があります。 これを行うには、異なる数値キーの値を各列内の異なる値に割り当てる Microsoft.ML.Transforms.OneHotEncodingTransformer> 変換クラスを使用する次のコードを追加します。

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

データの準備の最後の手順では、`mlContext.Transforms.Concatenate` 変換クラスを使用して、すべての特徴列を **Features** 列に結合します。 既定では、学習アルゴリズムは **Features** 列の特徴のみを処理します。 次のコードを追加します。

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

データをパイプラインに追加して正しい入力形式に変換したら、学習アルゴリズム (**ラーナー**) を選択します。 ラーナーはモデルをトレーニングします。 この問題に対しては**回帰タスク**を選択するので、`FastTreeRegressionTrainer` ラーナー (ML.NET によって提供される回帰ラーナーの 1 つ) を使用します。

`FastTreeRegressionTrainer`トレーニング アルゴリズムでは、勾配ブースティングを使用します。 勾配ブースティングは、回帰問題に対応する機械学習の手法です。 この手法では、それぞれの回帰ツリーを段階的に構築します。 また、定義済みの損失関数を使用して、各ステップの誤差を測定し、次の段階で修正します。 結果は予測モデルですが、実際は弱い予測モデルの集合です。 勾配ブースティングについて詳しくは、「[Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression)」(ブーストされたデシジョン ツリー回帰) を参照してください。

`Train` メソッドに次のコードを追加して、前の手順で追加したデータ処理コードに `FastTreeRegressionTrainer` を追加します。

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>モデルをトレーニングする

最後の手順は、モデルのトレーニングです。 読み込まれて変換されたデータ セットに基づいて、モデル <xref:Microsoft.ML.Data.TransformerChain> をトレーニングします。 見積もり機能が定義されたら、既に読み込まれたトレーニング データを提供しながら、<xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> を使用してモデルをトレーニングします。 これにより、予測で使用されるモデルが返されます。 `pipeline.Fit()` でパイプラインをトレーニングし、`DataView` に基づいて `Transformer` を返します。 これが行われるまで、実験は実行されません。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a>モデルを保存する

この時点で、既存または新規のどの .NET アプリケーションにも統合できる、型が <xref:Microsoft.ML.Data.TransformerChain> のモデルができました。 モデルを .zip ファイルに保存するには、`Train` メソッドの終わりに次のコードを追加します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>モデルを .zip ファイルとして保存する

`Train` メソッドの直後に、次のコードを使用して `SaveModelAsFile` メソッドを作成します。

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` メソッドは次のタスクを実行します。

* モデルを .zip ファイルとして保存します。

他のアプリケーションで再利用し、使用できるように、モデルを保存するメソッドを作成する必要があります。 `ITransformer` には <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> メソッドがあり、`_modelPath` グローバル フィールドと <xref:System.IO.Stream> を受け取ります。 これを zip ファイルとして保存するために、`FileStream` を作成した直後に `SaveTo` メソッドを呼び出します。 `SaveModelAsFile` メソッドに次のコード行を追加します。

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

`_modelPath` を使用してコンソール メッセージを記述することで、ファイルが書き込まれた場所も表示できるようになります。これには次のコードを使用します。

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>モデルを評価する

評価は、モデルがラベル値を適切に予測するかどうかを確認するプロセスです。 モデルのトレーニング時に使用しなかったデータを適切に予測できるかどうかが重要になります。 そのための方法の 1 つとしては、このチュートリアルで行ったように、データをトレーニング用のデータ セットとテスト用のデータ セットに分けます。 トレーニング用データでのモデルのトレーニングは完了しているので、テスト用データでモデルが適切に機能するかどうかを確認できます。

`Evaluate` メソッドはモデルを評価します。 そのメソッドを作成するには、`Train` メソッドの下に次のコードを追加します。

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
`Evaluate` メソッドは次のタスクを実行します。

* テスト データ セットを読み込む。
* 回帰エバリュエーターを作成する。
* モデルを評価し、メトリックを作成する。
* メトリックを表示する。

`Train` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

`MLContext.Data.LoadFromTextFile` ラッパーを使用して、テスト データセットを読み込みます。 このデータ セットを品質チェックとして使用して、モデルを評価できます。 `Evaluate` メソッドに次のコードを追加します。

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

次に、機械学習 `model` パラメーター (変換器) を使用して特徴を入力し、予測を返します。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

`RegressionContext.Evaluate` メソッドは、指定されたデータセットを使用して `PredictionModel` の品質メトリックを計算します。 これによって返される <xref:Microsoft.ML.Data.RegressionMetrics> オブジェクトには、回帰エバリュエーターによって計算されるメトリック全体が含まれます。 これらを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

次のコードを追加してモデルを評価し、評価メトリックを生成します。

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) は回帰モデルのもう 1 つの評価メトリックです。 RSquared は 0 から 1 までの値を取ります。 値が 1 に近づくほど、優れたモデルになります。 次のコードを `Evaluate` メソッドに追加して、RSquared 値を表示します。

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) は回帰モデルの評価メトリックの 1 つです。 RMS が低いほど、優れたモデルになります。 `Evaluate` メソッドに次のコードを追加することで、RMS 値を表示します。

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>モデルを使用して予測を行う


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>モデルと 1 つのコメントを使用してテスト データの結果を予測する

`Evaluate` メソッドの直後に、次のコードを使用して `TestSinglePrediction` メソッドを作成します。

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

`TestSinglePrediction` メソッドは次のタスクを実行します。

* テスト データの 1 つのコメントを作成します。
* テスト データに基づいて運賃合計を予測します。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

保存した zip ファイルからモデルを読み込むために、`Load` メソッドを呼び出す直前に `FileStream` を作成します。 `TestSinglePrediction` メソッドに次のコード行を追加します。

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

`model` は多数のデータ行を操作する `transformer` ですが、よくある運用シナリオとして個々の例に対する予測のニーズがあります。 <xref:Microsoft.ML.PredictionEngine%602> は、`CreatePredictionEngine` メソッドから返されるラッパーです。 次の行を追加して、`PredictionEngine` を `TestSinglePrediction` メソッドの次の行として作成しましょう。

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
このチュートリアルでは、このクラス内の 1 つのテスト用の旅行を使用します。 モデルを試行するために後で他のシナリオを追加できます。 `TaxiTrip` のインスタンスを作成して、`TestSinglePrediction` メソッドでコストのトレーニング済みモデルの予測をテストするために、旅行を追加します。

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 これを使用して、タクシー運賃データの 1 つのインスタンスに基づいて料金を予測することができます。 予測を取得するには、データに対して <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> を使用します。 入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

指定された旅行の予測運賃を表示するために、次のコードを `TestSinglePrediction` メソッドに追加します。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

プログラムを実行し、テスト ケースに対して予測されたタクシー運賃を確認します。

おめでとうございます!  これで、タクシー旅行運賃を予測する機械学習モデルが正常に構築され、その正確度が評価され、このモデルを使用した予測が行われました。 このチュートリアルのソース コードは、[dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub リポジトリで確認できます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習タスクを選択する
> * データを準備して理解する
> * 学習パイプラインを作成する
> * データを読み込んで変換する
> * 学習アルゴリズムを選択する
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

さらに詳しく学習するには、次のチュートリアルに進んでください。
> [!div class="nextstepaction"]
> [アヤメのクラスタリング](iris-clustering.md)

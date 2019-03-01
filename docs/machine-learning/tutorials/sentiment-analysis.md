---
title: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する
description: バイナリ分類のシナリオで ML.NET を使用する方法を学習して、センチメント予測をどのように使用して適切なアクションを実行するかを理解します。
ms.date: 02/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 9afdf1d8369e71f9614ebc2bf327e98d31b988ff
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748389"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>チュートリアル: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

このサンプル チュートリアルでは、Visual Studio 2017 で ML.NET を使用して、C# を使用する .NET Core コンソール アプリケーションからセンチメント分類器を作成する方法を示 します。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習アルゴリズムを選択する
> * データを準備する
> * データを変換する
> * モデルをトレーニングする
> * モデルを評価する
> * トレーニング済みモデルを使用して予測する
> * 読み込み済みのモデルを使用して配置および予測する

## <a name="sentiment-analysis-sample-overview"></a>センチメント分析のサンプルの概要

このサンプルは ML.NET を使用するコンソール アプリケーションであり、センチメントを分類して肯定的か否定的かを予測するモデルをトレーニングします。 また、高品質な分析のために、2 番目のデータ セットを使用してモデルを評価します。 センチメントのデータ セットは、WikiDetox プロジェクトからのものです。

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。

* [Wikipedia detox line data タブ区切りファイル (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)。
* [Wikipedia detox line test タブ区切りファイル (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv)。

## <a name="machine-learning-workflow"></a>機械学習ワークフロー

このチュートリアルでは、プロセスを順序立てて進められるようにする機械学習ワークフローに従います。

このワークフローには次のフェーズがあります。

1. **問題を把握する**
2. **データを準備する**
   * **データを読み込む**
   * **特徴を抽出する (データを変換する)**
3. **ビルドしてトレーニングする** 
   * **モデルをトレーニングする**
   * **モデルを評価する**
4. **モデルの配置**
   * **モデルを使用して予測する**

### <a name="understand-the-problem"></a>問題を把握する

まず、問題を把握して、モデルのビルドおよびトレーニングに使用できるパーツに分ける必要があります。 問題を分けることで、結果の予測および評価ができるようになります。

このチュートリアルでの問題は、書き込まれた Web サイト コメントのセンチメントを解釈して適切なアクションを実行することです。

この問題は、モデルのトレーニングに使用するセンチメント テキストおよびセンチメント値と、評価して運用に使用することができる予測されたセンチメント値に分けることができます。

次に、センチメントを**決定**する必要があります。これは機械学習タスクを選択するときに役立ちます。

## <a name="select-the-appropriate-machine-learning-algorithm"></a>適切な機械学習アルゴリズムを選択する

この問題に関してわかっていることは次のとおりです。

トレーニング データである Web サイト コメントは、有害 (1) か無害 (0) (**センチメント**) のいずれかとなります。
次の例のような、新しい Web サイト コメントの**センチメント**が有害か無害かを予測します。

* Wikipedia に無意味な記述を追加するのはやめてください。
* 彼は最高です。記事ではそのことを記述するべきです。

このシナリオには、分類機械学習アルゴリズムが適しています。

### <a name="about-the-classification-task"></a>分類タスクについて

分類は、データを使用して項目またはデータ行のカテゴリ、型、クラスを**判断**する機械学習アルゴリズムです。 分類はたとえば、次のような目的に使用できます。

* センチメントが肯定的か否定的かを判断する。
* 電子メールをスパム、迷惑メール、正常なメールに分類する。
* 患者の検体が癌性かどうかを判断する。
* 顧客を販売キャンペーンへの反応性で分類する。

多くの場合、分類アルゴリズムは次のいずれかの種類です。

* バイナリ: A か B のいずれかである。
* 多クラス: 1 つのモデルを使用して予測できるカテゴリが多数ある。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「SentimentAnalysis」と入力し、**[OK]** を選択します。

2. プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

3. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

### <a name="prepare-your-data"></a>データを準備する

1. [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) データ セットと [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) データ セットをダウンロードして、作成済みの *Data* フォルダーに保存します。 1 番目のデータ セットでは機械学習モデルをトレーニングし、2 番目のデータ セットはモデルの精度を評価するために使用します。

2. ソリューション エクスプローラーで、各 \*.tsv ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

最近ダウンロードしたファイルのパスを保存する 3 つのグローバル フィールドと、`TextLoader` のためのグローバル変数を作成する必要があります。

* `_trainDataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。
* `_testDataPath` には、モデルの評価に使用するデータ セットのパスが含まれます。
* `_modelPath` には、トレーニング済みのモデルを保存するパスが含まれます。
* `_textLoader` は、データセットの読み込みと変換に使用される <xref:Microsoft.ML.Data.TextLoader> です。

`Main` メソッドのすぐ上にある行に次のコードを追加して、それらのパスと `_textLoader` 変数を指定します。

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

入力データと予測のために、いくつかのクラスを作成する必要があります。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。 次に、**[追加]** を選択します。

    コード エディターで *SentimentData.cs* ファイルが開きます。 *SentimentData.cs* の先頭に次の `using` ステートメントを 追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

既存のクラス定義を削除し、`SentimentData` と `SentimentPrediction` の 2 つのクラスを含む次のコードを *SentimentData.cs* ファイルに追加します。

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` は入力データ セット クラスで、肯定的か否定的のいずれかのセンチメント値を持つ `float` (`Sentiment`) と、コメントの文字列 (`SentimentText`) を含みます。 どちらのフィールドにも `Column` 属性が添付されています。 この属性はデータ ファイル内での各フィールドの順序と、どちらが `Label` フィールドであるかを示しています。 `SentimentPrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。 これは、1 つのブール値 (`Sentiment`) と、`PredictedLabel` `ColumnName` 属性を持ちます。 `Label` はモデルを作成してトレーニングするために使用され、2 番目のデータ セットでもモデルを評価するために使用されます。 `PredictedLabel` は予測と評価の際に使用されます。 評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。

ML.NET を使用してモデルをビルドするときは、まず `MLContext` を作成します。 これは、概念的には Entity Framework での `DbContext` の使用に相当します。 環境によって、例外の追跡とログ記録に使用できる ML ジョブのコンテキストが提供されます。

### <a name="initialize-variables-in-main"></a>Main で変数を初期化する

`mlContext` という変数を作成し、`MLContext` の新しいインスタンスで初期化します。  `Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

次に、データ読み込みを設定するために、再利用できるように `_textLoader` グローバル変数を初期化します。  `MLContext.Data.CreateTextLoader` を使用して `TextLoader` を作成するとき、必要なコンテキストと、カスタマイズを可能にする <xref:Microsoft.ML.Data.TextLoader.Arguments> クラスを渡します。

 すべての列名とそれらの型を含む <xref:Microsoft.ML.Data.TextLoader.Column> オブジェクトの配列をローダーに渡して、データ スキーマを指定します。 データ スキーマは、`SentimentData` クラスを作成したときに既に定義しています。 このスキーマでは、最初の列 (Label) は <xref:System.Boolean> (予測) で、2 番目の列 (SentimentText) はセンチメントの予測に使用される text/string 型の特徴です。
`TextLoader` クラスは、完全に初期化された <xref:Microsoft.ML.Data.TextLoader> を返します。  

必要なデータセットで再利用するために `_textLoader` グローバル変数を初期化するには、`mlContext` 初期化の後に次のコードを追加します。

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

`Main` メソッドに次のコード行を追加します。

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

`Train` メソッドは次のタスクを実行します。

* データを読み込みます。
* データを抽出して変換します。
* モデルをトレーニングする。
* テスト データに基づいてセンチメントを予測する。
* モデルを返します。

`Main` メソッドの直後に、次のコードを使用して `Train` メソッドを作成します。

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Train メソッドに 2 つのパラメーターが渡されていることに注意してください。`MLContext` はコンテキスト (`mlContext`)、<xref:System.String> はデータセットのパス (`dataPath`) に関するものです。 トレーニングとテストのためにこのメソッドは複数回使用します。

## <a name="load-the-data"></a>データを読み込む

`_textLoader` グローバル変数と `dataPath` パラメーターを使用してデータを読み込みます。 <xref:Microsoft.Data.DataView.IDataView> が返されます。 `Transforms` の入力および出力として、`DataView` は基本的なデータ パイプラインの種類であり、`LINQ` の `IEnumerable` と同等です。

ML.NET ではデータは SQL ビューに似ています。 つまり、遅延評価、体系的、異種です。 オブジェクトはパイプラインの最初の部分であり、データを読み込みます。 このチュートリアルでは、コメントと対応する有害または無害のセンチメントを含むデータセットが読み込まれます。 これを使用して、モデルを作成してトレーニングします。

 `Train` メソッドの最初の行として、次のコードを追加します。

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a>データを抽出して変換する

データの前処理とクリーニングは、機械学習でデータ セットを効果的に使用する前に発生する重要なタスクです。 多くの場合、生データはノイズが多くて信頼性が低く、値が欠落している可能性もあります。 これらのモデル化タスクを行わずにデータを使用すると、誤解を招く結果が生じるおそれがあります。

ML.NET の変換パイプラインによって、トレーニングまたはテストの前にデータに適用するカスタム変換セットが作成されます。 この変換の主な目的は、データの[特徴付け](../resources/glossary.md#feature-engineering)です。 機械学習アルゴリズムによって理解されるのは、[特徴付け](../resources/glossary.md#feature)されたデータです。したがって、次の手順では、テキスト データを ML アルゴリズムが認識できる形式に変換します。 その形式は、[数値ベクトル](../resources/glossary.md#numerical-feature-vector)です。

次に、`mlContext.Transforms.Text.FeaturizeText` を呼び出します。これによってテキスト列 (`SentimentText`) が特徴付けされ、機械学習アルゴリズムで使用される `Features` という数値ベクトルになります。 これは、実質的にパイプラインになる <xref:Microsoft.ML.Data.EstimatorChain%601> を返すラッパー呼び出しです。 後でトレーナーを `EstimatorChain` に付加するときに、この `pipeline` を指定します。 次のコード行を追加します。

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

>[!WARNING]
> ML.NET バージョン 0.10 では、変換パラメーターの順序が変更されました。 アプリケーションを実行してモデルを構築するまで、これによるエラーは出力されません。 変換パラメーターの名前を上記のコード スニペットに示すように使用してください。

これが前処理/特徴付けのステップです。 ML.NET に用意されているその他のコンポーネントを使用すると、モデルでより良い結果が得られます。

## <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

トレーナーを追加するには、<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> オブジェクトを返す `mlContext.Transforms.Text.FeaturizeText` ラッパー メソッドを呼び出します。 これは、このパイプラインで使用するデシジョン ツリーの学習器です。 `FastTreeBinaryClassificationTrainer` が `pipeline` に追加されます。これは、特徴付けされた `SentimentText` (`Features`) と `Label` 入力パラメーターを受け入れて、履歴データから学習します。

`Train` メソッドに次のコードを追加します。

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>モデルをトレーニングする

読み込まれて変換されたデータ セットに基づいて、モデル <xref:Microsoft.ML.Data.TransformerChain%601> をトレーニングします。 推定器が定義されたら、既に読み込まれたトレーニング データを提供しながら、<xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> を使用してモデルをトレーニングします。 これにより、予測で使用されるモデルが返されます。 `pipeline.Fit()` でパイプラインをトレーニングし、`DataView` に基づいて `Transformer` を返します。 これが行われるまで、実験は実行されません。

`Train` メソッドに次のコードを追加します。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>評価に使用する、トレーニングされたモデルを保存して返す

この時点で、既存または新規のどの .NET アプリケーションにも統合できる、型が <xref:Microsoft.ML.Data.TransformerChain%601> のモデルができました。 `Train` メソッドの最後で、モデルを返します。

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a>モデルを評価する

これでモデルの作成とトレーニングが完了したので、品質保証と検証のために、別のデータ セットを使用してモデルを評価します。 `Evaluate` メソッドでは、`Train` で作成されたモデルが渡されて評価されます。 `Train` の直後に、次のコードに示すように `Evaluate` メソッドを作成します。

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` メソッドは次のタスクを実行します。

* テスト データ セットを読み込む。
* バイナリ評価器を作成する。
* モデルを評価し、メトリックを作成する。
* メトリックを表示する。

`Train` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

前に初期化した `_textLoader` グローバル変数と `_testDataPath` グローバル フィールドを使用して、テスト データセットを読み込みます。 このデータ セットを品質チェックとして使用して、モデルを評価できます。 `Evaluate` メソッドに次のコードを追加します。

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

次に、機械学習の `model` パラメーター (変換器) を使用し、特徴を入力して予測を返します。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

`BinaryClassificationContext.Evaluate` メソッドは、指定されたデータセットを使用して `PredictionModel` の品質メトリックを計算します。 これによって返される `BinaryClassificationEvaluator.CalibratedResult` オブジェクトには、バイナリ分類評価器によって計算されるメトリック全体が含まれます。 これらを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>モデル検証のためのメトリックを表示する

次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

モデルを返す前に .zip ファイルに保存するには、`Evaluate` 内に次の行を追加して `SaveModelAsFile` メソッドを呼び出します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a>モデルを .zip ファイルとして保存する

`Evaluate` メソッドの直後に、次のコードを使用して `SaveModelAsFile` メソッドを作成します。

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` メソッドは次のタスクを実行します。

* モデルを .zip ファイルとして保存します。

次に、モデルを再利用して他のアプリケーションで使用できるようにモデルを保存するメソッドを作成します。 `ITransformer` には <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> メソッドがあり、`_modelPath` グローバル フィールドと <xref:System.IO.Stream> を受け入れます。 これを zip ファイルとして保存するには、`FileStream` を作成した直後に `SaveTo` メソッドを呼び出します。 `SaveModelAsFile` メソッドに次のコード行を追加します。

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
読み込み済みのモデルを使用して配置および予測する `_modelPath` を使用してコンソール メッセージを記述することで、ファイルが書き込まれた場所も表示できるようになります。これには次のコードを使用します。

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>保存したモデルを使用してテスト データの結果を予測する

`Evaluate` メソッドの直後に、次のコードを使用して `Predict` メソッドを作成します。

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

`Predict` メソッドは次のタスクを実行します。

* テスト データの 1 つのコメントを作成する。
* テスト データに基づいてセンチメントを予測する。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

`model` は多数のデータ行を操作する `transformer` ですが、よくある運用シナリオとして個々の例に対する予測のニーズがあります。 <xref:Microsoft.ML.PredictionEngine%602> は、`CreatePredictionEngine` メソッドから返されるラッパーです。 次の行を追加して、`PredictionEngine` を `Predict` メソッドの 1 行目として作成しましょう。

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
コメントを追加して、`Predict` メソッドでトレーニングされたモデルの予測をテストします。これには `SentimentData` のインスタンスを作成します。

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 これを使用すると、コメント データの 1 インスタンスのセンチメントが有害か無害かを予測できます。 予測を取得するには、データに対して <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> を使用します。 入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a>モデルの使用: 予測

結果を共有し、それに応じたアクションを実行するために、`SentimentText` および対応するセンチメント予測を表示します。 これは運用化と呼ばれ、返されたデータを運用ポリシーとして使用します。 次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果の表示を作成します。

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>読み込み済みのモデルを使用して配置および予測する

`SaveModelAsFile` メソッドの直前に、次のコードを使用して `PredictWithModelLoadedFromFile` メソッドを作成します。

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

`PredictWithModelLoadedFromFile` メソッドは次のタスクを実行します。

* バッチ テスト データを作成します。
* テスト データに基づいてセンチメントを予測する。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

`Predict` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

`PredictWithModelLoadedFromFile` メソッドでトレーニングされるモデルの予測をテストするために、いくつかのコメントを追加します。

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

モデルを読み込みます

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

モデルは既にあるので、それを利用して、<xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> メソッドでコメント データのセンチメントが有害か無害かを予測できます。 予測を取得するには、新しいデータに対して `Predict` を使用します。 入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。 予測のために `PredictWithModelLoadedFromFile` メソッドに次のコードを追加します。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a>予測のために読み込み済みのモデルを使用する

結果を共有し、それに応じたアクションを実行するために、`SentimentText` および対応するセンチメント予測を表示します。 これは運用化と呼ばれ、返されたデータを運用ポリシーとして使用します。 次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果のヘッダーを作成します。

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

予測された結果を表示する前に、元のコメントとその予測されたセンチメントが一緒に表示されるように、センチメントと予測を結合します。 次のコードでは <xref:System.Linq.Enumerable.Zip%2A> メソッドを使用してそれを行うため、そのコードを次に追加します。

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

これで `SentimentText` と `Sentiment` が 1 つのクラスに結合されたので、<xref:System.Console.WriteLine?displayProperty=nameWithType> メソッドを使用して結果を表示できます。

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

推定されたタプル要素名は C# 7.1 の新機能であり、このプロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。
そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。 **[OK]** ボタンを選択します。

## <a name="results"></a>結果

結果は以下のようになるはずです。 パイプラインが処理されると、メッセージが表示されます。 警告または処理メッセージが表示されることがありますが、 わかりやすくするために、それらは次の結果から削除してあります。

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

おめでとうございます!  これで、メッセージのセンチメントを分類および予測するための機械学習モデルをビルドできました。 このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習アルゴリズムを選択する
> * データを準備する
> * データを変換する
> * モデルをトレーニングする
> * モデルを評価する
> * トレーニング済みモデルを使用して予測する
> * 読み込み済みのモデルを使用して配置および予測する

さらに詳しく学習するには、次のチュートリアルに進んでください。
> [!div class="nextstepaction"]
> [問題の分類](github-issue-classification.md)

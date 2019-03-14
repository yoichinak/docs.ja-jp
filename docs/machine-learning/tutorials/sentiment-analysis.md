---
title: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する
description: バイナリ分類のシナリオで ML.NET を使用する方法を学習して、センチメント予測をどのように使用して適切なアクションを実行するかを理解します。
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d7e46b489506f4adad843ba5315afde4c7689b4e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723323"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>チュートリアル: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する

このサンプル チュートリアルでは、ML.NET を使用して、肯定的または否定的な感情のいずれかを予測するセンチメント分類器の作成を示します。これは、Visual Studio 2017 で C# を使用する .NET Core コンソール アプリケーションを通して実行されます。 機械学習の世界では、この種の予測は二項分類と呼ばれます。

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

このチュートリアルと関連サンプルでは、現時点では **ML.NET バージョン 0.11** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

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

このサンプルは ML.NET を使用するコンソール アプリケーションであり、センチメントを分類して肯定的か否定的かを予測するモデルをトレーニングします。 Yelp センチメント データセットは、カリフォルニア大学アーバイン校 (UCI) 提供のデータセットです。これがトレーニング データセットとテスト データセットに分割されます。 サンプルでは、テスト データセットを使用してモデルを評価して、品質分析を実行します。 

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。

* [UCI Sentiment Labeled Sentences データセット zip ファイル](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

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

トレーニング データ: Web サイトのコメントは、肯定的 (1) または否定的 (0) (**センチメント**) のいずれかになります。

次の例のような、新しい Web サイト コメントの**センチメント**が肯定的か否定的かを予測します。

* ここの給仕スタッフは最高です。 とても有能です。
* この場所のスープは最悪です。

このシナリオには、分類機械学習アルゴリズムが適しています。

### <a name="about-the-classification-algorithm"></a>分類アルゴリズムについて

分類は、データを使用して項目またはデータ行のカテゴリ、型、クラスを**判断**する機械学習アルゴリズムです。 分類はたとえば、次のような目的に使用できます。

* センチメントが肯定的か否定的かを判断する。
* 電子メールをスパム、迷惑メール、正常なメールに分類する。
* 患者の検体が癌性かどうかを判断する。
* 顧客を販売キャンペーンへの反応性で分類する。

多くの場合、分類アルゴリズムは次のいずれかの種類です。

* バイナリ: A か B のいずれかである。
* 多クラス: 1 つのモデルを使用して予測できるカテゴリが多数ある。

Web サイトのコメントは、肯定的または否定的のいずれかとして分類する必要があるため、二項分類アルゴリズムが使用されます。 

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「SentimentAnalysis」と入力し、**[OK]** を選択します。

2. プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

3. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

### <a name="prepare-your-data"></a>データを準備する

1. [UCI Sentiment Labeled Sentences データセット zip ファイル (次の注の引用を参照)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) をダウンロードして解凍します。

2. `yelp_labelled.txt` ファイルを、作成した *Data* ディレクトリにコピーします。

> [!NOTE]
> このチュートリアルで使用されるデータセットは、「From Group to Individual Labels using Deep Features」 (Kotzias 他 著、 KDD 2015) のものであり、UCI 機械学習リポジトリ (Dua, D. and Karra Taniskidou, E.(2017)) でホストされています。 UCI 機械学習リポジトリ [http://archive.ics.uci.edu/ml]。 カリフォルニア州アーバイン: カリフォルニア大学情報コンピュータサイエンス学部。

3. ソリューション エクスプローラーで、`yelp_labeled.txt` ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

最近ダウンロードしたデータセット ファイルのパスと保存したモデル ファイルのパスを保持するために、2 つのグローバル フィールドを作成する必要があります。

* `_dataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。
* `_modelPath` には、トレーニング済みのモデルを保存するパスが含まれます。

`Main` メソッドのすぐ上にある行に次のコードを追加して、それらのパスを指定します。

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

入力データと予測のために、いくつかのクラスを作成する必要があります。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。 次に、**[追加]** を選択します。

    コード エディターで *SentimentData.cs* ファイルが開きます。 *SentimentData.cs* の先頭に次の `using` ステートメントを 追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

既存のクラス定義を削除し、`SentimentData` と `SentimentPrediction` の 2 つのクラスを含む次のコードを *SentimentData.cs* ファイルに追加します。

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

入力データセット クラス `SentimentData` には、コメントの `string` (`SentimentText`) と、肯定的または否定的のいずれかであるセンチメントの値を持つ `bool` (`Sentiment`) があります。 どちらのフィールドにも <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> 属性が添付されています。 この属性は、データ ファイルの各フィールドの順序を示しています。  さらに、`Sentiment` プロパティには、それを `Label` フィールドとして指定する <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> があります。 `SentimentPrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。 これは、1 つのブール値 (`Sentiment`) と、`PredictedLabel` `ColumnName` 属性を持ちます。 `Label` はモデルを作成してトレーニングするために使用され、モデルを評価するための分割されたテスト データセットでも使用されます。 `PredictedLabel` は予測と評価の際に使用されます。 評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。

ML.NET を使用してモデルをビルドするときは、まず <xref:Microsoft.ML.MLContext> を作成します。 `MLContext` は、概念的には Entity Framework での `DbContext` の使用に相当します。 環境によって、例外の追跡とログ記録に使用できる ML ジョブのコンテキストが提供されます。

### <a name="initialize-variables-in-main"></a>Main で変数を初期化する

`mlContext` という変数を作成し、`MLContext` の新しいインスタンスで初期化します。  `Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

`Main` メソッドに次のコード行を追加します。

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData` メソッドは次のタスクを実行します。

* データを読み込みます。
* 読み込んだデータセットを、トレーニングデータセットとテスト データセットに分割します。
* 分割されたトレーニングデータセットとテスト データセットを返します。

`Main` メソッドの直後に、次のコードを使用して `LoadData` メソッドを作成します。

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>データを読み込む

前に作成した `SentimentData` データ モデルの種類がデータセット スキーマと一致するため、<xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29> の `MLContext.Data.ReadFromTextFile` ラッパーを使用して、初期化、マッピング、およびデータセットの読み込みを 1 行のコードに組み合わせることができます。 <xref:Microsoft.Data.DataView.IDataView> が返されます。 

 `Transforms` の入力および出力として、`DataView` は基本的なデータ パイプラインの種類であり、`LINQ` の `IEnumerable` と同等です。

ML.NET ではデータは SQL ビューに似ています。 つまり、遅延評価、体系的、異種です。 オブジェクトはパイプラインの最初の部分であり、データを読み込みます。 このチュートリアルでは、コメントと対応する有害または無害のセンチメントを含むデータセットが読み込まれます。 これを使用して、モデルを作成してトレーニングします。

 `LoadData` メソッドの最初の行として、次のコードを追加します。

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>モデルのトレーニング用とテスト用にデータセットを分割する

次に、モデルをトレーニングするためのトレーニング データセットと、モデルを評価するためのテスト データセットの両方が必要です。 <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> をラップする `MLContext.BinaryClassification.TrainTestSplit` を使用して、読み込まれたデータセットをトレーニング データセットとテスト データセットに分割し、それらを <xref:Microsoft.ML.TrainCatalogBase.TrainTestData> に返します。 `testFraction` パラメーターを使用して、テスト セット用のデータの割合を指定できます。 既定値は 10% ですが、ここでは、評価でより多くのデータを使用するために 20% を使用します。  

読み込まれたデータを必要なデータセットに分割するには、`LoadData` メソッドの次の行として、次のコードを追加します。

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

`LoadData` メソッドの最後に、`splitDataView` が返されます。

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>モデルを構築してトレーニングする

`Main` メソッドの次のコード行として、`BuildAndTrainModel` メソッドに次の呼び出しを追加します。

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` メソッドは次のタスクを実行します。

* データを抽出して変換します。
* モデルをトレーニングする。
* テスト データに基づいてセンチメントを予測する。
* モデルを返します。

`Main` メソッドの直後に、次のコードを使用して `Train` メソッドを作成します。

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

Train メソッドに 2 つのパラメーターが渡されていることに注意してください。`MLContext` はコンテキスト (`mlContext`)、`IDataView` はトレーニング データセット (`splitTrainSet`) に関するものです。 

## <a name="extract-and-transform-the-data"></a>データを抽出して変換する

データの前処理とクリーニングは、機械学習でデータ セットを効果的に使用する前に発生する重要なタスクです。 多くの場合、生データはノイズが多くて信頼性が低く、値が欠落している可能性もあります。 これらのモデル化タスクを行わずにデータを使用すると、誤解を招く結果が生じるおそれがあります。

ML.NET の変換パイプラインによって、トレーニングまたはテストの前にデータに適用するカスタム変換セットが作成されます。 この変換の主な目的は、データの[特徴付け](../resources/glossary.md#feature-engineering)です。 機械学習アルゴリズムによって理解されるのは、[特徴付け](../resources/glossary.md#feature)されたデータです。したがって、次の手順では、テキスト データを ML アルゴリズムが認識できる形式に変換します。 その形式は、[数値ベクトル](../resources/glossary.md#numerical-feature-vector)です。

次に、`mlContext.Transforms.Text.FeaturizeText` を呼び出します。これによってテキスト列 (`SentimentText`) が特徴付けされ、機械学習アルゴリズムで使用される `Features` という数値ベクトルになります。 これは、実質的にパイプラインになる <xref:Microsoft.ML.Data.EstimatorChain%601> を返すラッパー呼び出しです。 後でトレーナーを `EstimatorChain` に付加するときに、この `pipeline` を指定します。 次のコード行を追加します。

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> ML.NET バージョン 0.10 では、変換パラメーターの順序が変更されました。 アプリケーションを実行してモデルを構築するまで、これによるエラーは出力されません。 変換パラメーターの名前を上記のコード スニペットに示すように使用してください。

これが前処理/特徴付けのステップです。 ML.NET に用意されているその他のコンポーネントを使用すると、モデルでより良い結果が得られます。

## <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

トレーナーを追加するには、<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> オブジェクトを返す `mlContext.BinaryClassification.Trainers.FastTree` ラッパー メソッドを呼び出します。 これは、このパイプラインで使用するデシジョン ツリーの学習器です。 `FastTreeBinaryClassificationTrainer` が `pipeline` に追加されます。これは、特徴付けされた `SentimentText` (`Features`) と `Label` 入力パラメーターを受け入れて、履歴データから学習します。

`BuildAndTrainModel` メソッドに次のコードを追加します。

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>モデルをトレーニングする

読み込まれて変換されたデータ セットに基づいて、モデル <xref:Microsoft.ML.Data.TransformerChain%601> をトレーニングします。 推定器が定義されたら、既に読み込まれたトレーニング データを提供しながら、<xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> メソッドを使用してモデルをトレーニングします。 これにより、予測で使用されるモデルが返されます。 `pipeline.Fit()` でパイプラインをトレーニングし、`DataView` に基づいて `Transformer` を返します。 `.Fit()` メソッドが実行されるまで、実験は実行されません。

`BuildAndTrainModel` メソッドに次のコードを追加します。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>評価に使用する、トレーニングされたモデルを保存して返す

この時点で、既存または新規のどの .NET アプリケーションにも統合できる、型が <xref:Microsoft.ML.Data.TransformerChain%601> のモデルができました。 `BuildAndTrainModel` メソッドの最後で、モデルを返します。

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>モデルを評価する

これでモデルの作成とトレーニングが完了したので、品質保証と検証のために、別のデータ セットを使用してモデルを評価します。 `Evaluate` メソッドでは、`BuildAndTrainModel` で作成されたモデルが渡されて評価されます。 `BuildAndTrainModel` の直後に、次のコードに示すように `Evaluate` メソッドを作成します。

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate` メソッドは次のタスクを実行します。

* テスト データ セットを読み込む。
* binaryclassification 評価器を作成します。
* モデルを評価し、メトリックを作成する。
* メトリックを表示する。

`Train` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

次に、機械学習の `model` パラメーター (変換器) と `splitTestSet` パラメーターを使用して特徴を入力し、予測を返します。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

`mlContext.BinaryClassification.Evaluate` メソッドは、指定されたデータセットを使用して `PredictionModel` の品質メトリックを計算します。 これによって返される <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> オブジェクトには、バイナリ分類評価器によって計算されるメトリック全体が含まれます。 これらを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>モデル検証のためのメトリックを表示する

次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

モデルを返す前に .zip ファイルに保存するには、`Evaluate` 内に次の行を追加して `SaveModelAsFile` メソッドを呼び出します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

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

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>読み込み済みのモデルを使用して配置および予測する

`_modelPath` を使用してコンソール メッセージを記述することで、ファイルが書き込まれた場所も表示できるようになります。これには次のコードを使用します。

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>保存したモデルを使用してテスト データの結果を予測する

`Evaluate` メソッドの直後に、次のコードを使用して `UseModelWithSingleItem` メソッドを作成します。

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem` メソッドは次のタスクを実行します。

* テスト データの 1 つのコメントを作成する。
* テスト データに基づいてセンチメントを予測する。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

`model` は多数のデータ行を操作する `transformer` ですが、よくある運用シナリオとして個々の例に対する予測のニーズがあります。 <xref:Microsoft.ML.PredictionEngine%602> は、`CreatePredictionEngine` メソッドから返されるラッパーです。 次の行を追加して、`PredictionEngine` を `Predict` メソッドの 1 行目として作成しましょう。

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
コメントを追加して、`Predict` メソッドでトレーニングされたモデルの予測をテストします。これには `SentimentData` のインスタンスを作成します。

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 これを使用すると、コメント データの 1 つのインスタンスのセンチメントが肯定的か否定的かを予測できます。 予測を取得するには、データに対して <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> を使用します。 入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>モデルを使用する: 予測

結果を共有し、それに応じたアクションを実行するために、`SentimentText` および対応するセンチメント予測を表示します。 これは運用化と呼ばれ、返されたデータを運用ポリシーとして使用します。 次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果の表示を作成します。

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>読み込み済みのモデルを使用して配置および予測する

`SaveModelAsFile` メソッドの直前に、次のコードを使用して `UseLoadedModelWithBatchItems` メソッドを作成します。

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

`UseLoadedModelWithBatchItems` メソッドは次のタスクを実行します。

* バッチ テスト データを作成します。
* テスト データに基づいてセンチメントを予測する。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

`UseModelWithSingleItem` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

`UseLoadedModelWithBatchItems` メソッドでトレーニングされるモデルの予測をテストするために、いくつかのコメントを追加します。

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

モデルを読み込みます

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

モデルは既にあるので、それを利用して、<xref:Microsoft.ML.ITransformer.Transform%2A> メソッドでコメント データのセンチメントが有害か無害かを予測できます。 予測を取得するには、新しいデータに対して `Predict` を使用します。 入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。 予測のために `UseLoadedModelWithBatchItems` メソッドに次のコードを追加します。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>読み込み済みのモデルを予測のために使用する

結果を共有し、それに応じたアクションを実行するために、`SentimentText` および対応するセンチメント予測を表示します。 これは運用化と呼ばれ、返されたデータを運用ポリシーとして使用します。 次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果のヘッダーを作成します。

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

予測された結果を表示する前に、元のコメントとその予測されたセンチメントが一緒に表示されるように、センチメントと予測を結合します。 次のコードでは <xref:System.Linq.Enumerable.Zip%2A> メソッドを使用してそれを行うため、そのコードを次に追加します。

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

これで `SentimentText` と `Sentiment` が 1 つのクラスに結合されたので、<xref:System.Console.WriteLine?displayProperty=nameWithType> メソッドを使用して結果を表示できます。

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

推定されたタプル要素名は C# 7.1 の新機能であり、このプロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。
そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。 **[OK]** ボタンを選択します。

## <a name="results"></a>結果

結果は以下のようになるはずです。 パイプラインが処理されると、メッセージが表示されます。 警告または処理メッセージが表示されることがありますが、 わかりやすくするために、それらは次の結果から削除してあります。

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

おめでとうございます!  これで、メッセージのセンチメントを分類および予測するための機械学習モデルをビルドできました。 

優れたモデルの構築は、反復的なプロセスです。 このチュートリアルでは、モデルのトレーニングを短時間で実行するために小さなデータセットを使用しているため、このモデルの品質は最初は低くなっています。 このモデルの品質に満足できなければ、大規模なトレーニング データセットを使用するか、別のトレーニング アルゴリズムとアルゴリズムごとに異なるハイパーパラメーターを選択することで、モデルを改良することを試行できます。

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。

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

---
title: ML.NET を GitHub の問題の多クラス分類シナリオで使用する
description: GitHub の問題を分類し、それを特定の領域に割り当てるための多クラス分類シナリオで、ML.NET を使用する方法について説明します。
ms.date: 02/20/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: fdb6621078854d80f0af484ae1b92526f0f9cbb8
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584292"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>チュートリアル: ML.NET を、GitHub の問題を分類する多クラス分類シナリオで使用する

このサンプル チュートリアルでは、Visual Studio 2017 で ML.NET を使用して、C# を使用する .NET Core コンソール アプリケーションから GitHub の問題を作成する方法を示します。

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

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

## <a name="github-issue-sample-overview"></a>GitHub の問題のサンプルの概要

このサンプルは ML.NET を使用するコンソール アプリケーションであり、GitHub の問題の区分ラベルを分類および予測するモデルをトレーニングします。 また、高品質な分析のために、2 番目のデータ セットを使用してモデルを評価します。 問題のデータセットは、dotnet/corefx GitHub リポジトリにあります。

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) リポジトリで確認できます。

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。

* [Github の問題のタブ区切りのファイル (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv)。
* [Github の問題のテスト タブ区切りのファイル (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv)。

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

このチュートリアルでの問題は、優先順位付けとスケジューリングを行うための正しいラベル付けのために、受け取った GitHub の問題がどの区分に属するかを理解することです。

問題は次の部分に分けることができます。

* 問題のタイトル テキスト
* 問題の説明テキスト
* モデルのトレーニング データの区分値
* 評価して操作で使用できる予測される区分値

次に、区分を**決定**する必要があります。これは機械学習タスクを選択するときに役立ちます。

## <a name="select-the-appropriate-machine-learning-algorithm"></a>適切な機械学習アルゴリズムを選択する

この問題に関してわかっていることは次のとおりです。

トレーニング データ:

GitHub の問題は、次の例のようないくつかの領域 (**区分**) にラベル分けできます。

* area-System.Numerics
* area-System.Xml
* area-Infrastructure
* area-System.Linq
* area-System.IO

次の例のように、新しい GitHub の問題の**区分**を予測します。

* Contract.Assert 対 Debug.Assert
* System.Xml のフィールドを読み取り専用にする

このシナリオには、分類機械学習アルゴリズムが適しています。

### <a name="about-the-classification-learning-algorithm"></a>分類学習アルゴリズムについて

分類は、データを使用して項目またはデータ行のカテゴリ、型、クラスを**判断**する機械学習アルゴリズムです。 分類はたとえば、次のような目的に使用できます。

* センチメントが肯定的か否定的かを判断する。
* 電子メールをスパム、迷惑メール、正常なメールに分類する。
* 患者の検体が癌性かどうかを判断する。
* 顧客を販売キャンペーンへの反応性で分類する。

多くの場合、分類学習アルゴリズムは次のいずれかの種類です。

* バイナリ: A か B のいずれかである。
* 多クラス: 1 つのモデルを使用して予測できるカテゴリが多数ある。

この種の問題では、問題カテゴリの予測が 2 つだけ (バイナリ) ではなく複数のカテゴリの 1 つ (多クラス) なので、多クラス分類学習アルゴリズムを使用します。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

### <a name="create-a-project"></a>プロジェクトを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「GitHubIssueClassification」と入力し、**[OK]** を選択します。

2. プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

3. プロジェクトに *Models* という名前のディレクトリを作成して、モデルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Models」と入力し、Enter キーを押します。

4. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

### <a name="prepare-your-data"></a>データを準備する

1. [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) データ セットと [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) データ セットをダウンロードして、それらを作成済みの *Data* フォルダーに保存します。 1 番目のデータ セットでは機械学習モデルをトレーニングし、2 番目のデータ セットはモデルの精度を評価するために使用します。

2. ソリューション エクスプローラーで、各 \*.tsv ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

最近ダウンロードしたファイルのパスを保存する 3 つのグローバル フィールドと、`MLContext`、`DataView`、`PredictionEngine`、`TextLoader` のためのグローバル変数を作成します。

* `_trainDataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。
* `_testDataPath` には、モデルの評価に使用するデータ セットのパスが含まれます。
* `_modelPath` には、トレーニング済みのモデルを保存するパスが含まれます。
* `_mlContext` は処理コンテキストを提供する <xref:Microsoft.ML.MLContext> です。
* `_trainingDataView` は、トレーニング データセットを処理するために使用される <xref:Microsoft.Data.DataView.IDataView> です。
* `_predEngine` は、1 つの予測に使用される <xref:Microsoft.ML.PredictionEngine%602> です。
* `_reader` は、データセットの読み込みと変換に使用される <xref:Microsoft.ML.Data.TextLoader> です。

`Main` メソッドのすぐ上にある行に次のコードを追加して、それらのパスとその他の変数を指定します。

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

入力データと予測のために、いくつかのクラスを作成します。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを「*GitHubIssueData.cs*」に変更します。 次に、**[追加]** を選択します。

    コード エディターで *GitHubIssueData.cs* ファイルが開きます。 *GitHubIssueData.cs* の先頭に次の `using` ステートメントを追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

既存のクラス定義を削除し、`GitHubIssue` と `IssuePrediction` の 2 つのクラスを含む次のコードを *GitHubIssueData.cs* ファイルに追加します。

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` は、入力データセット クラスで、次の <xref:System.String> フィールドがあります。

* `ID` には GitHub の問題の ID 値が含まれます
* `Area` には、`Area` ラベルの値が含まれます
* `Title` には GitHub の問題のタイトルが含まれます
* `Description` には GitHub の問題の説明が含まれます

`IssuePrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。 これは、1 つの `string` (`Area`) と、`PredictedLabel` `ColumnName` 属性があります。 `Label` はモデルを作成してトレーニングするために使用され、2 番目のデータ セットでもモデルを評価するために使用されます。 `PredictedLabel` は予測と評価の際に使用されます。 評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。

ML.NET を使用してモデルをビルドするときは、まず <xref:Microsoft.ML.MLContext> を作成します。 `MLContext` は、概念的には Entity Framework での `DbContext` の使用に相当します。 環境によって、例外の追跡とログ記録に使用できる ML ジョブのコンテキストが提供されます。

### <a name="initialize-variables-in-main"></a>Main で変数を初期化する

複数のトレーニング間で反復可能な決定論的結果を得るために、`_mlContext` グローバル変数をランダム シード (`seed: 0`) を使用して `MLContext` の新しいインスタンスで初期化します。  `Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>データを読み込む

次いで、`_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> グローバル変数を初期化して、`_trainDataPath` パラメーターを使用してデータを読み込みます。

 [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer) の入力および出力として、`DataView` は基本的なデータ パイプラインの種類であり、`LINQ` の `IEnumerable` と同等です。

ML.NET ではデータは `SQL view` に似ています。 つまり、遅延評価、体系的、異種です。 オブジェクトはパイプラインの最初の部分であり、データを読み込みます。 このチュートリアルでは、問題のタイトル、説明、および対応する区分 GitHub ラベルを使用してデータセットを読み込みます。 モデルの作成とトレーニングには、`DataView` が使用されます。

以前に作成した `GitHubIssue` データ モデルの種類がデータセット スキーマと一致するため、初期化、マッピング、およびデータセットの読み込みを 1 行のコードに組み合わせることができます。

行の最初の部分 (`CreateTextLoader<GitHubIssue>(hasHeader: true)`) では、`GitHubIssue` データ モデル型からデータセット スキーマを推論し、データセットのヘッダーを使用し、<xref:Microsoft.ML.Data.TextLoader> を作成します。

データ スキーマは、`GitHubIssue` クラスを作成したときに既に定義しています。 スキーマでは次のとおりです。

* 最初の列 `ID` (GitHub 問題 ID)
* 2 番目の列 `Area` (トレーニングの予測)
* 3 番目の列 `Title` (GitHub の問題のタイトル) は、`Area` の予測に使用される最初の[特徴](../resources/glossary.md##feature)です
* 第 4 列 `Description` は、`Area` の予測に使用される 2 番目の特徴です

行の 2 番目の部分 (`.Read(_trainDataPath)`) では <xref:Microsoft.ML.Data.TextLoader.Read%2A> メソッドを使用して、`IDataView` (`_trainingDataView`) グローバル変数に `_trainDataPath` を使用してトレーニング用のテキスト ファイルを読み込みます。  

パイプラインで利用するために `_trainingDataView` グローバル変数を初期化して読み込むには、`mlContext` 初期化の後に次のコードを追加します。

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


`Main` メソッドに次のコード行を追加します。

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` メソッドは次のタスクを実行します。

* データを抽出して変換します。
* 処理パイプラインを返します。

`Main` メソッドの直後に、次のコードを使用して `ProcessData` メソッドを作成します。

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>特徴を抽出してデータを変換する

データの前処理とクリーニングは、機械学習でデータ セットを効果的に使用する前に発生する重要なタスクです。 多くの場合、生データはノイズが多くて信頼性が低く、値が欠落している可能性もあります。 これらのモデル化タスクを行わずにデータを使用すると、誤解を招く結果が生じるおそれがあります。

ML.NET の変換パイプラインによって、トレーニングまたはテストの前にデータに適用されるカスタムの `transforms` セットが作成されます。 この変換の主な目的は、データの[特徴付け](../resources/glossary.md#feature-engineering)です。 機械学習アルゴリズムによって理解されるのは、[特徴付け](../resources/glossary.md#feature)されたデータです。したがって、次の手順では、テキスト データを ML アルゴリズムが認識できる形式に変換します。 その形式は、[数値ベクトル](../resources/glossary.md#numerical-feature-vector)です。

次の手順では、`GitHubIssue` クラス内で定義された名前によって列を参照します。

モデルのトレーニングと評価が行われるとき、既定では、**Label** 列内の値が予測される適切な値と見なされます。 `GitHubIssue` の区分 GitHub ラベルを予測したいので、`Area` 列を **Label** 列にコピーします。 これを行うには、<xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> 変換クラスのラッパーである `MLContext.Transforms.Conversion.MapValueToKey` を使用します。  `MapValueToKey` は、実質的にパイプラインになる <xref:Microsoft.ML.Data.EstimatorChain%601> を返します。 後でトレーナーを `EstimatorChain` に付加するときに、この `pipeline` を指定します。 次のコード行を追加します。

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 特徴付けによって、各列内のさまざまな値に異なる数値が割り当てられ、機械学習のアルゴリズムで使用されます。 次に、`mlContext.Transforms.Text.FeaturizeText` を呼び出します。これによってテキスト列 (`Title` および `Description`) が特徴付けされ、それぞれ `TitleFeaturized` および `DescriptionFeaturized` と呼ばれる数値ベクトルになります。 次のコードを使用して、両列の特徴付けをパイプラインに追加します。

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> ML.NET バージョン 0.10 では、変換パラメーターの順序が変更されました。 これについては、ビルドするまでエラーが出力されません。 変換パラメーターの名前を上記のコード スニペットに示すように使用してください。

データの準備の最後の手順では、`Concatenate` 変換クラスを使用して、すべての特徴列を **Features** 列に結合します。 既定では、学習アルゴリズムは **Features** 列の特徴のみを処理します。 次のコードを使用してパイプラインに、この変換を追加します。

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 次に、DataView をキャッシュするために <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> を追加します。つまり、次のコードでキャッシュを使用してデータが複数回反復されると、パフォーマンスが向上する場合があります。

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> 小/中規模のデータセットの場合は、AppendCacheCheckpoint を使用して、トレーニング時間を短くします。 非常に大きいデータセットを処理するときは、使用しないでください (.AppendCacheCheckpoint() を削除します)。

`ProcessData` メソッドの最後で、パイプラインが返されます。

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

この手順で前処理と特徴付けが処理されます。 ML.NET に用意されているその他のコンポーネントを使用すると、モデルでより良い結果が得られます。

## <a name="build-and-train-the-model"></a>モデルを構築してトレーニングする

`Main` メソッドの次のコード行として、`BuildAndTrainModel` メソッドに次の呼び出しを追加します。

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` メソッドは次のタスクを実行します。

* トレーニング アルゴリズムのクラスを作成します。
* モデルをトレーニングする。
* トレーニング データに基づいて区分を予測します。
* モデルを `.zip` ファイルに保存します。
* モデルを返します。

`Main` メソッドの直後に、次のコードを使用して `BuildAndTrainModel` メソッドを作成します。

```csharp
public static EstimatorChain<KeyToValueMappingTransformer> BuildAndTrainModel(IDataView trainingDataView, EstimatorChain<ITransformer> pipeline)
{

}
```

これでトレーニング データセット (`trainingDataView`) 用の `IDataView` と、ProcessData (`pipeline`) で作成された処理用パイプライン用の <xref:Microsoft.ML.Data.EstimatorChain%601> の 2 つのパラメーターが BuildAndTrainModel メソッドに渡されます。

 `BuildAndTrainModel` メソッドの最初の行として、次のコードを追加します。

### <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

学習アルゴリズムを追加するには、<xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> オブジェクトを返す `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` ラッパー メソッドを呼び出します。  `SdcaMultiClassTrainer` が `pipeline` に追加されます。これは、特徴付けされた `Title` と `Description` (`Features`) と `Label` 入力パラメーターを受け入れて、履歴データから学習します。 元の読み取り可能な状態に戻すために、値にラベルもマップする必要があります。 これらの両アクションは、次のコードを使用して実行します。

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a>モデルをトレーニングする

読み込まれて変換されたデータ セットに基づいて、モデル <xref:Microsoft.ML.Data.TransformerChain%601> をトレーニングします。 推定器が定義されたら、既に読み込まれたトレーニング データを提供しながら、<xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> を使用してモデルをトレーニングします。 このメソッドにより、予測で使用されるモデルが返されます。 `trainingPipeline.Fit()` でパイプラインをトレーニングし、`DataView` に基づいて `Transformer` を返します。 `.Fit()` メソッドが実行されるまで、実験は実行されません。

`BuildAndTrainModel` メソッドに次のコードを追加します。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

`model` は多数のデータ行を操作する `transformer` ですが、個々の例に対する予測のニーズは、よくある運用シナリオです。 <xref:Microsoft.ML.PredictionEngine%602> は、`CreatePredictionEngine` メソッドから返されるラッパーです。 次の行を追加して、`PredictionEngine` を `BuildAndTrainModel` メソッドの次の行として作成しましょう。

[!code-csharp[CreatePredictionEngine1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>トレーニング済みモデルを使用して予測する

GitHub の問題を追加して、`Predict` メソッドでトレーニングされたモデルの予測をテストします。これには `GitHubIssue` のインスタンスを作成します。

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

これを使用して、問題のデータの 1 インスタンスの `Area` レベルを予測できます。 予測を取得するには、データに対して <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> を使用します。 入力データは文字列で、モデルには特徴付けが含まれます。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>モデルの使用: 予測結果

結果を共有し、それに応じたアクションを実行するために、`GitHubIssue` および対応する `Area` ラベル予測を表示します。  次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果の表示を作成します。

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>評価に使用する、トレーニング済みのモデルを返す

`BuildAndTrainModel` メソッドの最後で、モデルを返します。

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>モデルを評価する

これでモデルの作成とトレーニングが完了したので、品質保証と検証のために、別のデータ セットを使用してモデルを評価します。 `Evaluate` メソッドでは、`BuildAndTrainModel` で作成されたモデルが渡されて評価されます。 `BuildAndTrainModel` の直後に、次のコードに示すように `Evaluate` メソッドを作成します。

```csharp
public static void Evaluate()
{

}
```

`Evaluate` メソッドは次のタスクを実行します。

* テスト データ セットを読み込む。
* 多クラス評価器を作成する。
* モデルを評価し、メトリックを作成する。
* メトリックを表示する。

`BuildAndTrainModel` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

既にトレーニング データセットで行ったように、初期化、マッピング、テスト データの読み込みを 1 行のコードに結合できます。 このデータ セットを品質チェックとして使用して、モデルを評価できます。 `Evaluate` メソッドに次のコードを追加します。

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

`MulticlassClassificationContext.Evaluate` は、指定されたデータセットを使用してモデルの品質メトリックを計算する <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> メソッドのラッパーです。 これによって返される <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> オブジェクトには、多クラス分類評価器によって計算されるメトリック全体が含まれます。
メトリックを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。
特徴を入力し、予測を戻す、機械学習の `_trainedModel` グローバル変数 (変換器) の `Transform` メソッドの使用法に注目してください。 `Evaluate` メソッドに次のコード行を追加します。

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

多クラス分類では、次のメトリックが評価されます。

* マイクロ精度: すべてのサンプルとクラスのペアが、精度メトリックに均等に作用します。  マイクロ精度は可能な限り 1 に近づけます。

* マクロ精度: すべてのクラスが、精度メトリックに均等に作用します。 少数派のクラスは、大規模なクラスと同じ重みが与えられています。 マクロ精度は可能な限り 1 に近づけます。

* 対数損失: [対数損失](../resources/glossary.md#log-loss)に関するページを参照してください。 対数損失は可能な限り 1 に近づけます。

* 対数損失還元: 範囲は [-inf, 100] です。ここで、100 は完璧な予測で、0 は平均の予測です。 対数損失還元は可能な限り 1 に近づけます。

### <a name="displaying-the-metrics-for-model-validation"></a>モデル検証のためのメトリックを表示する

次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a>トレーニング済みの評価されたモデルを保存する

この時点で、既存または新規のどの .NET アプリケーションにも統合できる、型が <xref:Microsoft.ML.Data.TransformerChain%601> のモデルができました。 トレーニングしたモデルを .zip ファイルに保存するには、`BuildAndTrainModel` の次の行で `SaveModelAsFile` メソッドを呼び出すために次のコードを追加します。

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a>モデルを .zip ファイルとして保存する

`Evaluate` メソッドの直後に、次のコードを使用して `SaveModelAsFile` メソッドを作成します。

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` メソッドは次のタスクを実行します。

* モデルを .zip ファイルとして保存します。

次に、モデルを再利用して他のアプリケーションで使用できるようにモデルを保存するメソッドを作成します。 `ITransformer` には <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> メソッドがあり、`_modelPath` グローバル フィールドと <xref:System.IO.Stream> を受け取ります。 モデルを ZIP ファイルとして保存するには、`FileStream` を作成した直後に `SaveTo` メソッドを呼び出します。 `SaveModelAsFile` メソッドに次のコード行を追加します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

`_modelPath` を使用してコンソール メッセージを記述することで、ファイルが書き込まれた場所も表示できるようになります。これには次のコードを使用します。

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a>読み込み済みのモデルを使用して配置および予測する

`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

`Evaluate` メソッドの直後 (および `SaveModelAsFile` メソッドの直前) に、次のコードを使用して `PredictIssue` メソッドを作成します。

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` メソッドは次のタスクを実行します。

* テスト データの問題を 1 つ作成します。
* テスト データに基づいて区分を予測します。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

まず、次のコードを使用して、先ほど保存したモデルを読み込みます。

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

GitHub の問題を追加して、`Predict` メソッドでトレーニングされたモデルの予測をテストします。これには `GitHubIssue` のインスタンスを作成します。

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
これでモデルがあるので、それを使用して GitHub の問題データの 1 インスタンスの区分 GitHub ラベルを予測できます。 予測を取得するには、データに対して <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> を使用します。 入力データは文字列で、モデルには特徴付けが含まれます。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。 予測のために `PredictIssue` メソッドに次のコードを追加します。

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>予測のために読み込み済みのモデルを使用する

問題を分類し、それに応じて処理するために `Area` を表示します。 次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果の表示を作成します。

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>結果

結果は以下のようになるはずです。 パイプラインが処理されると、メッセージが表示されます。 警告または処理メッセージが表示されることがありますが、 わかりやすくするために、これらのメッセージは次の結果から削除してあります。

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

おめでとうございます!  これで、GitHub の問題用の区分ラベルを分類および予測するための機械学習モデルをビルドできました。 このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) リポジトリで確認できます。

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
> [タクシー代予測](taxi-fare.md)

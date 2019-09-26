---
title: 'チュートリアル: TensorFlow 画像分類器を再トレーニングする - 転移学習'
description: 転移学習と ML.NET を使用して画像分類 TensorFlow モデルを再トレーニングする方法について説明します。 元のモデルは、個々の画像を分類するようにトレーニングされました。 再トレーニング後、新しいモデルは、画像を広範なカテゴリに整理します。
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e069abe44b77b1dc31b78ecec1971ccc73f2e012
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054078"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>チュートリアル: 転移学習と ML.NET を使用して TensorFlow 画像分類子を再トレーニングする

転移学習と ML.NET を使用して画像分類 TensorFlow モデルを再トレーニングする方法について説明します。 元のモデルは、個々の画像を分類するようにトレーニングされました。 再トレーニング後の新しいモデルは、画像を広範なカテゴリに整理します。 

[画像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition)モデルを最初からトレーニングするには、数百万のパラメーター、大量のラベル付きトレーニング データ、膨大な量の計算リソース (数百時間の GPU) を設定する必要があります。 最初からカスタム モデルをトレーニングするほど効果的ではありませんが、転移学習を使用すると、何千もの画像と何百万ものラベル付き画像を使用し、カスタマイズされたモデルを短時間 (GPU が搭載されていないマシンで 1 時間以内) で構築できます。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
>
> * 問題を把握する
> * トレーニング済みのモデルを再利用して調整する
> * 画像を分類する

## <a name="what-is-transfer-learning"></a>転移学習とは何か

トレーニング済みのモデルを再利用して同様の問題を解決し、そのモデルのレイヤーの全部または一部を再トレーニングして問題を解決することもできます。 トレーニング済みのモデルの一部を再利用して新しいモデルを構築するこの手法は、[転移学習](https://en.wikipedia.org/wiki/Transfer_learning)と呼ばれます。

## <a name="image-classification-sample-overview"></a>画像分類サンプルの概要

このサンプルは、トレーニング済みのモデルを再利用して少量のトレーニング データで画像を分類することによって、ML.NET を使用して画像分類器を構築するコンソール アプリケーションです。

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) リポジトリで確認できます。 既定では、このチュートリアルの .NET プロジェクトの構成は .NET Core 2.2 を対象としています。

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。 

* Microsoft.ML 1.0.0 Nuget パッケージ
* Microsoft.ML.ImageAnalytics 1.0.0 Nuget パッケージ
* Microsoft.ML.TensorFlow 0.12.0 Nuget パッケージ

* [チュートリアル資産ディレクトリの .ZIP ファイル](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [InceptionV1 機械学習モデル](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>適切な機械学習タスクを選択する

[ディープ ラーニング](https://en.wikipedia.org/wiki/Deep_learning)は、Computer Vision や音声認識などの分野に革命を起こしている Machine Learning のサブセットです。

ディープ ラーニング モデルは、複数の学習レイヤーを含む多数の[ラベル付きデータ](https://en.wikipedia.org/wiki/Labeled_data)と[ニューラル ネットワーク](https://en.wikipedia.org/wiki/Artificial_neural_network)を使用してトレーニングされます。 ディープ ラーニング:

* Computer Vision などの一部のタスクでより効果的に機能します。

* 膨大なデータ量に対しても適切に機能します。

画像分類は、画像を次のような複数のカテゴリに自動的に分類することができる一般的な機械学習タスクです。

* 画像から人の顔を検出するかどうか。
* 猫と犬の検出。

 または、次の画像のように、画像が食品、おもちゃ、またはアプライアンスのいずれであるかを判断する場合。

![ピザの画像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![テディ ベアの画像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![トースターの画像](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> 上の画像は Wikimedia Commons に属し、次のように属性が付けられています。
>
> * "220px-Pepperoni_pizza.jpg" パブリック ドメイン、 https://commons.wikimedia.org/w/index.php?curid=79505 、
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - 自己撮影、CC BY-SA 2.0、 https://commons.wikimedia.org/w/index.php?curid=48166 。
> * "193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - 自分の作品、CC BY-SA 3.0、 https://commons.wikimedia.org/w/index.php?curid=27403

転移学習には、*すべてのレイヤーの再トレーニング*、*最後から 2 番目のレイヤー*など、いくつかの戦略があります。 このチュートリアルでは、"*最後から 2 番目のレイヤー戦略*" の使用方法について説明します。 "*最後から 2 番目のレイヤー戦略*" は、トレーニング済みのモデルを再利用して特定の問題を解決します。 次に、この戦略では、そのモデルの最後のレイヤーを再トレーニングして新しい問題を解決します。 トレーニング済みのモデルを新しいモデルの一部として再利用すると、時間とリソースを大幅に節約できます。

この画像分類モデルでは [Inception モデル](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)を再利用します。これは、TensorFlow モデルによって画像全体の 1,000 個のクラス ("傘"、"ジャージー"、"皿洗い機" など) への分類を試行する、`ImageNet` データセットに対してトレーニングされた人気のある画像認識モデルです。

`Inception v1 model` は[ディープ畳み込みニューラル ネットワーク](https://en.wikipedia.org/wiki/Convolutional_neural_network)と分類することができます。また、分野によっては、困難な視覚認識タスクで、人間のパフォーマンスに匹敵するかそれを超える妥当なパフォーマンスを達成できます。 モデル/アルゴリズムは、複数の研究者によって開発され、以下の元の論文に基づいています。[「Rethinking the Inception Architecture for Computer Vision (Computer Vision のためのインセプション アーキテクチャの再考)」(Szegedy 他)](https://arxiv.org/abs/1512.00567)

`Inception model` は何千種類もの画像に対して事前にトレーニングされているため、画像の識別に必要な[画像の特徴](https://en.wikipedia.org/wiki/Feature_(computer_vision))が含まれています。 以下の画像機能レイヤーは単純な特徴 (端など) を認識し、上のレイヤーはより複雑な特徴 (図形など) を認識します。 最後のレイヤーは、画像の分類方法を既に理解しているトレーニング済みのモデルから始めているため、はるかに小さいデータ セットに対してトレーニングされます。 モデルで 3 つ以上のカテゴリを分類できるので、これは[複数クラス分類器](../resources/tasks.md#multiclass-classification)の一例です。 

`TensorFlow` は、ディープ ニューラル ネットワーク (および一般的な数値計算) をトレーニングできる人気のあるディープ ラーニングおよび機械学習ツールキットであり、.ML.NET では `transformer` として実装されています。 このチュートリアルでは、`Inception model` を再利用するために使用されています。

次の図に示すように、.NET Core または .NET Framework アプリケーションに ML.NET NuGet パッケージへの参照を追加します。 内部的には、スコア付けのために既存のトレーニング済み `TensorFlow` モデル ファイルを読み込むコードを作成できるネイティブ `TensorFlow` ライブラリが ML.NET には含まれ、参照されています。  

![TensorFlow 変換 ML.NET Arch 図](./media/image-classification/tensorflow-mlnet.png)

`Inception model` は、画像を 1,000 個のカテゴリに分類するようにトレーニングされていますが、画像をより小さなカテゴリ セットにのみ分類する必要があります。 `transfer learning` の `transfer` 部分を入力します。 `Inception model` の画像を認識および分類する能力をカスタム画像分類器の新しい限られたカテゴリに転移ことができます。  

 3 つのカテゴリ セットを使用して、そのモデルの最後のレイヤーを再トレーニングします。

* 食品
* おもちゃ
* アプライアンス

レイヤーは、[多項ロジスティック回帰アルゴリズム](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)を使用して正しいカテゴリを可能な限り早く見つけます。 このアルゴリズムでは、確率を使用して答えを決定し、正しいカテゴリに 1 つの値を与え、他のカテゴリに 0 の値を与えます。  

### <a name="dataset"></a>DataSet

データ ソースは 2 つあります。`.tsv` ファイルと画像ファイルです。  `tags.tsv` ファイルには 2 つの列があります。最初の列は `ImagePath` と定義され、2 番目の列は画像に対応する `Label` です。 次のファイル例にはヘッダー行がなく、次のような内容です。

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

トレーニングとテストの画像は、zip ファイルでダウンロードする資産フォルダー内にあります。 これらの画像は Wikimedia Commons に属します。
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208)、無料メディア リポジトリ。* 2018 年 10 月 17 日 10:48 に以下から取得:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

### <a name="create-a-project"></a>プロジェクトを作成する

1. "TransferLearningTF" という **.NET Core Console アプリケーション**を作成します。

2. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択し、"**Microsoft.ML**" を検索します。 **[バージョン]** ドロップダウンをクリックし、一覧から **1.0.0** パッケージを選択し、 **[インストール]** ボタンを選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。 **Microsoft.ML.ImageAnalytics v1.0.0** と **Microsoft.ML.TensorFlow v0.12.0** について、これらの手順を繰り返します。

### <a name="prepare-your-data"></a>データを準備する

1. [プロジェクト資産ディレクトリの zip ファイル](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)をダウンロードし、展開します。

2. `assets` ディレクトリを *TransferLearningTF* プロジェクト ディレクトリにコピーします。 このディレクトリとそのサブディレクトリには、このチュートリアルに必要なデータ ファイルとサポート ファイル (次の手順でダウンロードして追加する Inception モデルを除く) が含まれています。

3. [Inception モデル](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)をダウンロードして展開します。

4. `inception5h` ディレクトリの内容をコピーし、*TransferLearningTF* プロジェクトの `assets\inputs-train\inception` ディレクトリに展開します。 次の画像に示すように、このディレクトリには、このチュートリアルに必要なモデルと追加のサポート ファイルが含まれています。

   ![Inception ディレクトリの内容](./media/image-classification/inception-files.png)

5. ソリューション エクスプローラーで、資産ディレクトリとサブディレクトリ内の各ファイルを右クリックし、 **[プロパティ]** を選択します。 **[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

さまざまな資産のパスを保持するグローバル フィールドと、`LabelTokey`、`ImageReal`、および `PredictedLabelValue` のグローバル変数を作成します。

* `_assetsPath` には、資産のパスが含まれます。
* `_trainTagsTsv` には、トレーニング画像データ タグの tsv ファイルのパスが含まれます。
* `_predictTagsTsv` には、予測画像データ タグの tsv ファイルのパスが含まれます。
* `_trainImagesFolder` には、モデルのトレーニングに使用される画像のパスが含まれます。
* `_predictImagesFolder` には、トレーニング済みのモデルによって分類される画像のパスが含まれます。
* `_inceptionPb` には、モデルの再トレーニングに再利用できるトレーニング済みの Inception モデルのパスが含まれます。
* `_inputImageClassifierZip` には、トレーニング済みのモデルの読み込み元のパスが含まれます。
* `_outputImageClassifierZip` には、トレーニング済みのモデルを保存するパスが含まれます。
* `LabelTokey` は、キーにマップされた `Label` 値です。
* `ImageReal` は予測された画像値を含む列です。
* `PredictedLabelValue` は予測されたラベル値を含む列です。

`Main` メソッドのすぐ上にある行に次のコードを追加して、それらのパスとその他の変数を指定します。

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

入力データと予測のために、いくつかのクラスを作成します。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを「*ImageData.cs*」に変更します。 次に **[追加]** を選択します。

    コード エディターで *ImageData.cs* ファイルが開きます。 次の `using` ステートメントを *ImageData.cs* の先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

既存のクラス定義を削除し、`ImageData` クラスの次のコードを *ImageData.cs* ファイルに追加します。

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` は、入力画像データ クラスであり、次の <xref:System.String> フィールドがあります。

* `ImagePath` には、画像ファイル名が含まれます。
* `Label` には、画像ラベルの値が含まれます。

`ImagePrediction` のプロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *ImagePrediction.cs* に変更します。 次に **[追加]** を選択します。

    コード エディターに *ImagePrediction.cs* ファイルが開きます。 *ImagePrediction.cs* の先頭にある `System.Collections.Generic` と `System.Text` `using` の両方のステートメントを削除します。

既存のクラス定義を削除し、`ImagePrediction` クラスを含む次のコードを *ImagePrediction.cs* ファイルに追加します。

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` は、画像予測クラスであり、次のフィールドがあります。

* `Score` には、指定した画像分類の信頼度が含まれています。
* `PredictedLabelValue` には、予測された画像分類ラベルの値が含まれています。

`ImagePrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。 これには画像パスの `string` (`ImagePath`) が含まれます。 `Label` はモデルの再利用と再トレーニングに使用されます。 `PredictedLabelValue` は予測と評価の際に使用されます。 評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。

[MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の開始点で、`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。 これは Entity Framework における `DBContext` と概念的には同じです。

### <a name="initialize-variables-in-main"></a>Main で変数を初期化する

新しいインスタンスの `MLContext` を使用して `mlContext` 変数を初期化します。  `Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>既定のパラメーター用に構造体を作成する

Inception モデルには、渡す必要がある既定のパラメーターがいくつかあります。 次のコードを使用して、`Main()` メソッドの直後に、既定のパラメーター値をフレンドリ名にマップする構造体を作成します。

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>表示ユーティリティ メソッドを作成する

画像データとそれに関連する予測を複数回表示するので、画像と予測結果の表示を処理する表示ユーティリティ メソッドを作成します。

`DisplayResults()` メソッドは次のタスクを実行します。

* 予測された結果を表示する。

`InceptionSettings` 構造体の直後に、次のコードを使用して `DisplayResults()` メソッドを作成します。

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

`Transform()` メソッドによって、予測済みフィールドと共に `ImagePrediction` に `ImagePath` が設定されました。 ML.NET プロセスが進むにつれて、各コンポーネントに列が追加されます。これで、結果が簡単に表示されます。

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

2 つの画像分類メソッドのうち `DisplayResults()` メソッドを呼び出します。

### <a name="create-a-tsv-file-utility-method"></a>.tsv ファイル ユーティリティ メソッドを作成する

`ReadFromTsv()` メソッドは次のタスクを実行します。

* 画像データ `tags.tsv` ファイルを読み取ります。
* 画像ファイル名のファイル パスを追加します。
* ファイル データを IEnumerable `ImageData` オブジェクトに読み込みます。

`PairAndDisplayResults()` メソッドの直後に、次のコードを使用して `ReadFromTsv()` メソッドを作成します。

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

次のコードは、`tags.tsv` ファイルを解析して、ファイルパスを `ImagePath` プロパティの画像ファイル名に追加し、それと `Label` を `ImageData` オブジェクトに読み込みます。 `ReadFromTsv()` メソッドの最初の行として追加します。  予測結果を表示するには、完全修飾ファイル パスが必要です。

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
ML.NET には、次の 3 つの主要な概念があります。[データ](../resources/glossary.md#data)、[トランスフォーマー](../resources/glossary.md#transformer)、および[エスティメーター](../resources/glossary.md#estimator)です。

## <a name="reuse-and-tune-pre-trained-model"></a>トレーニング済みのモデルを再利用して調整する

`Main()` メソッドの次のコード行として、`ReuseAndTuneInceptionModel()` メソッドに次の呼び出しを追加します。

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` メソッドは次のタスクを実行します。

* データを読み込みます。
* データを抽出して変換します。
* TensorFlow モデルにスコアを付けます。
* モデルを調整 (再トレーニング) します。
* モデルの結果を表示します。
* モデルを評価します。
* モデルを返します。

`InceptionSettings` 構造体の直後、かつ `DisplayResults()` メソッドの直前に、次のコードを使用して `ReuseAndTuneInceptionModel()` メソッドを作成します。

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>データを読み込む

ML.NET 内のデータは、[IDataView クラス](xref:Microsoft.ML.IDataView)として表されます。 `IDataView` は、表形式のデータ (数値とテキスト) を表すための柔軟で効率的な方法です。 データはテキスト ファイルから、またはリアルタイムで (SQL データベースやログ ファイルなど) `IDataView` オブジェクトに読み込むことができます。

`MLContext.Data.LoadFromTextFile` ラッパーを使用して、データを読み込みます。 `ReuseAndTuneInceptionModel()` メソッドに次のコード行を追加します。

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>特徴を抽出してデータを変換する

データの前処理とクリーニングは、機械学習でデータ セットを効果的に使用する前に発生する重要なタスクです。  これらのモデル化タスクを行わずにデータを使用すると、誤解を招く結果が生じるおそれがあります。

機械学習アルゴリズムは、[特徴を生成した](../resources/glossary.md#feature)データを理解します。ディープ ニューラル ネットワークを扱うときは、画像をネットワークで想定されている形式に合わせる必要があります。 その形式は、[数値ベクトル](../resources/glossary.md#numerical-feature-vector)です。

トレーニングと評価の後、**Label** 列の値を使用して予測します。 トレーニング済みのモデルを使用しているので、[MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) メソッドを使用してフィールドを新しいモデルにマップします。 このメソッドは、`Label` を数値キー型 (`LabelTokey`) の列に変換し、それを新しいデータセット列として追加します。トレーナーも追加するので、これに `estimator` と名前を付けます。 次のコード行を追加します。

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

画像処理エスティメーターは、特徴の抽出のために事前にトレーニングされた[ディープ ニューラル ネットワーク (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) フィーチャライザーを使用します。 ディープ ニューラル ネットワークを扱うときは、画像を想定されているネットワーク形式に合わせます。 これが、画像データをモデルの想定されている形式に変換するために複数の画像変換を使用する理由です。

1. `LoadImages` 変換画像は、ビットマップ型としてメモリに読み込まれます。
2. トレーニング済みのモデルには定義された入力画像の幅と高さがあるので、`ResizeImages` 変換は画像のサイズを変更します。
3. `ExtractPixels` 変換は入力画像からピクセルを抽出し、それを数値ベクトルに変換します。

これらの画像変換を次のコード行として追加します。

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

`LoadTensorFlowModel` は、`TensorFlow` モデルを一度読み込んでから `ScoreTensorFlowModel` を使用して `TensorFlowEstimator` を作成する場合に便利なメソッドです。 `ScoreTensorFlowModel` は指定された出力 (`Inception model` の画像の特徴 `softmax2_pre_activation`) を抽出し、トレーニング済みの `TensorFlow` モデルを使用してデータセットにスコアを付けます。

`softmax2_pre_activation` は、画像がどのクラスに属するかを判断できるようにモデルを支援します。 `softmax2_pre_activation` は、画像の各カテゴリの確率を返します。また、確率をすべて合計すると、常に 1 になります。 次の例に示すように、画像は 1 つのカテゴリにのみ属すると想定しています。

| クラス         | 確率   |
| ------------- | ------------- |
| `Food`        |  0.001        |
| `Toy`         |  0.95         |
| `Appliance`   |  0.06         |

次のコード行を使用して、`TensorFlowTransform` を `estimator` に追加します。

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>トレーニング アルゴリズムを選択する

トレーニング アルゴリズムを追加するには、`mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` ラッパー メソッドを呼び出します。  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) は `estimator` に追加され、Inception 画像の特徴 (`softmax2_pre_activation`) および `Label` 入力パラメーターを受け入れて、履歴データから学習します。  次のコードを使用してトレーナーを追加します。

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

また、`predictedlabel` を `predictedlabelvalue` にマップする必要があります。

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` メソッドでは、データセットを変換して、トレーニングを適用することにより、モデルがトレーニングされます。 `ReuseAndTuneInceptionModel()` メソッドの次のコード行として以下を追加して、モデルをトレーニング データセットに適合させ、トレーニング済みモデルを返します。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドはテスト データセットの指定した複数の入力行に対して予測を行います。  次のコードを `ReuseAndTuneInceptionModel()` に追加して、`Training` データを変換します。

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

表示を簡単にするために、画像データと予測の `DataViews` を厳密に型指定された `IEnumerables` に変換します。 この処理を行うには、次のコードを使用して `MLContext.CreateEnumerable()` メソッドを使用します。

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

次のコードを追加して、`ReuseAndTuneInceptionModel()` メソッドの次の行としてデータと予測を表示します。

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

予測セットを作成したら、[Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) メソッドを呼び出します。

* モデルを評価します (予測値と実際のデータセット `Labels` を比較します)。

* モデルのパフォーマンス メトリックを返します。

`ReuseAndTuneInceptionModel()` メソッドに次のコード行を追加します。

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

画像分類では、次のメトリックが評価されます。

* `Log-loss` - 「[対数損失](../resources/glossary.md#log-loss)」を参照してください。 対数損失は可能な限り 1 に近づけます。

* `Per class Log-loss`。 クラスごとの対数損失は可能な限り 1 に近づけます。

次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 次の行としてトレーニング済みモデルを返すように次のコードを追加します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>読み込み済みのモデルを使用して画像を分類する

`Main` メソッドの次のコード行として、`ClassifyImages()` メソッドに次の呼び出しを追加します。

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` メソッドは次のタスクを実行します。

* .TSV ファイルを `IEnumerable` に読み込みます。
* テスト データに基づいて画像分類を予測します。

`ReuseAndTuneInceptionModel()` メソッドの直後、かつ `PairAndDisplayResults()` メソッドの直前に、次のコードを使用して `ClassifyImages()` メソッドを作成します。

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

まず `ReadFromTsv()` メソッドを呼び出して、各 `ImagePath` の完全修飾パスを含む `IEnumerable<ImageData>` クラスを作成します。 データと予測結果を組み合わせるには、そのファイル パスが必要です。 また、`IEnumerable<ImageData>` クラスを `IDataView` に変換して予測に使用する必要があります。 `ClassifyImages()` メソッドの次の 2 行として次のコード行を追加します。

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

トレーニング画像データを使用して以前に実行したように、渡されたモデルの [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを使用してテスト画像データのカテゴリを予測します。 予測のために次のコードを `ClassifyImages()` メソッドに追加し、ペアリングと表示のために `predictions` `IDataView` を `IEnumerable` に変換します。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

テスト画像データと予測を組み合わせて表示するには、次のコードを追加して、`ClassifyImages()` メソッドの次の行として以前に作成した `DisplayResults()` メソッドを呼び出します。

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>読み込み済みのモデルを使用して単一の画像を分類する

`Main` メソッドの次のコード行として、`ClassifySingleImage()` メソッドに次の呼び出しを追加します。

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` メソッドは次のタスクを実行します。

* `ImageData` インスタンスを読み込みます。
* テスト データに基づいて画像分類を予測します。

`ClassifyImages()` メソッドの直後、かつ `PairAndDisplayResults()` メソッドの直前に、次のコードを使用して `ClassifySingleImage()` メソッドを作成します。

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

まず 1 つの `ImagePath` の完全修飾パスと画像ファイル名を含む `ImageData` クラスを作成します。 `ClassifySingleImage()` メソッドの次の行として、次のコードを追加します。

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[PredictionEngine クラス](xref:Microsoft.ML.PredictionEngine%602)は、単一のデータ インスタンスに対して予測を実行する便利な API です。 [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 関数はデータの 1 つの列で予測を行います。 次のコードを `ClassifySingleImage()` に追加して、`imageData` を `PredictionEngine` に渡して画像カテゴリを予測します。

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

`ClassifySingleImage()` メソッドの次のコード行として予測結果を表示します。

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>結果

上記の手順を実行した後、コンソール アプリを実行します (Ctrl + F5 キー)。 結果は以下の出力のようになるはずです。  警告メッセージまたは処理中のメッセージが表示される場合がありますが、わかりやすくするため、これらのメッセージは結果から削除してあります。

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

おめでとうございます! これで、ML.NET でトレーニング済みの `TensorFlow` モデルを再利用して画像分類用の機械学習モデルを構築できました。

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) リポジトリで確認できます。

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
>
> * 問題を把握する
> * トレーニング済みのモデルを再利用して調整する
> * 読み込み済みのモデルを使用して画像を分類する

Machine Learning サンプルの GitHub リポジトリを確認し、拡張された画像分類サンプルを探索してください。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub リポジトリ](https://github.com/dotnet/machinelearning-samples/)

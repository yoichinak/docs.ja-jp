---
title: 'チュートリアル: センチメントの分析 - 二項分類'
description: このチュートリアルでは、Web サイトのコメントのセンチメントを分類して適切なアクションを実行する Razor Pages アプリケーションの作成方法について説明します。 この二項センチメント分類子では、Visual Studio の C# を使用します。
ms.date: 09/13/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6184e097daf4604173db9e2a34606e68eb0fdc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054274"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>チュートリアル: ML.NET モデル ビルダーを使用して Web アプリケーションで Web サイトのコメントのセンチメントを分析する

ここでは、Web アプリケーション内部でコメントからセンチメントをリアルタイムで分析する方法を学習します。

このチュートリアルでは、Web サイトのコメントのセンチメントをリアルタイムで分類する ASP.NET Core Razor Pages アプリケーションの作成方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * ASP.NET Core Razor Pages アプリケーションを作成する
> * データを準備して理解する
> * シナリオを選択する
> * データを読み込む
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

> [!NOTE]
> モデル ビルダーは現在のところ、プレビュー段階です。

このチュートリアルのソース コードは、[dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) リポジトリにあります。

## <a name="pre-requisites"></a>前提条件

前提条件の一覧とインストール手順は、[モデル ビルダーのインストール ガイド](../how-to-guides/install-model-builder.md)を参照してください。

## <a name="create-a-razor-pages-application"></a>Razor Pages アプリケーションを作成する

1. **ASP.NET Core Razor Pages アプリケーション**を作成します。

    1. Visual Studio を開いて、メニュー バーで **[ファイル]、[新規]、[プロジェクト]** の順に選択します。 
    1. [新しいプロジェクト] ダイアログで、 **[Visual C#]** ノードを選択し、 **[Web]** ノードを選択します。 
    1. 次に、 **[ASP.NET Core Web アプリケーション]** プロジェクト テンプレートを選択します。 
    1. **[名前]** テキスト ボックスに「SentimentRazor」と入力します。
    1. **[ソリューションのディレクトリの作成]** チェックボックスは、既定でオンになっています。 オンになっていない場合は、オンにします。 
    1. **[OK]** ボタンを選択します。
    1. さまざまな種類の ASP.NET Core プロジェクトが表示されているウィンドウで、 **[Web アプリケーション]** を選択し、 **[OK]** ボタンを選択します。

## <a name="prepare-and-understand-the-data"></a>データを準備して理解する

[Wikipedia detox データセット](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)をダウンロードします。 Web ページが開いたら、そのページを右クリックして、 **[名前を付けて保存]** を選択し、コンピューター上の任意の場所にファイルを保存します。 

*wikipedia-detox-250-line-data.tsv* データセットの各行は、ユーザーが Wikipedia に残した異なるレビューを表します。 最初の列は、テキストのセンチメントを表し (0 は無害、1 は有害)、2 番目の列はユーザーが残したコメントを表します。 列はタブで区切られます。 データは次のようになります。

| Sentiment | SentimentText |
| :---: | :---: |
1 | ==無礼== なんて無礼な。Carl のその画像をアップロードし戻しておくのが身のためだぞ。
1 | == OK! ==  それなら、WILD ONES WIKI をぶっ壊す!!!
0 | この情報がお役に立てば幸いです。

## <a name="choose-a-scenario"></a>シナリオを選択する

![](./media/sentiment-analysis-model-builder/model-builder-screen.png)

モデルをトレーニングするには、モデル ビルダーによって提供される機械学習シナリオの一覧から選択する必要があります。 

1. **ソリューション エクスプローラー**で、 *[SentimentRazor]* プロジェクトを右クリックし、 **[追加]**  >  **[機械学習]** の順に選択します。
1. このサンプルのシナリオは、センチメント分析です。 モデル ビルダー ツールの "*シナリオ*" の手順で、 **[センチメント分析]** シナリオを選択します。

## <a name="load-the-data"></a>データを読み込む

モデル ビルダーは、SQL Server データベースか、`csv` 形式または `tsv` 形式のローカル ファイルという 2 つのソースからデータを受け取ります。

1. モデル ビルダー ツールのデータの手順で、データ ソースのドロップダウンから **[ファイル]** を選択します。
1. **[ファイルの選択]** テキスト ボックスの横にあるボタンを選択し、エクスプローラーを使用してファイルを参照し、*wikipedia-detox-250-line-data.tsv* ファイルを選択します。
1. **[Label or Column to Predict]\(予測するラベルまたは列\)** ドロップダウンで **[センチメント]** を選択します。
1. **[トレーニング]** リンクを選択して、モデル ビルダー ツールの次の手順に進みます。

## <a name="train-the-model"></a>モデルをトレーニングする

このチュートリアルで、価格予測モデルのトレーニングに使用する機械学習のタスクは、二項分類です。 モデルのトレーニング プロセス中、モデル ビルダーは、データセットに対して最もパフォーマンスの優れたモデルを見つけるために、さまざまな二項分類アルゴリズムと設定を使用して個々のモデルをトレーニングします。

モデルのトレーニングに必要な時間は、データの量に比例します。 モデル ビルダーにより、 **[Time to train (seconds)]\(トレーニング時間 (秒)\)** の既定値が、データ ソースのサイズに基づいて自動的に選択されます。 

1. モデル ビルダーによって **[トレーニング時間 (秒)]** の値が 10 秒に設定しますが、30 秒に増加します。 トレーニング時間が長いほど、モデル ビルダーは最良のモデルの検索の中で、より多くのアルゴリズムやパラメーターの組み合わせを調べることができます。
1. **[Start Training]\(トレーニング開始\)** を選択します。

    トレーニング プロセスを通して、進捗データがトレーニングの手順の `Progress` セクションに表示されます。

    - 状態には、トレーニング プロセスの完了ステータスが表示されます。
    - [Best accuracy]\(最良の精度\) には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのモデルの精度が表示されます。 精度が高くなるほど、テスト データでモデルが正確に予測されたことになります。
    - [Best algorithm]\(最良のアルゴリズム\) には、これまでにモデル ビルダーで見つかった最良のパフォーマンスのアルゴリズムの名前が表示されます。
    - [Last algorithm]\(最後のアルゴリズム\) には、モデル ビルダーがモデルのトレーニングに最近使用したアルゴリズムの名前が表示されます。

1. トレーニングが完了したら、 **[評価]** リンクを選択して、次の手順に進みます。

## <a name="evaluate-the-model"></a>モデルを評価する

トレーニングの手順の結果が、最良のパフォーマンスだった 1 つのモデルになります。 モデル ビルダー ツールの評価の手順の出力セクションには、 **[Best Model]\(最良のモデル\)** エントリの最良のパフォーマンスのモデルで使用されたアルゴリズムと、 **[Best Model Quality (RSquared)]\(最良のモデル品質 (RSquared)\)** のメトリックが含まれます。 また、概要テーブルには上位 5 つのモデルとそのメトリックが含まれています。

精度のメトリックに不満がある場合、モデルのトレーニング時間を増やすか、さらに多くのデータを使用すると、モデルの精度を簡単に高めることができます。 それ以外の場合、 **[コード]** リンクを選択して、モデル ビルダー ツールの最後の手順に進みます。

## <a name="add-the-code-to-make-predictions"></a>予測を行うコードを追加する

トレーニング プロセスの結果として 2 つのプロジェクトが作成されます。

### <a name="reference-the-trained-model"></a>トレーニング済みモデルの参照

1. モデル ビルダー ツールの "*コード*" の手順で、 **[プロジェクトの追加]** を選択して、自動生成されたプロジェクトをソリューションに追加します。

    **ソリューション エクスプローラー**に次のプロジェクトが表示されます。

    - *SentimentRazorML.ConsoleApp*: モデル トレーニングと予測コードが含まれる .NET Core コンソール アプリケーション。
    - *SentimentRazorML.Model*: 入出力モデル データのスキーマを定義するデータ モデルと、トレーニング中にパフォーマンスが最も良かったモデルの永続化バージョンが含まれる .NET Standard クラス ライブラリ。

    このチュートリアルでは、コンソールではなく *SentimentRazor* Web アプリケーションで予測を行うため、*SentimentRazorML.Model* プロジェクトのみを使用します。 *SentimentRazorML.ConsoleApp* はスコアリングに使用されませんが、これは、後で新しいデータを使用してモデルを再トレーニングするために使用できます。 ただし、再トレーニングはこのチュートリアルの範囲外です。

1. トレーニング済みのモデルを Razor Pages アプリケーション内で使用するには、*SentimentRazorML.Model* プロジェクトへの参照を追加します。

    1. **[SentimentRazor]** プロジェクトを右クリックします。 
    1. **[追加]、[参照]** の順に選択します。 
    1. **[プロジェクト]、[ソリューション]** ノードの順に選択して、リストで **[SentimentRazorML.Model]** プロジェクトのチェックボックスをオンにします。
    1. **[OK]** を選択します。

### <a name="configure-the-predictionengine-pool"></a>PredictionEngine プールの構成

1つの予測を行うのに [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を使用します。 お使いのアプリケーションで [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を使用するには、必要に応じてそれを作成する必要があります。 その場合、ベストプラクティスとして、依存関係を挿入することを検討します。

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。 パフォーマンスとスレッドセーフを改善するために、`PredictionEnginePool` サービスを使用します。これにより、アプリケーションで使用される `PredictionEngine` オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。 詳しくは、[ASP.NET Core での `PredictionEngine` オブジェクトプールの作成と使用](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)のブログ投稿で確認してください。 

1. *Microsoft.Extensions.ML* NuGet パッケージをインストールします。

    1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。 
    1. [パッケージ ソース] として [nuget.org] を選択します。 
    1. **[参照]** タブを選択して、「**Microsoft.Extensions.ML**」を検索します。 
    1. リストでパッケージを選択して、 **[インストール]** ボタンを選択します。 
    1. **[変更のプレビュー]** ダイアログで **[OK]** ボタンを選択します。
    1. 一覧表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスへの同意]** ダイアログで **[同意する]** ボタンを選択します。 

1. *SentimentRazor* プロジェクトで *Startup.cs* ファイルを開きます。
1. *Microsoft.Extensions.ML* NuGet パッケージと *SentimentRazorML.Model* プロジェクトを参照する次の using ステートメントを追加します。

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]        

1. トレーニング済みのモデル ファイルの場所を格納するグローバル変数を作成します。

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. モデル ファイルは、アプリケーションのアセンブリ ファイルと共にビルド ディレクトリに格納されます。 アクセスしやすいように、`Configure` メソッドの後に `GetAbsolutePath` というヘルパー メソッドを作成します。

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. `Startup` クラス コンストラクターで `GetAbsolutePath` メソッドを使用して、`_modelPath` を設定します。

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. `ConfigureServices` メソッドでアプリケーションの `PredictionEnginePool` を構成します。

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a>センチメント分析ハンドラーの作成

予測は、アプリケーションのメイン ページ内で行われます。 このため、ユーザー入力を受け取り、`PredictionEnginePool` を使用して予測を返すメソッドを追加する必要があります。

1. *Pages* ディレクトリにある *Index.cshtml.cs* ファイルを開いて、次の using ステートメントを追加します。

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    `Startup` クラスで構成された `PredictionEnginePool` を使用するには、使用するモデルのコンストラクターにそれを挿入する必要があります。 

1. `IndexModel` クラス内で `PredictionEnginePool` を参照する変数を追加します。

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. `IndexModel` クラスでコンストラクターを作成し、それに `PredictionEnginePool` サービスを挿入します。

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. `PredictionEnginePool` を使用して、Web ページから受け取ったユーザー入力から予測を行うメソッド ハンドラーを作成します。

    1. `OnGet` メソッドの下に、`OnGetAnalyzeSentiment` という新しいメソッドを作成します。

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. ユーザーからの入力が空白または null の場合、`OnGetAnalyzeSentiment` メソッド内で、"*ニュートラル*" センチメントを返します。

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)] 
    
    1. 入力が有効な場合は、`ModelInput` の新しいインスタンスを作成します。 

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)] 

    1. `PredictionEnginePool` を使用してセンチメントを予測します。

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)] 

    1. 次のコードを使用して、予測された `bool` 値を有害または無害に変換します。

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. 最後に、センチメントを Web ページに返します。

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a>Web ページの構成

`OnGetAnalyzeSentiment` によって返される結果は、`Index` Web ページに動的に表示されます。

1. *Pages* ディレクトリ内にある *Index.cshtm* を開いて、その内容を次のコードに置き換えます。 

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. 次に、*wwwroot\css* ディレクトリ内の *site.css* ページの末尾に css スタイル コードを追加します。

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. その後、入力を Web ページから `OnGetAnalyzeSentiment` ハンドラーに送信するコードを追加します。

    1. *wwwroot\js* ディレクトリ内にある *site.js* ファイルで、`getSentiment` という関数を作成し、`OnGetAnalyzeSentiment` ハンドラーへのユーザー入力を使用して GET HTTP 要求を作成します。

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. その下に、`updateMarker` という別の関数を追加して、センチメントが予測されると、Web ページ上のマーカーの位置を動的に更新します。

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. `updateSentiment`というイベント ハンドラー関数を作成し、ユーザーから入力を取得し、`getSentiment` 関数を使用してそれを `OnGetAnalyzeSentiment` 関数に送信し、`updateMarker` 関数でマーカーを更新します。

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. 最後に、イベント ハンドラーを登録し、`id=Message` 属性を使ってそれを `textarea`要素にバインドします。

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>アプリケーションの実行

アプリケーションがセットアップされたので、アプリケーションを実行します。アプリケーションはブラウザー内で起動します。

アプリケーションが起動したら、テキスト領域に「*Model Builder is cool!* 」 と入力します。 表示される予測済みセンチメントは、「*無害*」になります。

![](./media/sentiment-analysis-model-builder/web-app.png)

別のソリューション内で後でモデル ビルダーによって生成されたプロジェクトを参照する必要がある場合、それらは、`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` ディレクトリ内にあります。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * ASP.NET Core Razor Pages アプリケーションを作成する
> * データを準備して理解する
> * シナリオを選択する
> * データを読み込む
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

### <a name="additional-resources"></a>その他のリソース

このチュートリアルで説明しているトピックについて詳しくは、次のリソースを参照してください。

- [モデル ビルダーのシナリオ](../automate-training-with-model-builder.md#scenarios)
- [二項分類](../resources/glossary.md#binary-classification)
- [二項分類モデル メトリック](../resources/metrics.md#metrics-for-binary-classification)
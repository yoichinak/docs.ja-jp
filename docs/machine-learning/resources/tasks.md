---
title: 機械学習のタスク - ML.NET
description: ML.NET でサポートされる機械学習のさまざまなタスクと、それらに関連するタスクについて説明します。
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613162"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET での機械学習のタスク

機械学習モデルを構築する場合は、データを使用して実現したい目的を最初に定義する必要があります。 これによって、状況に適した機械学習のタスクを選択できます。 選択可能な機械学習のさまざまなタスクといくつかの一般的なユース ケースについて以下で説明します。

どのタスクが自分のシナリオにとって適切かを決定したら、モデルをトレーニングするのに最適なアルゴリズムを選択する必要があります。 使用可能なアルゴリズムは、タスクごとのセクションに一覧表示されています。

## <a name="binary-classification"></a>二項分類

データのインスタンスが 2 つのうちのどちらのクラス (カテゴリ) に属しているかを予測するために使用する[教師あり機械学習](glossary.md#supervised-machine-learning)タスクです。 分類アルゴリズムの入力はラベル付けされた一連のサンプルであり、各ラベルは整数 0 または 1 です。 二項分類アルゴリズムの出力は分類子であり、ラベルのない新しいインスタンスのクラスを予測するために使用できます。 二項分類のシナリオの例を次に示します。

* [Twitter コメントのセンチメントが "肯定的" か "否定的" かを理解する](../tutorials/sentiment-analysis.md)。
* 患者が特定の病気であるかどうかを診断する。
* 電子メールを "スパム" としてマークするかどうかを決定する。
* 写真に犬または果物が含まれているかどうかを決定する。

詳しくは、Wikipedia の[二項分類](https://en.wikipedia.org/wiki/Binary_classification)の記事を参照してください。

### <a name="binary-classification-training-algorithms"></a>二項分類トレーニング アルゴリズム

次のアルゴリズムを使用して二項分類モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a>多クラス分類

データのインスタンスのクラス (カテゴリ) を予測するために使用する[教師あり機械学習](glossary.md#supervised-machine-learning)タスクです。 分類アルゴリズムの入力は、ラベル付けされた一連のサンプルです。 各ラベルは、通常、テキストとして開始されます。 その後、TermTransform を経由してキー (数値) 型に変換されます。 分類アルゴリズムの出力は分類子であり、ラベルのない新しいインスタンスのクラスを予測するために使用できます。 多クラス分類のシナリオの例を次に示します。

* "シベリアン ハスキー"、"ゴールデン レトリバー"、"プードル" などの犬種を特定する。
* 映画のレビューが "肯定的"、"中立"、"否定的" のどれかを理解する。
* ホテルのレビューを "立地"、"価格"、"清潔さ" などに分類する。

詳しくは、Wikipedia の[多クラス分類](https://en.wikipedia.org/wiki/Multiclass_classification)の記事を参照してください。

>[!NOTE]
>一対全では、多クラス データセットに対して機能するように[二項分類学習器](#binary-classification)がアップグレードされます。 詳細については、[Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)) を参照してください。

### <a name="multiclass-classification-training-algorithms"></a>多クラス分類のトレーニング アルゴリズム

次のトレーニング アルゴリズムを使用して多クラス分類モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a>回帰

関連する一連の特徴からラベルの値を予測するために使用する[教師あり機械学習](glossary.md#supervised-machine-learning)タスクです。 ラベルには任意の実際の値を使用できます。分類タスクのように有限の値のセットから取得するものではありません。 回帰アルゴリズムでは、ラベルに関連する特徴におけるラベルの依存関係をモデル化して、特徴の値が変化するとラベルがどのように変化するかを判断します。 回帰アルゴリズムの入力は、既知の値のラベルが付いた一連のサンプルです。 回帰アルゴリズムの出力は関数であり、新しい入力特徴のセットのラベル値を予測するために使用できます。 回帰のシナリオの例を次に示します。

* 住宅の属性 (寝室数、立地、規模など) に基づいて住宅価格を予測する。
* 履歴データと現在の市場動向に基づいて将来の株価を予測する。
* 広告予算に基づいて製品の売り上げを予測する。

### <a name="regression-training-algorithms"></a>回帰トレーニング アルゴリズム

次のアルゴリズムを使用して回帰モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a>クラスタリング

データのインスタンスを、同様の特性を持つクラスタにグループ化するために使用する[教師なし機械学習](glossary.md#unsupervised-machine-learning)タスクです。 また、閲覧や単純な観測では論理的に導き出せない可能性のあるデータ セットにおける関係をクラスタリングを使用して識別することもできます。 クラスタリング アルゴリズムの入力と出力は、選択した方法によって異なります。 分布、重心、結合性、または密度に基づくアプローチを利用できます。 現在、ML.NET では、K 平均法によるクラスタリングを使用した重心に基づくアプローチをサポートしています。 クラスタリングのシナリオの例を次に示します。

* ホテル選択の傾向と特性に基づいてホテルの宿泊客のセグメントを理解する。
* 対象を絞った広告キャンペーンの構築に役立つ顧客セグメントと統計データを特定する。
* 製造メトリックに基づいてインベントリを分類する。

### <a name="clustering-training-algorithms"></a>クラスタリング トレーニング アルゴリズム

次のアルゴリズムを使用してクラスタリング モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a>異常検出

このタスクでは、主成分分析 (PCA) を使用して、異常検出モデルを作成します。 PCA に基づく異常分析は、有効なトランザクションなどの 1 つのクラスからトレーニング データを簡単に取得できるが、対象とする異常の十分なサンプルを取得するのが難しいシナリオでモデルを構築するのに役立ちます。

機械学習における確立された手法である PCA は、データの内部構造を明らかにし、データの分散を説明するために、調査データ分析で頻繁に使用されます。 PCA は、複数の変数が含まれるデータを分析することで機能します。 変数の相関を探し、結果内の差異を最も捕らえている値の合成を決定します。 これらの合成されたフィーチャー値を使用して、主成分と呼ばれる、よりコンパクトなフィーチャー空間が作成されます。

異常検出には、機械学習における多くの重要なタスクが含まれています。

* 不正な可能性があるトランザクションを識別します。
* ネットワークへの侵入が発生していることを示唆するパターンを学習します。
* 患者の異常なクラスターを検出します。
* システムに入力された値をチェックします。

異常とは定義上はまれに発生するイベントであるため、モデル化するために使用する代表的なデータ サンプルを収集するのは困難です。 このカテゴリに含まれるアルゴリズムは、不均衡なデータセットの使用によるモデルの構築とトレーニングという主要な課題に対処するように特別に設計されています。

### <a name="anomaly-detection-training-algorithms"></a>異常検出トレーニング アルゴリズム

次のアルゴリズムを使用して異常検出モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a>ランキング

ランキング タスクでは、ラベル付きのサンプルのセットからランカーが構築されます。 この例のセットは、特定の条件を使用してスコア付けできるインスタンス グループで構成されています。 順位付けのラベルは、インスタンスごとに {0、1、2、3, 4} です。  各インスタンスのスコアが不明である新しいインスタンス グループをランク付けするように、ランカーがトレーニングされます。 ML.NET のランキング学習器は、[機械が学習したランキング](https://en.wikipedia.org/wiki/Learning_to_rank)に基づいています。

### <a name="ranking-training-algorithms"></a>ランキング トレーニング アルゴリズム

次のアルゴリズムを使ってランキング モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a>推奨事項

レコメンデーション タスクによって、推奨される製品やサービスの一覧を作成できます。 ML.NET では、カタログ内に製品のレーティングの履歴データがある場合は、レコメンデーション用の[協調フィルタリング](https://en.wikipedia.org/wiki/Collaborative_filtering) アルゴリズムである[行列因子分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) が使用されます。 たとえば、ユーザーによる映画の採点の履歴データがあるときに、そのユーザーが次に見たいと思う映画を推薦できます。

### <a name="recommendation-training-algorithms"></a>レコメンデーション トレーニング アルゴリズム

次のアルゴリズムを使ってレコメンデーション モデルをトレーニングすることができます。

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

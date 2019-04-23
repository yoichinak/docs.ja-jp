---
title: .NET の機械学習に関するハウツー ガイド - ML.NET
description: カスタム AI ソリューションの作成と、.NET アプリケーションへの Machine Learning 統合を支援するための、特定のタスクを実行する方法について説明します。
ms.custom: seodec18
ms.date: 03/01/2019
ms.openlocfilehash: c8d1258629f777cd8bced47e4b956c9cf100a682
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427584"
---
# <a name="net-machine-learning-how-to-guides---mlnet"></a>.NET の機械学習に関するハウツー ガイド - ML.NET

ML.NET ガイドの方法に関するセクションには、よく寄せられる質問に対する簡単な回答が記載されています。 場合によっては、見つけやすいように、記事が複数のセクションで表示されることもあります。

## <a name="load-the-data"></a>データを読み込む

* [機械学習の処理のために多数の列を含むデータを CSV ファイルから読み込みます。](load-data-from-mult-column-csv-ml-net.md)

* [機械学習の処理のために複数ファイルからデータを読み込みます。](load-data-from-multiple-files-ml-net.md)

* [機械学習の処理のためにテキスト ファイルからデータを読み込みます。](load-data-from-text-file-ml-net.md)

### <a name="prepare-the-data"></a>データを準備する

* [データ処理で使うためにノーマライザーでトレーニング データを前処理します。](normalizers-preprocess-data-ml-net.md)

## <a name="train-the-model"></a>モデルをトレーニングする

* [テキスト ファイルではないデータを使って機械学習モデルをトレーニングします。](load-non-file-training-data-ml-net.md)

* [クロス検証を使って機械学習モデルをトレーニングします。](train-cross-validation-ml-net.md)

* [ML.NET を使って値を予測する回帰モデルをトレーニングします。](train-regression-model-ml-net.md)

### <a name="evaluate-the-model-quality"></a>モデルの品質を評価する

* [メトリックを計算してモデルの品質を評価します。](verify-model-quality-ml-net.md)

### <a name="model-explainability"></a>モデルの説明可能性

* [Permutation Feature Importance を使ってモデルの特徴の重要度を判断します。](determine-global-feature-importance-in-model.md)

* [モデルの説明可能性のために一般化加法モデルと形状関数を使います。](use-gams-for-model-explainability.md)

### <a name="feature-engineering"></a>特徴エンジニアリング

* [カテゴリ データに対するモデル トレーニングに特徴エンジニアリングを適用します。](train-model-categorical-ml-net.md)

* [ML.NET を使ってテキスト データに対するモデル トレーニングに特徴エンジニアリングを適用します。](train-model-textual-ml-net.md)

## <a name="run"></a>実行

* [ML.NET パイプライン処理中の中間データ値を検査します。](inspect-intermediate-data-ml-net.md)

* [トレーニング済みの機械学習モデルをアプリで運用化します。](consuming-model-ml-net.md)

* [PredictionFunction を使って一度に 1 つの予測を行います。](single-predict-model-ml-net.md)

## <a name="probabilistic-infernet"></a>確率論的 (Infer.NET)

* [Infer.NET と確率論的プログラミングでゲーム対戦リスト アプリを作成します。](matchup-app-infer-net.md)
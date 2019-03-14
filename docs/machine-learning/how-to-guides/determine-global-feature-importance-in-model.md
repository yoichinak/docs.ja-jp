---
title: ML.NET の Permutation Feature Importance を使ってモデルの特徴の重要度を判断する
description: ML.NET の Permutation Feature Importance を使ってモデルの特徴の重要度を理解する
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b0457bc07168579403e5a00383864c5612e1d17f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675551"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a>ML.NET の Permutation Feature Importance を使ってモデルの特徴の重要度を判断する

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

機械学習モデルを作成するとき、予測を作成するだけでは十分でないことがよくあります。 多くの場合、機械学習の開発者、意思決定者、およびモデルによって影響を受ける担当者は、機械学習モデルがどのように決定を行うか、またそのパフォーマンスにどの特徴が関係するかを理解する必要があります。 `Permutation Feature Importance` (PFI) はモデルについて説明するツールであり、機械学習開発者がモデルの特徴の重要性をよく理解できるように社内で使用されています。

PFI は、トレーニングされた機械学習モデルの**グローバルな特徴の重要性**を判断する技術であり、Breiman 著[「Random Forests」論文、セクション 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) から刺激を受けたものです。 PFI では、特徴の重要性を測定するために、"特徴の値がランダム* 値に設定されたら、どのような影響がモデルに及ぼされるか?" と質問します。 PFI 方法のメリットは、モデルに依存しない点です。評価することができるすべてのモデルに使用できます。また、特徴の重要性を計算するために、トレーニング セットだけでなく任意のデータセットを使用できます。 PFI を使用すると、このグラフのように特徴の重要性を示すことができます。

![Permutation Feature Importance グラフ](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model.LastTransformer, model.Transform(data), "MedianHomeValue");

// Get the feature names from the training set
var featureNames =
    data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Write out the feature names and their importance to the model's Mean R-squared value
for (int i = 0; i < featureNames.Length;i++)
{
    Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].RSquared.Mean:G4}");
}
```

モデルの特徴の重要性を分析する PFI の使用例については、[dotnet/machinelearning GitHub リポジトリ](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance)をご覧ください。

/* 厳密にはランダムではありませんが、サンプルのセット全体で順序が変更されます。

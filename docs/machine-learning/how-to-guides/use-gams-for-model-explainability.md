---
title: モデルの説明可能性のために一般化加法モデルと形状関数を使用する
description: ML.NET でモデルの説明可能性のために一般化加法モデルと形状関数を使う
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: ef56f737a2ad0cba616e32229ac3a395146fb6d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662131"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>ML.NET でモデルの説明可能性のために一般化加法モデルと形状関数を使う

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

機械学習モデルを作成するとき、予測を作成するだけでは十分でないことがよくあります。 多くの場合、機械学習の開発者、意思決定者、およびモデルによって影響を受ける担当者は、機械学習モデルがどのように決定を行うか、またそのパフォーマンスにどの特徴が関係するかを理解する必要があります。 **一般化加法モデル (GAM)** は、モデルについて説明するために社内で使用され、他の人が簡単に解釈できる高性能モデルを機械学習の開発者が作成する際に役立ちます。

GAM は、線形モデルである**解釈可能モデル**の一種です。ここでは、用語は、1 つの変数の "形状関数" と呼ばれる非線形関数です。 線形モデルとして、これらは簡単に解釈されます。ただし、モデルは 1 つの重みではなく特徴の関数を学習するため、1 つの線形モデルよりも複雑な関係をモデル化することができます。 結果として得られる GAM 予測器は、トレーニング セットで平均予測を表す用語と、平均予測からの偏差を表す形状関数をインターセプトします。 形状関数を調べると、さまざまな値の特徴に対するモデルのレスポンスを目視で確認でき、コード例の最後で作成される次のグラフのように視覚化できます。 ML.NET の GAM トレーナーは、ノンパラメトリック形状関数を学習するように、浅い勾配ブースティング木 (たとえば切り株) を使って実装されます。これは、Lou、Caruana、Gehrke 共著の「[Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf)」(分類および回帰の明瞭なモデル) で説明されている方法に基づいています。

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![一般化加法モデルの形状関数のグラフ](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

GAM モデルのトレーニングや、結果の検査と解釈の方法の例については、[dotnet/machinelearning GitHub リポジトリ](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs)をご覧ください。

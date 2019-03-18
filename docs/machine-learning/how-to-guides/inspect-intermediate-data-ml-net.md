---
title: ML.NET パイプライン処理中の中間データ値を検査する
description: ML.NET 機械学習パイプラインの処理中に実際の中間データ値を検査する方法について説明します。
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 362cb9351c3cb77b6aa67d59154854e882869ad9
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843417"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a>ML.NET パイプライン処理中の中間データ値を検査する

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

実験中に、特定の時点のデータ処理結果を観察し、検証することが必要になる場合があります。 これは簡単ではありません。なぜなら、ML.NET の操作は、データの 'promise' であるオブジェクトの遅延構築だからです。

`GetColumn<T>` 拡張メソッドを使用すると、中間データを検査できます。 1 つのデータ列の内容が `IEnumerable` として返されます。

`GetColumn<T>` 拡張メソッドを使用する方法を次の例に示します。

[ファイルの例](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):

<!-- markdownlint-disable MD010 -->
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```
<!-- markdownlint-enable MD010 -->

このクラスは次のように定義されています。

```csharp
public class InspectedRow
{
    [LoadColumn(0)]
    public bool IsOver50K { get; set; }
    [LoadColumn(1)]
    public string WorkClass { get; set; }
    [LoadColumn(2)]
    public string Education { get; set; }
    [LoadColumn(3)]
    public string MaritalStatus { get; set; }
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Read the data into a data view.
var data = mlContext.Data.ReadFromTextFile<InspectedRow>(dataPath, hasHeader: true);

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "WorkClass", "Education", "MaritalStatus");

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns =
    transformedData
        .GetColumn<string[]>(mlContext, "AllFeatures")
        .Take(20)
        .ToArray();
```

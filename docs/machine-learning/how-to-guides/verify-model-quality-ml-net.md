---
title: 機械学習モデルの品質を評価するメトリックを計算する
description: ML.NET を使用して機械学習モデルの品質を評価および検証するメトリックを計算する方法について説明します。
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 529003913b166c966e131b006800f944096605b7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855565"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>機械学習モデルの品質を評価するメトリックを計算する 

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

モデルをトレーニングした後はどのように品質を評価すればよいでしょうか。 各機械学習タスクは品質評価用のメトリックを公開しています。

次の例のように、タスクの対応する 'コンテキスト' を使用してモデルを評価することができます。

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```

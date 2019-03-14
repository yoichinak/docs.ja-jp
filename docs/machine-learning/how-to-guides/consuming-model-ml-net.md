---
title: トレーニング済みの機械学習モデルをアプリで運用化する - ML.NET
description: ML.NET を使用して、アプリケーションでトレーニングおよび評価された機械学習モデルを使用する方法について説明します
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675135"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>トレーニング済みの機械学習モデルをアプリで運用化する - ML.NET

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

モデルのメトリックに満足したら、次はモデルを "運用化" します。 構築した `model` オブジェクトは、トレーニング中に "学習" したものと同じ手順を適用して、さまざまな環境で使用、永続化、および再利用することができます。

モデルをファイルに保存し、(場合によっては別のコンテキストで) 再度読み込むには、次の例を使用します。

```csharp
using (var stream = File.Create(modelPath))
{
    // Saving and loading happens to 'dynamic' models.
    mlContext.Model.Save(model, stream);
}

// Potentially, the lines below can be in a different process altogether.

// When you load the model, it's a transformer.
ITransformer loadedModel;
using (var stream = File.OpenRead(modelPath))
    loadedModel = mlContext.Model.Load(stream);
```

---
title: ML.NET による自動機械学習
description: 自動モデル選択およびトレーニングの概要
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: da2d764e678debc78a25faeb8e48facb44fc4021
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929420"
---
# <a name="automated-machine-learning-with-mlnet"></a>ML.NET による自動機械学習

自動機械学習は、自動モデル選択およびトレーニングを実行する ML.NET の機能です。 機械学習タスクを指定し、データセットを指定すると、自動 ML によって最適なメトリックのモデルが選択されます。 出力内容は次のとおりです。

- 予測アプリケーションに読み込むことができるモデル ファイル
- 予測を行うアプリケーション コード
- (モデルを理解するために) 特徴の選択とモデルのトレーニングに使用されるソース コード

> [!NOTE]
> この機能は現在プレビュー段階であり、資料は変更される場合があります。 

現在、自動 ML は二項分類、多クラス分類、回帰の機械学習[タスク](resources/tasks.md)に限定されています。 他の機械学習タスクが今後のリリースでサポートされる予定です。

自動 ML を使用する方法は 3 つあります。

1. [ML.NET モデル ビルダー](automate-training-with-model-builder.md) でグラフィカル ユーザー インターフェイスを使用する
1. コマンド ライン上で [ML.NET CLI](automate-training-with-cli.md) を使用する
1. アプリケーションを介して[自動 ML API](how-to-guides/how-to-use-the-automl-api.md) を使用する

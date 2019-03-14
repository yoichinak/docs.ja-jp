---
title: Infer.NET と確率論的プログラミングでゲーム対戦リスト アプリを作成する
description: 確率論的プログラミングと Infer.NET を使用して、TrueSkill の簡易バージョンに基づいたゲーム対戦リスト アプリについて紹介します。
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 06538ec9de26f5aeabe474fbcae69f0a313c8d32
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679135"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Infer.NET と確率論的プログラミングでゲーム対戦リスト アプリを作成する

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

ここで説明する方法と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

このハウツー ガイドでは、Infer.NET を使用した確率論的プログラミングについて説明します。 確率論的プログラミングは、カスタム モデルがコンピューター プログラムとして表現される機械学習アプローチです。 ドメインの知識をモデルに組み込み、機械学習システムから解釈可能にすることができます。 また、新しいデータを取得したときの学習プロセスであるオンライン推論もサポートしています。 Infer.NET は、Microsoft で Azure、Xbox、Bing のさまざまな製品で使用されています。

## <a name="what-is-probabilistic-programming"></a>確率論的プログラミングとは

確率論的プログラミングを使用すると、現実世界のプロセスの統計モデルを作成することができます。

## <a name="prerequisites"></a>必須コンポーネント

- ローカルの開発環境の設定

  このハウツー ガイドでは、開発用に使用できるマシンがあることを想定しています。 Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するチュートリアルに記載されています。

## <a name="create-your-app"></a>アプリを作成する

1. コマンド プロンプトを開き、次のコマンドを実行します。

```console
dotnet new console -o myApp
cd myApp
```

`dotnet` コマンドで、種類が `console` の `new` アプリケーションを作成します。 `-o` パラメーターで、アプリが格納されるディレクトリ `myApp` を作成し、必要なファイルを指定します。 `cd myApp` コマンドで、新しく作成されたアプリ ディレクトリに移動します。

## <a name="install-infernet-package"></a>Infer.NET パッケージのインストール

Infer.NET を使用するには、`Microsoft.ML.Probabilistic.Compiler` パッケージをインストールする必要があります。 コマンド プロンプトで次のコマンドを実行します。

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>モデルを設計する

このサンプルでは、オフィス内でプレイされる卓球またはフーズボールの試合を使用します。 参加者と各試合の結果があります。  このデータからプレーヤーのスキルを推論します。 各プレーヤーには正規分布の潜在的なスキルがあり、各試合の成績はこのスキルにノイズを加えたバージョンと仮定します。 このデータによって、勝者の成績が敗者の成績よりも高くなるように制限します。 これは、一般的な [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) モデルの簡易バージョンです。TrueSkill モデルは、チーム、引き分けなどの拡張機能もサポートしています。 このモデルの[高度なバージョン](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/)は、ベストセラーのゲーム タイトルである Halo と Gears of War のマッチメイキングに使用されています。

推定されたプレーヤーのスキルをその分散 (そのスキルの不確実性の尺度) と共に列挙する必要があります。

*ゲーム結果のサンプル データ*

ゲーム |勝者 | 敗者
---------|----------|---------
 1 | プレーヤー 0 | プレーヤー 1
 2 | プレーヤー 0 | プレーヤー 3
 3 | プレーヤー 0 | プレーヤー 4
 4 | プレーヤー 1 | プレーヤー 2
 5 | プレーヤー 3 | プレーヤー 1
 6 | プレーヤー 4 | プレーヤー 2

サンプル データを詳しく見ると、プレーヤー 3 とプレーヤー 4 のどちらも 1 勝 1 敗であることがわかります。 確率論的プログラミングを使用するとランキングがどのようになるかを見てみましょう。 オフィスの対戦リストであっても開発者にとってはゼロベースなので、プレーヤーがゼロである点にも注意してください。

## <a name="write-some-code"></a>コードを記述する

モデルを設計したら、次は Infer.NET モデル API を使用して確率論的プログラムとして表現します。 使い慣れたテキスト エディターで `Program.cs` を開き、すべての内容を次のコードに置き換えます。

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a>アプリの実行

コマンド プロンプトで次のコマンドを実行します。

```console
dotnet run
```

## <a name="results"></a>結果

結果は以下のようになるはずです。

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

この結果では、モデルに従ってプレーヤー 3 がプレーヤー 4 よりわずかにランクが高い点に注目してください。 これは、プレーヤー 3 がプレーヤー 1 に勝ったことが、プレーヤー 4 がプレーヤー 2 に勝ったことよりも重要であるためです (プレーヤー 1 がプレーヤー 2 に勝つことに注意してください)。 プレーヤー 0 が全体のチャンピオンです。

## <a name="keep-learning"></a>学習の継続

統計モデルの設計は独自のスキルです。 Microsoft Research Cambridge チームは、この記事を簡単に紹介した[無料のオンライン ブック](http://mbmlbook.com/)を作成しました。 このブックの第 3 章には、TrueSkill モデルが詳しく説明されています。 モデルを考えついたら、Infer.NET Web サイトの[膨大なドキュメント](https://dotnet.github.io/infer/)を使用してモデルをコードに変換することができます。

## <a name="next-steps"></a>次の手順

学習を続けてその他のサンプルを確認するには、Infer.NET の GitHub リポジトリを参照してください。
> [!div class="nextstepaction"]
> [dotnet/infer の GitHub リポジトリ](https://github.com/dotnet/infer)

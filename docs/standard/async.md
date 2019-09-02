---
title: 非同期の概要
description: ブロッキング I/O と複数コアでの同時操作の処理を容易にする鍵となる手法である非同期プログラミングについて説明します。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 2f76eb7d2b769b59809bec81aefacb7cec90a450
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106686"
---
# <a name="async-overview"></a>非同期の概要

少し前まで、アプリの高速化は、より新しい PC やサーバーを購入することによって単純に実現されていましたが、その傾向は終わりました。 実際には、逆転しました。 1 GHz のシングル コア ARM チップを搭載した携帯電話が登場し、サーバーのワークロードは VM に移行されました。 ユーザーは引き続き応答速度の速い UI を望み、ビジネス オーナーは業務の拡大に合わせて拡張できるサーバーを必要としています。 モバイルおよびクラウドへの移行が進み、インターネット接続ユーザーが 30 億人を超えた結果、新しいソフトウェア パターンが生まれました。 

- クライアント アプリケーションには、アプリ ストアの高い評価と共に、常時オンで常時接続であること、そのうえでユーザーの操作 (タッチなど) に対する応答性を常に維持することが期待されます。
- サービスは、適切にスケールアップおよびスケールダウンしてトラフィックの急増に対処することが期待されます。 

非同期プログラミングは、ブロッキング I/O と複数コアでの同時操作の処理を容易にする鍵となる手法です。 .NET では、C#、VB、F# で簡単に使用できる言語レベルの非同期プログラミング モデルにより、アプリやサービスの応答性と弾力性を実現する機能を提供します。

## <a name="why-write-async-code"></a>非同期コードを記述する理由

最新アプリでは、ファイルおよびネットワーク I/O を広範囲に使用します。 従来の I/O API は既定によりブロックし、困難なパターンを学習して使用しない限り、結果的にユーザー エクスペリエンスとハードウェア使用率が不適切になっていました。 このモデルを逆転させたのがタスクベースの非同期 API と言語レベルの非同期プログラミング モデルであり、非同期実行が既定になりました。これに関して新たに学習する必要がある概念はほとんどありません。

非同期コードの特性は次のとおりです。

- スレッドを生成することによって、I/O 要求が戻るのを待つ間により多くのサーバー要求を処理します。
- I/O 要求の待機中に UI 操作に対してスレッドを生成し、実行時間の長い作業を他の CPU コアに移行することによって、UI の応答性を高めます。
- 新しい .NET API の多くは非同期です。
- .NET で非同期コードを記述するのはとても簡単です。

## <a name="whats-next"></a>次の内容

詳しくは、「[非同期の詳細](async-in-depth.md)」トピックをご覧ください。

「[非同期プログラミングのパターン](asynchronous-programming-patterns/index.md)」トピックでは、.NET でサポートされている 3 種類の非同期プログラミング パターンの概要が説明されています。  
  
- [非同期プログラミング モデル (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (レガシ)  
  
- [イベント ベースの非同期パターン (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (レガシ)  
  
- [タスク ベースの非同期パターン (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (新規の開発に推奨)  

推奨されるタスク ベースのプログラミング モデルについて詳しくは、「[タスク ベースの非同期プログラミング](parallel-programming/task-based-asynchronous-programming.md)」トピックをご覧ください。

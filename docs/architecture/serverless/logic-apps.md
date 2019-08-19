---
title: Azure Logic Apps サーバーレスアプリ
description: クラウドサービスとオンプレミスシステムの間でアプリとデータを統合する、自動化されたスケーラブルなワークフローの構築を Azure Logic Apps できます。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577455"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)は、クラウドサービスとオンプレミスシステムの間でアプリとデータを統合するための自動化されたワークフローを構築するサーバーレスエンジンを提供します。 ワークフローは、ビジュアルデザイナーを使用して作成します。 イベントまたはタイマーに基づいてワークフローをトリガーし、統合アプリケーションへのコネクタを活用して、企業間 (B2B) 通信を容易にすることができます。 Logic Apps は Azure Functions とシームレスに統合されます。

![Azure Logic Apps ロゴ](./media/logic-apps-logo.png)

クラウドサービス (functions など) をクラウドリソース (キューやデータベースなど) と接続するだけでなく、Logic Apps もできます。 オンプレミスのゲートウェイを使用してオンプレミスのワークフローを調整することもできます。 たとえば、ロジックアプリを使用して、ワークフロー内のクラウドベースのイベントまたは条件付きロジックに応じて、オンプレミスの SQL ストアドプロシージャをトリガーすることができます。 オンプレミスのデータソースへの接続の詳細については、「[オンプレミスデータゲートウェイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)」を参照してください。

![Logic Apps アーキテクチャ](./media/logic-apps-architecture.png)

Azure Functions と同様に、トリガーを使用してロジックアプリのワークフローを開始します。 選択できるトリガーは多数あります。 次のキャプチャでは、使用可能な数百を超える人気のあるものをいくつか紹介します。

![Logic Apps トリガー](./media/logic-app-triggers.png)

アプリがトリガーされたら、ビジュアルデザイナーを使用して、ステップ、ループ、条件、およびアクションを作成できます。 前の手順で作成したデータ取り込まれたは、以降の手順で使用できます。 次のワークフローは、CosmosDB データベースから Url を読み込みます。 ホスト`t.co`があるものを検索し、Twitter で検索します。 対応するツイートが見つかった場合は、関数を呼び出すことによって、関連するツイートでドキュメントを更新します。

![ロジックアプリのワークフロー](./media/logic-app-workflow.png)

Logic Apps ダッシュボードには、ワークフローの実行履歴と、各実行が正常に完了したかどうかが表示されます。 特定の実行に移動し、各ステップで使用されるデータを調べて、トラブルシューティングを行うことができます。 Logic Apps には、編集できる既存のテンプレートも用意されており、複雑なエンタープライズワークフローに適しています。

詳細については、「 [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)」を参照してください。

>[!div class="step-by-step"]
>[前へ](application-insights.md)
>[次へ](event-grid.md)

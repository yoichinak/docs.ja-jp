---
title: Azure Logic Apps でサーバーレス アプリ
description: Azure Logic Apps は、アプリに統合される自動化されたスケーラブルなワークフローの構築を有効にして、クラウド間でデータ サービスし、オンプレミス システムにします。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638801"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)アプリとクラウド サービス間のデータを統合する自動化されたワークフローを構築するサーバーレス エンジンを提供し、オンプレミス システムにします。 ビジュアル デザイナーを使用してワークフローを作成します。 イベントまたはタイマーおよび統合アプリケーションへのコネクタを活用して基にワークフローをトリガーし、企業間取引 (B2B) 通信を容易にできます。 Logic Apps は、Azure Functions とシームレスに統合します。

![Azure Logic Apps のロゴ](./media/logic-apps-logo.png)

Logic Apps は、(キュー、およびデータベース) などのクラウド リソースを接続するだけです (関数) と同様、クラウド サービスよりも多く実行できます。 オンプレミス ゲートウェイとオンプレミスでワークフローを調整することもできます。 たとえば、クラウド ベースのイベントに応答をオンプレミスの SQL ストアド プロシージャまたはワークフローで条件付きロジックをトリガーするのにロジック アプリを使用できます。 詳細については[Azure をオンプレミス データ ゲートウェイとオンプレミス データ ソースに接続する](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)します。

![ロジック アプリのアーキテクチャ](./media/logic-apps-architecture.png)

Azure 関数のようにトリガーを使用してロジック アプリ ワークフローを開始します。 これは、多くのトリガーから選ぶことができます。 次のキャプチャは、最も一般的なもののうち何百も利用できるのほんの一部を示しています。

![ロジック アプリ トリガー](./media/logic-app-triggers.png)

アプリがトリガーされると、手順、ループ、条件、およびアクションを構築するビジュアル デザイナーを使用できます。 前の手順で取り込まれたデータは、以降の手順で使用するために使用できます。 次のワークフローは、CosmosDB データベースから Url を読み込みます。 ホストのあるものを見つけた`t.co`Twitter でそれらを検索します。 対応するツイートが見つかると、そのドキュメントを更新する関連ツイートの関数を呼び出すことによって。

![ロジック アプリ ワークフロー](./media/logic-app-workflow.png)

ロジック アプリのダッシュ ボードは、ワークフローとかどうかの各実行が完了したかが正常に実行の履歴を示します。 任意の特定の実行に移動し、トラブルシューティングの各ステップで使用されるデータを検査できます。 Logic Apps には、既存のテンプレートを編集でき、複雑なエンタープライズ ワークフローの場合に適しています。

詳細についてを参照してください。 [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)します。

>[!div class="step-by-step"]
>[前へ](application-insights.md)
>[次へ](event-grid.md)

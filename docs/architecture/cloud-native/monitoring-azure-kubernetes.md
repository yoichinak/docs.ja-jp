---
title: Azure Kubernetes Services での監視
description: Azure Kubernetes Services での監視
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "73841127"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Azure Kubernetes Services での監視

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kubernetes の組み込みログはプリミティブです。 ただし、Kubernetes からログを取得し、適切に分析できる場所にするための優れたオプションがいくつかあります。 AKS クラスターを監視する必要がある場合は、Kubernetes のエラスティックスタックの構成が優れたソリューションです。

## <a name="elastic-stack"></a>エラスティックスタック

エラスティックスタックは、Kubernetes クラスターから情報を収集するための強力なオプションです。 Kubernetes では、Elasticsearch エンドポイントへのログの送信がサポートされています。[ほとんど](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)の場合、図7-5 に示すように、環境変数を設定するだけで始める必要があります。

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**図 7-5** -Kubernetes の構成変数

これにより、クラスターに Elasticsearch がインストールされ、すべてのクラスターログをそのクラスターに送信するターゲットになります。

Kibana ダッシュボードの例 ![、取り込まれたからのログに対するクエリの結果を Kubernetes](./media/kibana-dashboard.png)
**図 7-6**に示します。 Kubernetes から取り込まれたのログに対するクエリの結果を表示する Kibana ダッシュボードの例

## <a name="azure-container-monitoring"></a>Azure コンテナーの監視

Azure Container Monitoring は、Kubernetes だけでなく、DC/OS、Docker の群れ、Red Hat OpenShift などの他のオーケストレーションエンジンからのログの使用もサポートしています。

さまざまなコンテナーからのログの使用 ![](./media/containers-diagram.png)
**図 7-7**。  さまざまなコンテナーからのログの使用

ログとメトリックの情報は、クラスターで実行されているコンテナーだけでなく、クラスターからも収集されます。 これにより、2つのログ情報を相互に関連付けることができるため、エラーをより簡単に追跡できます。

ログコレクターのインストールは、 [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes)クラスターと[Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes)クラスターで異なります。 ただし、どちらの場合も、ログの収集は Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)として実装されます。つまり、ログコレクターは各ノード上のコンテナーとして実行されます。

Azure Monitor デーモンを実行している orchestrator またはオペレーティングシステムにかかわらず、ログ情報は、ユーザーが使い慣れているのと同じ Azure Monitor ツールに転送されます。 これにより、ハイブリッド Kubernetes/Azure Functions 環境などのさまざまなログソースが混在する環境での並行操作が可能になります。

多数の実行中のコンテナーからのログ記録とメトリック情報を示すサンプルダッシュボードを ![します。](./media/containers-dashboard.png)
**図 7-8**。 多数の実行中のコンテナーからのログ記録とメトリック情報を示すサンプルダッシュボードです。

## <a name="logfinalize"></a>Log. Finalize ()

ログ記録は、大規模なアプリケーションのデプロイにおいて、見過ごされていて最も重要な部分の1つです。 アプリケーションのサイズと複雑さが増加するにつれて、アプリケーションのデバッグが困難になります。 高品質のログを使用すると、デバッグがはるかに簡単になり、"ほぼ不可能な" 領域から "快適なエクスペリエンス" に移行することができます。

>[!div class="step-by-step"]
>[前へ](logging-with-elastic-stack.md)
>[次へ](azure-monitor.md)

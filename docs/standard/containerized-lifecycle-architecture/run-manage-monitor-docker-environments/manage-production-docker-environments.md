---
title: Docker の実稼働環境を管理する
description: コンテナー ベースの実稼働環境を管理する重要な点を把握するを取得します。
ms.date: 02/15/2019
ms.openlocfilehash: 7d10f670745f8bac1084b8c33c5acde67bac6229
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641070"
---
# <a name="manage-production-docker-environments"></a>Docker の実稼働環境を管理する

クラスターの管理とオーケストレーションは、ホストのグループを制御するためのプロセスです。 追加して、クラスターでは、ホストとコンテナーの現在の状態に関する情報を取得し、開始およびプロセスの停止からホストを削除する必要があります。 クラスターの管理とオーケストレーションは、スケジューラは、クラスター内の各ホストへのアクセスをサービスのスケジュールを設定するにがある必要なためにのスケジューリングに密接に関連付けします。 このため、両方の目的で、同じツールがよく使用されます。

## <a name="container-service-and-management-tools"></a>コンテナー サービスと管理ツール

Container Service では、人気のオープン ソース コンテナーのクラスタ リングやオーケストレーション ソリューションの迅速なデプロイを提供します。 Docker イメージを使用して、アプリケーション コンテナーが完全に移植可能であることを確認します。 DC OS/(Mesosphere と Apache Mesos 利用) をデプロイするコンテナー サービスを使用して、Docker Swarm クラスターを Azure Resource Manager テンプレートまたは数千にこれらのアプリケーションをスケーリングできることを確認する Azure portal を使用: 数万も — のコンテナー。

Azure 仮想マシン スケール セットを使用してこれらのクラスターを展開して、クラスターを Azure のネットワークおよび記憶域サービスの利用します。 コンテナー サービスにアクセスするには、Azure サブスクリプションを必要があります。 Container service では、オーケストレーション レイヤーなど、アプリケーションの移植性を維持しながら Azure のエンタープライズ級の機能を活用がかかります。

表 6-1 は、オーケストレーター、スケジューラ、クラスタ リングのプラットフォームに関連する、一般的な管理ツールを一覧表示します。

**表 6-1**します。 Docker の管理ツール

| 管理ツール | 説明 | 関連するオーケストレーター |
|------------------|-------------|-----------------------|
| [Azure Monitor for Containers](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | 専用の azure の Kubernetes 管理ツール | Azure Kubernetes サービス (AKS) |
| [Kubernetes Web UI (ダッシュ ボード)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Kubernetes の管理ツールでは監視したり、ローカルの Kubernetes クラスターの管理 | Azure Kubernetes Service (AKS)<br/>ローカルの Kubernetes |
| [Service Fabric 用に azure ポータル](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Azure、オンプレミス、ローカルの開発、およびその他のクラウドでの Service Fabric クラスターを管理するためのオンラインやデスクトップのバージョン | Azure Service Fabric |
| [コンテナー (Azure Monitor) の監視](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | 一般的なコンテナー管理 y がソリューションを監視します。 使って Kubernetes クラスターを管理できます[コンテナー用の Azure Monitor](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview)します。 | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS、および他のユーザー。 |

## <a name="azure-service-fabric"></a>Azure Service Fabric

クラスターのデプロイと管理に関する別の選択肢では、Azure Service Fabric です。 [Service Fabric](https://azure.microsoft.com/services/service-fabric/)開発者と同様にコンテナーのオーケストレーションを含む Microsoft のマイクロ サービス プラットフォームは非常にスケーラブルなマイクロ サービス アプリケーションを構築するモデルをプログラミングします。 Service Fabric では、Linux と Windows コンテナーで Docker をサポートしているし、Windows および Linux サーバーで実行できます。

Service Fabric 管理ツールを次に示します。

- [Service Fabric 用に azure ポータル](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)クラスター関連の操作 (作成/更新/削除)、クラスターまたはインフラストラクチャ (Vm、ロード バランサー、ネットワークなど) の構成

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster)は特殊な web UI と洞察やノード/vm の観点から、アプリケーションとサービスの観点から、Service Fabric クラスターで特定の操作を提供するデスクトップのマルチプラット フォーム ツールです。

>[!div class="step-by-step"]
>[前へ](run-microservices-based-applications-in-production.md)
>[次へ](monitor-containerized-application-services.md)

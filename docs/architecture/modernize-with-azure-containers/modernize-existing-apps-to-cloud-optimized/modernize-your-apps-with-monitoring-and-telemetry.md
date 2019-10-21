---
title: 監視と製品利用統計情報でアプリを最新化する
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |監視とテレメトリを使用してアプリを最新化する
ms.date: 04/30/2018
ms.openlocfilehash: 3d629e89a73c870d4b6396c6b1d0ecbe95b79ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393849"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>監視と製品利用統計情報でアプリを最新化する

運用環境でアプリケーションを実行する場合、アプリケーションのパフォーマンスについての洞察があることが重要です。 高レベルで実行していますか。 ユーザーがエラーを受け取るか、アプリケーションの安定性と信頼性があるか。 アプリケーションを確実に使用し、期待どおりに実行できるように、豊富なパフォーマンス監視、強力なアラート、ダッシュボードが必要です。 また、問題が発生した場合はすばやく表示し、影響を受けている顧客の数を特定し、根本原因の分析を実行して問題を見つけて解決する必要もあります。

## <a name="monitor-your-application-with-application-insights"></a>Application Insights を使用したアプリケーションの監視

Application Insights は、複数のプラットフォームで作業する web 開発者向けの拡張可能なアプリケーションパフォーマンス管理 (APM) サービスです。 これを使用して、ライブ web アプリケーションを監視します。 Application Insights は、パフォーマンスの異常を自動的に検出します。 これには、問題の診断に役立つ強力な分析ツールが含まれており、ユーザーがアプリで実際に実行する操作を理解するのに役立ちます。 Application Insights は、パフォーマンスと使いやすさを継続的に向上させることができるように設計されています。 オンプレミスまたはクラウドにホストされているかどうかにかかわらず、.NET、node.js、J2EE など、さまざまなプラットフォーム上のアプリで動作します。 Application Insights は、DevOps プロセスと統合され、さまざまな開発ツールへの接続ポイントを備えています。

図4-10 は、Application Insights がアプリケーションを監視する方法と、その洞察をダッシュボードに表示する方法の例を示しています。

![Application Insights 監視ダッシュボードのスクリーンショット。](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**図 4-10.** Application Insights 監視ダッシュボード

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Log Analytics とそのコンテナー監視ソリューションを使用して Docker インフラストラクチャを監視する

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)は、 [Microsoft Azure 監視ソリューション全体](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)の一部です。 また、 [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)のサービスでもあります。 Log Analytics は、クラウドおよびオンプレミスの環境 (OMS の場合) を監視して、可用性とパフォーマンスを維持します。 クラウドとオンプレミスの環境内のリソースによって生成されたデータを収集し、その他の監視ツールから、複数のソースにわたる分析を提供します。

Azure インフラストラクチャログに関しては、Log Analytics azure サービスとして、他の Azure サービス ( [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)経由)、azure Vm、Docker コンテナー、オンプレミスまたはその他のクラウドインフラストラクチャのログとメトリックデータを取り込みします。 Log Analytics は、このデータの上に柔軟なログ検索と、すぐに利用できる分析機能を提供します。 これには、ソース全体のデータの分析に使用できる豊富なツールが用意されています。また、すべてのログに対して複雑なクエリを実行でき、指定された条件に基づいて事前にアラートを作成することもできます。 中央の Log Analytics リポジトリでカスタムデータを収集することもできます。この場合、クエリと視覚化を実行できます。 また、Log Analytics 組み込みソリューションを活用して、インフラストラクチャのセキュリティと機能についてすぐに洞察を得ることもできます。

OMS ポータルまたは任意のブラウザーで実行されている Azure portal を使用して Log Analytics にアクセスできます。また、構成設定や複数のツールにアクセスして、収集したデータを分析して操作することができます。

Log Analytics の[コンテナー監視ソリューション](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)を使用すると、Docker および Windows コンテナーホストを1か所で表示および管理できます。 このソリューションでは、どのコンテナーが実行されているか、どのコンテナーイメージが実行されているか、コンテナーが実行されている場所が示されます。 コンテナーで使用されているコマンドなど、詳細な監査情報を表示できます。 また、Docker または Windows ホストをリモートで表示することなく、集中管理されたログを表示および検索して、コンテナーのトラブルシューティングを行うこともできます。 ノイズが発生し、ホスト上のリソースを消費している可能性のあるコンテナーを見つけることができます。 また、コンテナーの CPU、メモリ、ストレージ、およびネットワークの集中的な使用率とパフォーマンス情報を表示できます。 Windows を実行しているコンピューターでは、Windows Server、Hyper-v、および Docker コンテナーのログを一元化して比較することができます。 このソリューションでは、次のコンテナー orchestrators サポートされています。

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

図4-11 は、さまざまなコンテナーホストとエージェントおよび OMS 間の関係を示しています。

![Log Analytics コンテナー監視ソリューションのスクリーンショット。](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**図 4-11.** Log Analytics コンテナー監視ソリューション

Log Analytics Container Monitoring ソリューションを使用して、次のことを行うことができます。

- 1つの場所にあるすべてのコンテナーホストに関する情報を表示します。

- 実行中のコンテナー、実行されているイメージ、および実行されている場所を把握します。

- コンテナーに対するアクションについては、監査証跡を参照してください。

- Docker ホストへのリモートログインを行わずに、一元化されたログを表示して検索することによってトラブルシューティングを行います。

- "ノイズの多い近隣ノード" であり、ホスト上で過剰なリソースを消費している可能性のあるコンテナーを検索します。

- コンテナーの CPU、メモリ、ストレージ、およびネットワークの集中的な使用状況とパフォーマンス情報を表示します。

### <a name="additional-resources"></a>その他の技術情報

- **Microsoft Azure での監視の概要**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights とは何か?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Log Analytics とは**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure Monitor のコンテナー監視ソリューション**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure Monitor の概要**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Operations Management Suite (OMS) とは**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[前へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[次へ](life-cycle-ci-cd-pipelines-devops-tools.md)

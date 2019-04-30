---
title: 監視と製品利用統計情報でアプリを最新化する
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |監視と遠隔測定でアプリを最新化します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: cd54861600127191b852e0a966baae6e0fe7914e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012093"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>監視と製品利用統計情報でアプリを最新化する

運用環境でアプリケーションを実行するときに、アプリケーションの実行状況に関する洞察があることが重要です。 高レベルが高いでしょうか。 ユーザー エラーが発生、または安定性と信頼性の高いアプリケーションは、ですか。 豊富なパフォーマンスの監視、強力なアラート、およびダッシュ ボード、アプリケーションが使用可能なと予期されるパフォーマンスであることを確認する必要があります。 また、かどうかは、問題をすばやく確認するには、顧客の数が影響を受けてし、見つけて、問題を修正、根本原因分析、を決定できる必要があります。

## <a name="monitor-your-application-with-application-insights"></a>Application Insights を使用してアプリケーションを監視します。

Application Insights は、複数のプラットフォームで作業を行う web 開発者の拡張可能なアプリケーション パフォーマンス管理 (APM) サービスです。 ライブ web アプリケーションを監視するのにには、これを使用します。 Application Insights は、パフォーマンスの異常を自動的に検出します。 これには、問題の診断に役立つとで何が実際に実行、アプリの理解に役立つ強力な分析ツールが含まれます。 Application Insights はパフォーマンスと使いやすさを継続的に向上させるために設計されています。 さまざまなプラットフォーム、.NET、Node.js、J2EE をかどうかなどのアプリケーションに適してがオンプレミスでホストまたはクラウドで。 Application Insights は、DevOps プロセスと統合し、さまざまな開発ツールへの接続ポイントします。

図 4-10 では、Application Insights がアプリケーションを監視する方法と、ダッシュ ボードにこれらの洞察の表示の例を示します。

![Application Insights の監視ダッシュ ボード](./media/image10.png)

> **図 4-10。** Application Insights の監視ダッシュ ボード

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Docker を Log Analytics とそのコンテナー監視ソリューション インフラストラクチャを監視します。

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)の一部である、 [Microsoft Azure の全体監視ソリューション](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)します。 これはまた、サービス[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)します。 Log Analytics 監視クラウドとオンプレミス環境 (オンプレミス用の OMS) の可用性とパフォーマンスを維持するためにします。 リソースが、クラウドおよびオンプレミス環境内で、複数のソースにわたる分析を提供する他の監視ツールから生成されたデータを収集します。

Azure インフラストラクチャのログに対する Log Analytics では、Azure のサービスとしてログとメトリックからデータを取り込む他の Azure サービス (を使用して[Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))、Azure Vm、Docker コンテナー、およびオンプレミスまたはその他のクラウド インフラストラクチャ。 Log Analytics では、柔軟なログ検索とそのデータ出力の分析を提供します。 指定した条件に基づいてことソース間でデータを分析する際、すべてのログの間で複雑なクエリがおよび、事前に通知することができます、豊富なツールを提供します。 中央の Log Analytics リポジトリを照会および視覚化できるにカスタム データも収集できます。 セキュリティに関する洞察を即座に得るために Log Analytics の組み込みソリューションを利用し、インフラストラクチャの機能を実行することができますも。

OMS ポータルまたは任意のブラウザーで実行して、Azure portal から Log Analytics にアクセスし、構成設定にアクセスしてや複数のツールを分析し、収集されたデータを操作できます。

[コンテナー監視ソリューション](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)Log Analytics での表示し、1 つの場所で Docker と Windows コンテナー ホストを管理します。 どのコンテナーが、ソリューションを示しています、どのようなコンテナー イメージを実行して、実行されているし、コンテナーが実行されています。 コンテナーで使用されているコマンドを含む、詳細な監査情報を表示することができます。 また、コンテナーを表示および Docker または Windows ホストをリモートで表示することがなく、一元化されたログを検索してトラブルシューティングすることもできます。 ホストで余分なリソースを簡潔にかかる可能性があるコンテナーが表示されます。 さらに、一元的な CPU、メモリ、ストレージ、およびネットワーク使用率およびパフォーマンスについては、コンテナーを表示することができます。 Windows を実行するコンピューターで、集中管理し、Windows サーバーからログを比較することができます、HYPER-V、および Docker コンテナー。 ソリューションには、次のようなコンテナー オーケストレーターがサポートされています。

- Docker Swarm

- DC OS/

- Kubernetes

- Service Fabric

- Red Hat の OpenShift

図 4-11 は、さまざまなコンテナー ホストとエージェントと OMS 間の関係を示しています。

![Log Analytics コンテナー監視ソリューション](./media/image11.png)

> **図 4-11。** Log Analytics コンテナー監視ソリューション

Log Analytics コンテナー監視ソリューションを使用できます。

- 1 つの場所ですべてのコンテナー ホストに関する情報を参照してください。

- どのコンテナーが、どのようなイメージを実行して、実行されているし、実行しています。

- コンテナー操作の監査証跡を参照してください。

- 表示および Docker ホストへのリモート ログインに関係なく、一元化されたログを検索してトラブルシューティングを行います。

- 「うるさい隣人」、可能性がありますし、ホストで余分なリソースを消費するコンテナーを検索します。

- 一元的な CPU、メモリ、ストレージ、およびネットワーク使用率およびパフォーマンスについては、コンテナーを表示します。

### <a name="additional-resources"></a>その他の技術情報

- **Microsoft Azure での監視の概要**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights とは何か?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Log Analytics とは何ですか。**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure Monitor でのコンテナー監視ソリューション**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure Monitor の概要**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Operations Management Suite (OMS) とは何ですか。**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- **OMS を使用して Service Fabric で Windows Server コンテナーの監視**

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
>[前へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[次へ](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)

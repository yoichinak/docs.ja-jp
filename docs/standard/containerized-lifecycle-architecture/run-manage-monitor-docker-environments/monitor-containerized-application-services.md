---
title: コンテナー化されたアプリケーションのサービスを監視します。
description: 監視コンテナー アーキテクチャの重要な側面について説明します
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975746"
---
# <a name="monitor-containerized-application-services"></a>コンテナー化されたアプリケーションのサービスを監視します。

アプリケーションが複数のコンテナーとマイクロ サービスに分割に監視し、アプリケーション全体の動作を分析する方法を実装するが重要です。

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)はライブ アプリケーションを監視する拡張可能な分析サービスです。 検出してパフォーマンスの問題を診断し、で何が実際に実行、アプリを理解することができます。 継続的にパフォーマンスを向上させるに役立つインテントと、サービスまたはアプリケーションの使いやすさの開発者に設計されています。 Application Insights は、さまざまなプラットフォームなど、.NET、Java、Node.js とその他の多くのプラットフォームは、オンプレミスでホストされているのかクラウド内でアプリを web/サービスとスタンドアロンの両方で動作します。

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Application Insights を使用して、QA 環境での Docker アプリの分析

Docker に関連して、ライフ サイクル イベントと Application Insights 上の Docker コンテナーからパフォーマンス カウンターをグラフにできます。 だけを実行する必要があります、 [Application Insights の Docker イメージ](https://hub.docker.com/r/microsoft/applicationinsights/)ように、ホストし、コンテナーは他の Docker イメージの場合と同様のホストのパフォーマンス カウンターを表示します。 この Application Insights の Docker イメージ (図 6-1) のパフォーマンスとの Docker ホスト (つまり、Linux Vm)、Docker コンテナーを実行しているアプリケーションのアクティビティに関するテレメトリを収集することで、コンテナー化アプリケーションを監視することに役立ちます内にします。

![例](./media/image1.png)

**図 6-1**。 Application Insights の Docker ホストとコンテナーの監視

実行すると、 [Application Insights の Docker イメージ](https://hub.docker.com/r/microsoft/applicationinsights/)次のメリットの Docker ホストで。

- ライフ サイクル ホストで実行されているすべてのコンテナーに関する製品利用統計情報: 開始、停止、および具合です。

- すべてのコンテナーのパフォーマンス カウンター:CPU、メモリ、ネットワークの使用状況、および詳細。

- インストールされている場合[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)コンテナーで実行されているアプリでこれらのアプリのすべてのテレメトリがコンテナーとホスト マシンを識別する追加のプロパティが。 そのため、たとえば、1 つ以上のホストで実行されているアプリのインスタンスがあれば、簡単にことができますをホストして、アプリのテレメトリをフィルター処理します。

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>アプリケーションの Docker および Docker ホストを監視するための Application Insights の設定

Application Insights リソースを作成するには、次の一覧に記事の指示に従います。 Azure ポータルを必要なスクリプトを作成します。

- **Application Insights で Docker アプリケーションを監視します。** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- **Docker Hub や GitHub にある application Insights の Docker イメージ:** \
  <https://hub.docker.com/r/microsoft/applicationinsights/> および \
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- **ASP.NET web アプリおよび ASP.NET Core 用の Application Insights を設定します。** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- **Web ページ用の application Insights:**  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a>セキュリティ、バックアップ、およびサービスの監視

大量の処理、アプリケーションおよびインフラストラクチャがビジネス上のニーズをサポートするために一流の条件を確認する必要のある詳細情報を多くのサポートのような作業があるし、する方法を作成する必要があります、状況が、マイクロ サービス領域で複雑になったアクションを実行する必要があるときに概要と詳細ビューがあります。

Azure では、管理し、クラウドとオンプレミスの両方のリソースの 4 つの重要な側面の統一されたビューを提供するツールがあります。

- **セキュリティ**します。 [Azure Security Center](https://azure.microsoft.com/services/security-center/)します。
  - 完全な可視化と仮想マシン、アプリ、ワークロードのセキュリティ制御を取得します。
  - セキュリティ ポリシーの管理を一元化し、既存のプロセスやツールを統合します。
  - 高度な分析の真の脅威を検出します。

- **バックアップ**します。 [Azure Backup](https://azure.microsoft.com/services/backup/)します。
  - コストのかかるビジネス中断を避けるため、コンプライアンス目標を満たすおよびランサムウェアやヒューマン エラーからデータを保護します。
  - 転送中に暗号化、バックアップ データを保持します。
  - 承認されていない使用を防ぐための多要素認証に基づいてアクセスを確認します。

- **監視**します。 [Azure monitoring](https://azure.microsoft.com/solutions/monitoring/)、 [Log Analytics](https://azure.microsoft.com/services/log-analytics/)、および[Application Insights](https://azure.microsoft.com/services/application-insights/)します。
  - 正常性と、Azure のワークロード、アプリケーション、およびインフラストラクチャのパフォーマンスには、完全な可視性を取得します。
  - 任意のソースからデータを収集し、仮想マシン、コンテナー、およびアプリケーションに豊富な分析情報を取得します。
  - 対話型クエリとフルテキスト検索を使用して必要な情報を検索します。 
  - 根本原因の分析と機械学習アルゴリズムなどの高度な分析を実行します。

- **オンプレミス リソースに**します。 [真に一貫性のあるハイブリッド クラウド](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)します。

>[!div class="step-by-step"]
>[前へ](manage-production-docker-environments.md)
>[次へ](../key-takeaways/index.md)

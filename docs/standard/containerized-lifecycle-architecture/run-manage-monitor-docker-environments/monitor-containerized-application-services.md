---
title: コンテナー化アプリケーションのサービスを監視する
description: 監視コンテナー アーキテクチャの重要な側面について説明します
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4553a35c8db6cfc46187525ef2ffc65cb3ba07c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672049"
---
# <a name="monitor-containerized-application-services"></a>コンテナー化アプリケーションのサービスを監視する

アプリケーションが複数のコンテナーとマイクロ サービスに分割に監視し、アプリケーション全体の動作を分析する方法を実装するが重要です。

## <a name="azure-monitor"></a>Azure Monitor

[Azure Monitor](https://azure.microsoft.com/services/monitor/)はライブ アプリケーションを監視する拡張可能な分析サービスです。 検出してパフォーマンスの問題を診断し、で何が実際に実行、アプリを理解することができます。 継続的にパフォーマンスを向上させるに役立つインテントと、サービスまたはアプリケーションの使いやすさの開発者に設計されています。 Azure Monitor は、さまざまなプラットフォームなど、.NET、Java、Node.js とその他の多くのプラットフォームは、オンプレミスでホストされているのかクラウド内でアプリを web/サービスとスタンドアロンの両方で動作します。

### <a name="additional-resources"></a>その他の技術情報

- **Azure Monitor の概要** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights とは何か?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Azure Monitor のメトリックとは何ですか。** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Azure Monitor でのコンテナー監視ソリューション** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>セキュリティとバックアップ サービス

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

- **オンプレミス リソースに**します。 [真に一貫性のあるハイブリッド クラウド](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)します。

>[!div class="step-by-step"]
>[前へ](manage-production-docker-environments.md)
>[次へ](../key-takeaways/index.md)

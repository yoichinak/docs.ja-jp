---
title: クラウドに最適化されたアプリケーションでの Microsoft テクノロジ
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |クラウドに最適化されたアプリケーションでの Microsoft テクノロジ
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 45eeee165a1dcbfc7b6dbc5146ce2c4b2be2e643
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773272"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>クラウドに最適化されたアプリケーションでの Microsoft テクノロジ

次の一覧には、ツール、テクノロジ、およびクラウドに最適化されたアプリの要件として認識されるソリューションについて説明します。 自分の優先順位に応じて選択的にまたは段階的に、クラウドに最適化された要素を導入できます。

-   **クラウド インフラストラクチャ**:このインフラストラクチャは、コンピューティング プラットフォーム、オペレーティング システム、ネットワーク、および記憶域を提供します。 Microsoft Azure は、このレベルに配置されます。

-   **ランタイム**:このレイヤーは、アプリケーションを実行する環境を提供します。 このレイヤーは、通常に基づく、コンテナーを使用している場合[Docker エンジン](https://docs.docker.com/engine/)、Linux ホストで、または Windows ホストで実行中です。 ([Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/) Windows Server 2016 以降ではサポートされています。 Windows コンテナーは Windows で実行される既存の .NET Framework アプリケーションに最適です。)

-   **クラウド管理**:管理されたクラウド オプションを選択すると、費用と複雑さを管理して、基になるインフラストラクチャ、Vm、OS パッチをサポートしているネットワーク構成を回避できます。 IaaS を使用して移行する場合がこれらのタスクのすべてのおよび関連するコストにあります。 管理されたクラウド オプションでは、アプリケーションとサービスを開発のみを管理します。 クラウド サービス プロバイダーを使用して、他はすべて通常管理します。 Azure で管理されたクラウド サービスの例として、 [Azure SQL Database](https://azure.microsoft.com/services/sql-database)、 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)、 [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)、 [Azure Storage](https://azure.microsoft.com/services/storage/)、[Azure Database for MySQL](https://azure.microsoft.com/services/mysql/)、 [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/)、 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)などのコンピューティング サービスを管理および[VM のスケール設定](https://azure.microsoft.com/services/virtual-machine-scale-sets/)、 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)、 [Azure App Service](https://azure.microsoft.com/services/app-service/)、および[Azure Kubernetes サービス](https://azure.microsoft.com/services/container-service/)します。

-   **アプリケーションの開発**:コンテナーで実行されるアプリケーションをビルドするときに、多くの言語から選択することができます。 このガイドの重点[.NET](https://www.microsoft.com/net)が、Node.js、Python、Spring/Java と同様に、他の言語を使用して、コンテナー ベースのアプリを開発したり、移動できます。

-   **監視、製品利用統計情報、ログ記録と監査**:監視と監査のアプリケーションとクラウドで実行されているコンテナー機能は、任意のクラウドに最適化されたアプリケーションにとって重要です。 [Azure Application Insights](https://azure.microsoft.com/services/application-insights/)と[Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite)はクラウドに最適化されたアプリの監視と監査を提供するマイクロソフトの主要なツールです。

-   **プロビジョニング**:自動化ツールでは、インフラストラクチャをプロビジョニングし、複数の環境 (運用、テスト、ステージング) にアプリケーションを展開できます。 Chef、Puppet などのツールを使用して、アプリケーションの構成と環境を管理することができます。 このレイヤーより簡単かつ直接的な方法を使用しても実装できます。 たとえば、ツール、Azure コマンド ライン インターフェイス (Azure CLI) を使用して直接展開し継続的なデプロイを使用し、リリース管理パイプラインで[Azure DevOps サービス](https://azure.microsoft.com/services/devops/)します。

-   **アプリケーションのライフ サイクル**:[Azure DevOps サービス](https://azure.microsoft.com/services/devops/)、Jenkins などの他のツールはビルド オートメーション サーバーにする際に役立つ実装 CI/CD パイプライン、リリース管理を含むとします。

この章では、および関連のチュートリアルの次のセクションでは、ランタイム レイヤー (Windows コンテナー) の詳細について重点的に説明します。 ガイダンスでは、Windows Server 2016 (およびそれ以降のバージョン) で Windows コンテナーの Vm と Azure Container Instances を展開する方法について説明します。 Azure App Service などのより高度な PaaS プラットフォームと Azure Service Fabric と Azure Kubernetes サービスなどのオーケストレーターについても説明します。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>モノリシック アプリケーション*できます*クラウド最適化します。

そのモノリシック アプリケーション (マイクロ サービスに基づいていないアプリケーション) を強調表示することが重要*できます*クラウドに最適化されたアプリケーションします。 構築し、コンテナー、継続的デリバリー、および DevOps の組み合わせを使用してモデルのコンピューティング クラウドを利用するモノリシック アプリケーションを操作できます。 既存のモノリシック アプリケーションが、ビジネス目標の適切な場合は、最新化し、ようにクラウドに最適化されました。

同様に、モノリシック アプリケーションをクラウドに最適化されたアプリケーションとできる場合は、N 層アプリケーションと同様より複雑なアーキテクチャできますも最新化としてクラウドに最適化されたアプリケーション。

>[!div class="step-by-step"]
>[前へ](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[次へ](what-about-cloud-native-applications.md)
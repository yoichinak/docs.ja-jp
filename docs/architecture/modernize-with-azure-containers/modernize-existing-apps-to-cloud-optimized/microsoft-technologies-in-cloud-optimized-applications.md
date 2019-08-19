---
title: クラウド向けに最適化されたアプリケーションの Microsoft テクノロジ
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |クラウド向けに最適化されたアプリケーションの Microsoft テクノロジ
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578225"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>クラウド向けに最適化されたアプリケーションの Microsoft テクノロジ

次の一覧では、クラウド向けに最適化されたアプリの要件として認識されるツール、テクノロジ、およびソリューションについて説明します。 優先順位に応じて、クラウドに最適化された要素を選択的または段階的に導入できます。

- **クラウドインフラストラクチャ**:コンピューティングプラットフォーム、オペレーティングシステム、ネットワーク、およびストレージを提供するインフラストラクチャ。 Microsoft Azure がこのレベルに配置されています。

- **ランタイム**:このレイヤーは、アプリケーションを実行するための環境を提供します。 コンテナーを使用している場合、このレイヤーは通常、Linux ホストまたは Windows ホストで実行されている[Docker エンジン](https://docs.docker.com/engine/)に基づいています。 (Windows[コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/)は、windows Server 2016 以降でサポートされています。 Windows コンテナーは、Windows で実行される既存の .NET Framework アプリケーションに最適な選択肢です)。

- **管理**されたクラウド:管理されたクラウドオプションを選択すると、基盤となるインフラストラクチャ、Vm、OS パッチ、およびネットワーク構成の管理とサポートに伴う費用と複雑さを回避できます。 IaaS を使用して移行することを選択した場合は、これらのすべてのタスクと関連コストについて責任があります。 マネージクラウドオプションでは、開発したアプリケーションとサービスのみを管理します。 クラウドサービスプロバイダーは、通常、他のすべてを管理します。 Azure の管理されたクラウドサービスの例としては、 [Azure SQL Database](https://azure.microsoft.com/services/sql-database)、 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)、 [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)、 [Azure Storage](https://azure.microsoft.com/services/storage/)、 [Azure Database for MySQL](https://azure.microsoft.com/services/mysql/)、 [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/)、azure Active などがあります。 [ディレクトリ](https://azure.microsoft.com/services/active-directory/)、および[VM スケールセット](https://azure.microsoft.com/services/virtual-machine-scale-sets/)、 [Azure App Service](https://azure.microsoft.com/services/app-service/)、 [Azure Kubernetes サービス](https://azure.microsoft.com/services/container-service/)などの管理されたコンピューティングサービス。

- **アプリケーション開発**:コンテナーで実行されるアプリケーションをビルドするときに、多くの言語から選択できます。 このガイドでは[.net](https://www.microsoft.com/net)に焦点を当てていますが、Node.js、Python、Spring/Java、またはゴーなどの他の言語を使用して、コンテナーベースのアプリを開発することもできます。

- **監視、テレメトリ、ログ、および監査**:クラウドで実行されているアプリケーションやコンテナーを監視および監査する機能は、クラウドに最適化されたアプリケーションにとって非常に重要です。 [Azure アプリケーション Insights](https://azure.microsoft.com/services/application-insights/)と[Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite)は、クラウド向けに最適化されたアプリの監視と監査を提供する主要な Microsoft ツールです。

- **プロビジョニング**:Automation ツールは、インフラストラクチャをプロビジョニングし、複数の環境 (運用、テスト、ステージング) にアプリケーションをデプロイするのに役立ちます。 Chef やパペットなどのツールを使用して、アプリケーションの構成と環境を管理できます。 このレイヤーは、より単純で直接的な方法を使用して実装することもできます。 たとえば、Azure コマンドラインインターフェイス (Azure CLI) ツールを使用して直接デプロイし、 [Azure DevOps Services](https://azure.microsoft.com/services/devops/)で継続的デプロイとリリース管理のパイプラインを使用することができます。

- **アプリケーションのライフサイクル**:[Azure DevOps Services](https://azure.microsoft.com/services/devops/)およびその他のツール (Jenkins など) は、リリース管理を含む CI/CD パイプラインの実装に役立つオートメーションサーバーを構築しています。

この章の次のセクションと関連するチュートリアルでは、特にランタイムレイヤー (Windows コンテナー) について詳しく説明します。 このガイダンスでは、windows Server 2016 (およびそれ以降のバージョン) の Vm と Azure Container Instances に Windows コンテナーを展開する方法について説明します。 また、Azure Kubernetes Service などの Azure App Service や orchestrator など、より高度な PaaS プラットフォームについても説明します。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>モノリシックアプリケーションはクラウドに最適化*できます*。

モノリシックアプリケーション (マイクロサービスをベースにしていないアプリケーション) は、クラウドに最適化されたアプリケーションにすることが重要です。 コンテナー、継続的デリバリー、DevOps の組み合わせを使用して、クラウドコンピューティングモデルを利用するモノリシックアプリケーションを構築して運用することができます。 既存のモノリシックアプリケーションがビジネスの目標に適している場合は、そのアプリケーションを最新化し、クラウドに最適化することができます。

同様に、モノリシックアプリケーションがクラウドに最適化されたアプリケーションの場合、N 層アプリケーションのような他の複雑なアーキテクチャも、クラウド最適化アプリケーションとして最新化することができます。

>[!div class="step-by-step"]
>[前へ](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[次へ](what-about-cloud-native-applications.md)

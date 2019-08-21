---
title: チュートリアルと技術的な概要
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |チュートリアルと技術入門概要
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660884"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>チュートリアルと技術的な概要

この電子書籍のサイズを制限するために、追加の技術ドキュメントと完全なチュートリアルは、GitHub リポジトリで入手できました。 この章で説明しているオンラインの一連のチュートリアルでは、Windows コンテナーに基づく複数の環境と Azure へのデプロイに関するステップバイステップのセットアップについて説明します。

次のセクションでは、各チュートリアルの内容、その目的、および高度なビジョンについて説明し、関連するタスクの図を示します。 チュートリアルは、「」の*eShopModernizing* apps GitHub リポジトリ wiki <https://github.com/dotnet-architecture/eShopModernizing/wiki>で入手できます。

## <a name="technical-walkthrough-list"></a>技術的なチュートリアルの一覧

次の入門チュートリアルでは、コンテナーを使用してリフトアンドシフトできるサンプルアプリについて、一貫性のある包括的な技術ガイダンスを提供し、Azure での複数のデプロイの選択肢を使用して移動することができます。

次の各チュートリアルでは、GitHub <https://github.com/dotnet-architecture/eShopModernizing>ので入手できる新しいサンプル eShopLegacy と eShopModernizing アプリを使用します。

- **EShop レガシアプリのツアー (最新化するベースラインアプリ)**

- **Windows コンテナーを使用した既存の ASP.NET web アプリ (WebForms & MVC) のコンテナー化**

- **Windows コンテナーを使用した既存の WCF サービス (N 層アプリ) のコンテナー化**

- **Windows コンテナーベースのアプリを Azure Vm にデプロイする**

- **Windows コンテナーベースのアプリを Azure Container Service の Kubernetes に展開する**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>チュートリアル 1:EShop レガシアプリのツアー

### <a name="technical-walkthrough-availability"></a>テクニカルチュートリアルの可用性

完全な技術チュートリアルについては、eShopModernizing GitHub リポジトリ wiki を参照してください。

[eShopModernizing wiki のチュートリアル](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>概要

このチュートリアルでは、3つのサンプルレガシアプリケーションの初期実装について説明します。 最初の2つのサンプル web アプリはモノリシックアーキテクチャを備えており、従来の ASP.NET を使用して作成されています。 1つのアプリケーションは ASP.NET 4.x MVC に基づいています。2番目のアプリケーションは、ASP.NET 4.x Web フォームに基づいています。
3番目のアプリケーションは、クライアント WinForms アプリとサーバー側[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)サービスによって構成される3層アプリです。

これらのアプリケーションはすべて、 [EShopModernizing GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)で入手できます。

### <a name="goals"></a>目標

このチュートリアルの主な目的は、これらのアプリとそのコードと構成をよく理解することです。 テスト目的で、SQL database を使用せずに、モックデータを生成して使用するようにアプリを構成することができます。 このオプションの構成は、分離された方法で依存関係の挿入に基づいています。

### <a name="scenario-1-aspnet-web-apps"></a>シナリオ 1:ASP.NET Web apps

次の図は、元のレガシ ASP.NET web アプリケーションの単純なシナリオを示しています。

![元のレガシ ASP.NET web アプリケーションの単純なアーキテクチャシナリオ](./media/image5-1.png)

ビジネスドメインの観点から見ると、どちらのアプリも同じカタログ管理機能を提供しています。 EShop enterprise チームのメンバーは、アプリを使用して、製品カタログを表示および編集します。

次の図は、最初のアプリのスクリーンショットを示しています。

![ASP.NET MVC と ASP.NET Web フォームアプリケーション (既存/レガシテクノロジ)](./media/image5-2.png)

ASP.NET 4.x またはそれ以前のバージョンの依存関係 (MVC の場合または Web フォームの場合) は、ASP.NET Core MVC を使用してコードを完全に書き直す場合を除き、これらのアプリケーションが .NET Core で実行されないことを意味します。

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>例 2:WCF サービスと WinForms クライアントアプリ (3 層アプリ)

次の図は、元の3層レガシアプリケーションの単純なシナリオを示しています。

![WCF サービスと WinForms クライアントアプリを使用した、元の従来の3層アプリのシンプルなアーキテクチャシナリオ](./media/image5-1.5.png)

### <a name="benefits"></a>利点

このチュートリアルの利点は単純です。コードと初期アプリについて理解を深めましょう。

### <a name="next-steps"></a>次の手順

このコンテンツについて詳しくは、GitHub wiki をご覧ください。

- [ベースライン ASP.NET MVC と Web フォームの "レガシ" アプリに関するツアー](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [ベースライン WCF サービスと WinForms (3 層) "従来の" アプリのツアー](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>チュートリアル 2:既存の .NET アプリケーションを Windows コンテナーにコンテナー化

### <a name="overview"></a>概要

Windows コンテナーを使用すると、MVC、Web フォーム、WCF などの既存の .NET アプリケーションを、運用環境、開発環境、およびテスト環境に展開しやすくなります。

### <a name="goals"></a>目標

このチュートリアルの目的は、既存の .NET Framework アプリケーションをコンテナー化するためのいくつかのオプションについて説明することです。 次の操作を行うことができます。

- [Visual studio 2017 Tools For Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual studio 2017 またはそれ以降のバージョン) を使用してアプリケーションをコンテナー化します。

- 手動で[Dockerfile](https://docs.docker.com/engine/reference/builder/)を追加し、 [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)を使用して、アプリケーションをコンテナー化します。

- [Img2Docker](https://github.com/docker/communitytools-image2docker-win)ツール (Docker からオープンソースツール) を使用して、アプリケーションをコンテナー化します。

このチュートリアルでは、Visual Studio 2017 Tools for Docker アプローチに焦点を当てていますが、Dockerfiles の使用に関しては、他の2つの方法は非常に似ています。

### <a name="scenario-1-containerized-aspnet-web-apps"></a>シナリオ 1:コンテナー化された ASP.NET web アプリ

次の図は、コンテナー化された eShop レガシ web apps アプリケーションのシナリオを示しています。

![開発環境でのコンテナー化された ASP.NET アプリケーションの簡略化されたアーキテクチャダイアグラム](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>例 2:コンテナー化された WCF サービス

次の図は、コンテナー化された WCF サービスを使用した3層アプリケーションのシナリオを示しています。

![開発環境でのコンテナー化された WCF サービスの簡略化されたアーキテクチャダイアグラム](./media/image5-3.5.png)

### <a name="benefits"></a>利点

コンテナーでモノリシックアプリケーションを実行することには利点があります。 まず、アプリケーションのイメージを作成します。 この時点から、すべての配置は同じ環境で実行されます。 すべてのコンテナーは同じバージョンの OS を使用し、同じバージョンの依存関係をインストールし、同じ .NET framework バージョンを使用します。また、同じプロセスを使用してビルドされます。 基本的には、Docker イメージを使用して、アプリケーションの依存関係を制御します。 コンテナーをデプロイすると、依存関係はアプリケーションと共に移動します。

さらに、開発者は Windows コンテナーによって提供される一貫性のある環境でアプリケーションを実行できるという利点もあります。 特定のバージョンでのみ表示される問題は、ステージング環境または運用環境ではなく、すぐに発見できます。 開発チームのメンバーが使用する開発環境の違いは、アプリケーションがコンテナーで実行される場合にはあまり重要ではありません。

コンテナー化されたアプリケーションには、flatter のスケールアウト曲線もあります。 コンテナー化されたアプリを使用すると、コンピューターごとの通常のアプリケーション展開と比較して、VM または物理マシンに、(コンテナーに基づく) より多くのアプリケーションとサービスインスタンスを作成できます。 これにより、特に Kubernetes のようなオーケストレーター使用する場合に、より高密度で必要なリソースが減少します。

コンテナー化は、理想的な状況では、アプリケーションコード (C\#) に変更を加える必要はありません。 ほとんどのシナリオでは、Docker 配置メタデータファイル (Dockerfiles および Docker Compose ファイル) が必要です。

### <a name="next-steps"></a>次の手順

このコンテンツについて詳しくは、GitHub wiki をご覧ください。

- [Windows コンテナーと Docker を使用して .NET Framework web アプリをコンテナー化する方法](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [WCF サービスへの Docker サポートの追加](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>チュートリアル 3:Windows コンテナーベースのアプリを Azure Vm にデプロイする

### <a name="technical-walkthrough-availability"></a>テクニカルチュートリアルの可用性

完全な技術チュートリアルについては、eShopModernizing GitHub リポジトリ wiki を参照してください。<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>概要

Azure の Windows Server 2016 仮想マシン (VM) 上の Docker ホストにデプロイすると、開発/テスト/ステージング環境をすばやく設定できます。 また、テスト担当者またはビジネスユーザーがアプリを検証するための一般的な場所も提供します。 Vm は、サービスとしてのインフラストラクチャ (IaaS) 運用環境としても有効です。

### <a name="goals"></a>目標

このチュートリアルの目的は、windows Server 2016 以降のバージョンを基盤とする Azure Vm に Windows コンテナーを展開するときに、複数の選択肢を紹介することです。

### <a name="scenarios"></a>シナリオ

このチュートリアルでは、いくつかのシナリオについて説明します。

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>シナリオ A:Docker エンジン接続を介して開発用 PC から Azure VM にデプロイする

![Docker エンジン接続を使用して開発用 PC から Azure VM にデプロイする](./media/image5-4.png)

**図 5-4** Docker エンジン接続を使用して開発用 PC から Azure VM にデプロイする

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>シナリオ B:Docker レジストリを使用して Azure VM にデプロイする

![Docker レジストリを使用して Azure VM にデプロイする](./media/image5-5.png)

**図 5-5** Docker レジストリを使用して Azure VM にデプロイする

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>シナリオ C:Azure DevOps Services の CI/CD パイプラインから Azure VM にデプロイする

![Azure DevOps Services の CI/CD パイプラインから Azure VM にデプロイする](./media/image5-6.png)

**図 5-6** Azure DevOps Services の CI/CD パイプラインから Azure VM にデプロイする

### <a name="azure-vms-for-windows-containers"></a>Windows コンテナー用の Azure Vm

Windows コンテナー用の Azure Vm は、Docker エンジンがセットアップされている Windows Server 2016、Windows 10 以降のバージョンに基づく Vm です。 ほとんどの場合、Azure Vm では Windows Server 2016 が使用されます。

Azure では現在、 **Windows Server 2016**という名前の VM とコンテナーを提供しています。 この VM を使用して、windows Server Core または Windows Nano Server のいずれかを使用して、新しい Windows Server コンテナー機能を試すことができます。 コンテナー OS イメージがインストールされた後、VM を Docker で使用する準備ができました。

### <a name="benefits"></a>利点

Windows コンテナーはオンプレミスの Windows Server 2016 Vm にデプロイできますが、Azure にデプロイすると、すぐに使い始めることができる Windows Server コンテナー Vm を使用して簡単に開始できます。 また、テスト担当者は、Azure 仮想マシンスケールセットを通じて自動的にスケーラビリティを利用できる、一般的なオンラインの場所も取得できます。

### <a name="next-steps"></a>次の手順

このコンテンツについて詳しくは、GitHub wiki をご覧ください。

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>チュートリアル 4:Windows コンテナーベースのアプリを Azure Container Instances (ACI) に展開する

### <a name="technical-walkthrough-availability"></a>テクニカルチュートリアルの可用性

完全な技術チュートリアルについては、eShopModernizing GitHub リポジトリ wiki を参照してください。

[ACI へのアプリの展開 (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>概要

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)は、コンテナーの開発/テスト/ステージング環境を作成するための最も簡単な方法です。コンテナーの1つのインスタンスをデプロイできます。

### <a name="goals"></a>目標

このチュートリアルでは、Azure Container Instances (ACI) に Windows コンテナーを展開する主なシナリオと、eShopModernizing アプリを ACI に展開する方法について説明します。

### <a name="scenarios"></a>シナリオ

1つまたはすべてのアプリ (MVC アプリ、WebForms app、または WCF サービス) をデプロイするなど、eShopModernizing アプリを ACI にデプロイすることにはさまざまなバリエーションがあります。 次に示すシナリオでは、ASP.NET MVC アプリと SQL Server コンテナーの両方が、コンテナーとして ACI (Azure Container Instances) に展開されていることを確認できます。

![開発環境から ACI にデプロイする](./media/image5-3.5.6.png)

### <a name="benefits"></a>利点

Azure Container Instances を使用すると、仮想マシンをプロビジョニングしたり、より高いレベルのサービスを採用したりしなくても、Azure で Docker コンテナーの作成と管理を簡単に行うことができます。 ACI を使用すると、Windows コンテナーを Azure に直接デプロイし、数秒で完全修飾ドメイン名 (FQDN) を使用してインターネットに公開することができます (Docker Hub や Azure Container などの Docker レジストリで Windows コンテナーイメージを準備している場合)。レジストリ)。

### <a name="considerations"></a>考慮事項

完全 .NET Framework/ASP.NET または SQL Server を使用した Windows コンテナーの展開は Azure Container Instances (ACI) ではありません。 Docker イメージは、次のように、通常の Docker ホストに展開するのと同じくらい高速ではありません (windows コンテナーを使用した Windows Server 2016 など)。SQL コンテナーイメージ (15.1 GB) と ASP.NET container image (13.9 GB) のサイズは、毎回 (Docker レジストリからプルされて) ダウンロードされますが、独自の Docker ホストを維持するよりもはるかにコストがかかります (完全にオンラインAzure の Windows コンテナー VM を使用した windows Server 2016) は、一方で、運用環境のデプロイに最適な選択肢である Azure の Kubernetes (AKS) のような orchestrator 全体を示すものではありません。

主要な結論として、Azure Container Instances を使用することは、開発/テストシナリオおよび CI/CD パイプラインの非常に説得力のあるオプションです。

## <a name="next-steps"></a>次の手順

このコンテンツについて詳しくは、GitHub wiki をご覧ください。

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>チュートリアル 5:Windows コンテナーベースのアプリを Azure Container Service の Kubernetes に展開する

### <a name="technical-walkthrough-availability"></a>テクニカルチュートリアルの可用性

完全な技術チュートリアルについては、eShopModernizing GitHub リポジトリ wiki を参照してください。

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>概要

Windows コンテナーに基づくアプリケーションでは、IaaS Vm からさらに離れた場所でも、プラットフォームをすばやく使用する必要があります。 これは、高いスケーラビリティと自動化されたスケーラビリティを簡単に実現するために必要であり、自動化された配置とバージョン管理の大幅な改善にも使用されます。 これらの目標は、 [Azure Container Services](https://azure.microsoft.com/services/container-service/)で利用できる orchestrator [Kubernetes](https://kubernetes.io/)を使用して実現できます。

### <a name="goals"></a>目標

このチュートリアルの目的は、Azure Container Service で Windows コンテナーベースのアプリケーションを Kubernetes ( *K8s*とも呼ばれます) に展開する方法について説明することです。 最初から Kubernetes への配置は、次の2段階のプロセスです。

1. Azure Container Service に Kubernetes クラスターをデプロイします。

2. アプリケーションと関連リソースを Kubernetes クラスターにデプロイします。

### <a name="scenarios"></a>シナリオ

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>シナリオ A:開発環境から Kubernetes クラスターに直接デプロイする

![開発環境から Kubernetes クラスターに直接デプロイする](./media/image5-7.png)

**図 5-7** 開発環境から Kubernetes クラスターに直接デプロイする

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>シナリオ B:Azure DevOps Services の CI/CD パイプラインから Kubernetes クラスターにデプロイする

![Azure DevOps Services の CI/CD パイプラインから Kubernetes クラスターにデプロイする](./media/image5-8.png)

**図 5-8** Azure DevOps Services の CI/CD パイプラインから Kubernetes クラスターにデプロイする

### <a name="benefits"></a>利点

Kubernetes でクラスターにデプロイすることには多くの利点があります。 最大の利点は、使用するコンテナーインスタンスの数 (既存のノードの内部スケーラビリティ) に基づいてアプリケーションをスケールアウトし、クラスター内のノードまたは Vm の数に基づいて、運用環境に対応した環境を実現できることです (クラスターのグローバルなスケーラビリティ)。

Azure Container Service は、Azure 専用の広く普及しているオープンソースのツールとテクノロジを最適化します。 コンテナーとアプリケーションの構成の両方について、移植性を提供するオープンソリューションを利用できます。 サイズ、ホスト数、および orchestrator ツールを選択します。コンテナーサービスは、他のすべてを処理します。

Kubernetes を使用すると、開発者は物理マシンと仮想マシンについて考えることができ、次のような機能を容易にするコンテナー中心のインフラストラクチャを計画することができます。

- 複数のコンテナーに基づくアプリケーション

- コンテナーインスタンスと水平方向の自動スケールのレプリケート

- 名前付けと検出 (例、内部 DNS)

- 負荷分散

- ローリングアップデート

- シークレットの配布

- アプリケーションの正常性チェック

## <a name="next-steps"></a>次の手順

このコンテンツについて詳しくは、GitHub wiki をご覧ください。<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>チュートリアル 6:コンテナー用の Azure App Service に Windows コンテナーベースのアプリを展開する

### <a name="technical-walkthrough-availability"></a>テクニカルチュートリアルの可用性

完全な技術チュートリアルについては、eShopModernizing GitHub リポジトリ wiki を参照してください。

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>概要

Windows コンテナーを使用する単純なコンテナー化されたアプリケーションは、コンテナーの Azure App Service に簡単にデプロイできます。 これは、ほとんどの Windows コンテナーベースのアプリケーションで推奨される方法です。

### <a name="goals"></a>目標

このチュートリアルの目的は、Windows コンテナーベースのアプリケーションを展開して、レジストリ (Docker Hub または Azure Container Registry) からコンテナーを Azure App Service する方法について説明することです。

### <a name="scenario"></a>シナリオ

![コンテナーの Azure App Service に Windows コンテナーベースのアプリを展開する](./media/image5-11.png)

### <a name="benefits"></a>利点

コンテナーの Azure App Service にデプロイすると、コンテナーの利点と Azure App Service の PaaS の利点との組み合わせが実現します。 App service は、垂直方向と水平方向の両方で簡単にスケーリングでき、変化する需要に合わせて自動スケールするように構成できます。 更新はダウンタイムなしで実行でき、レジストリからの継続的な展開の構成も簡単に構成できます。

## <a name="next-steps"></a>次の手順

このコンテンツについて詳しくは、GitHub wiki をご覧ください。<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [前へ](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [次へ](conclusions.md) <!-- Next Chapter -->

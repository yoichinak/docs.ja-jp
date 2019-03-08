---
title: チュートリアルと技術的な概要します。
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |チュートリアルと技術的な概要します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 15ea074693a75aa04b4f3a03e6e5e3d7f748cea1
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674940"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>チュートリアルと技術的な概要します。

この電子ブックのサイズを制限するには、その他の技術ドキュメントと完全なチュートリアルで行われた使用可能な GitHub リポジトリ。 オンラインの一連のこの章で説明したチュートリアルでは、Windows コンテナー、および Azure へのデプロイに基づいて複数の環境のステップ バイ ステップのセットアップについて説明します。

次のセクションでは、各チュートリアルでは、その目標と高度なビジョンを通知し、関連するタスクを次の図は、について説明します。 自体のチュートリアルを入手できますで、 *eShopModernizing*でアプリの GitHub リポジトリ wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)します。

## <a name="technical-walkthrough-list"></a>技術チュートリアルの一覧

次の概要チュートリアルでは、リフトとシフト、コンテナーを使用しておよび Azure で複数の展開のオプションを使用して、移動できるサンプル アプリの包括的な一貫性のあるの技術的なガイダンスを提供します。

次のチュートリアルの各アプリで使用して、新しいサンプル eShopLegacy と eShopModernizing、GitHub で利用できる[ https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)します。

- **EShop レガシ アプリ (現代化する基準アプリ) のツアー**

- **Windows コンテナーで既存 ASP.NET web アプリ (WebForms および MVC) のコンテナー格納します。**

- **Windows コンテナーで既存の WCF サービス (N 層アプリ) のコンテナー格納します。**

- **Azure Vm への Windows コンテナー ベース アプリをデプロイします。**

- **Windows コンテナー ベースのアプリを Azure Container Service で Kubernetes にデプロイします。**

- **Azure Service Fabric への Windows コンテナー ベースのアプリをデプロイします。**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>チュートリアル 1:EShop レガシ アプリケーションのツアー

### <a name="technical-walkthrough-availability"></a>テクニカル チュートリアルの可用性

完全な技術チュートリアル、eShopModernizing GitHub リポジトリ wiki で提供されています。

[wiki のチュートリアルは eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>概要

このチュートリアルでは、次の 3 つのサンプルのレガシ アプリケーションの最初の実装を確認できます。 最初の 2 つのサンプル web アプリは、モノリシック アーキテクチャがあるし、従来の ASP.NET を使用して作成されました。 1 つのアプリケーション ベースは ASP.NET 4.x MVC;2 番目のアプリケーションは、ASP.NET 4.x Web フォームに基づきます。
3 番目のアプリは、WinForms アプリをクライアントとサーバー側で構成されます 3 層アプリ[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)サービス。

これらすべてのアプリケーションは、 [eShopModernizing GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)します。

### <a name="goals"></a>目的

このチュートリアルの主な目的は、これらのアプリとそのコードと構成について詳しく理解することです。 生成およびテスト目的で、SQL database を使用せず、モックのデータを使用できるように、アプリを構成できます。 このオプションの構成は、分離された方法で依存関係の挿入に基づいています。

### <a name="scenario-1-aspnet-web-apps"></a>シナリオ 1:ASP.NET Web アプリ

次の図は、元の従来の ASP.NET web アプリケーションの簡単なシナリオを示します。

![元の従来の ASP.NET web アプリケーションのアーキテクチャの単純なシナリオ](./media/image5-1.png)

ビジネス ドメインの観点から両方のアプリは管理機能に同じカタログを提供します。 EShop エンタープライズ チームのメンバーでは、製品カタログの編集を表示したり、アプリを使用します。

次の図は、最初のアプリのスクリーン ショットを示します。

![ASP.NET MVC と ASP.NET Web フォーム アプリケーション (既存の/レガシ テクノロジ)](./media/image5-2.png)

依存関係 asp.net 4.x または以前のバージョン (MVC または Web フォームか) はこれらのアプリケーションは、ASP.NET Core MVC を使用してコードを書き直すが完全にしない限り、.NET Core で動作しません。

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>シナリオ 2:WCF サービスとクライアント アプリの WinForms (3 層アプリ)

次の図は、元の 3 層のレガシ アプリケーションの簡単なシナリオを示します。

![WCF サービスと、元のレガシ 3 層アプリおよび WinForms クライアント アプリのアーキテクチャの単純なシナリオ](./media/image5-1.5.png)

### <a name="benefits"></a>利点

このチュートリアルの利点はシンプルです。コードと最初のアプリを使用して理解します。

### <a name="next-steps"></a>次の手順

このコンテンツの詳細については、GitHub wiki 詳細します。

- [ASP.NET MVC、ベースラインをツアーと Web フォーム「レガシ」アプリ](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
-   [WCF サービスの基準と WinForms (3 層) の「レガシ」アプリのツアー](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>チュートリアル 2:Windows コンテナーで既存の .NET アプリケーションのコンテナー格納します。

### <a name="overview"></a>概要

MVC、Web フォーム、または WCF では、運用、開発、およびテスト環境に基づくように、既存の .NET アプリケーションの展開を向上させるために Windows コンテナーを使用します。

### <a name="goals"></a>目的

このチュートリアルの目的では、既存の .NET Framework アプリケーションをコンテナー化のいくつかのオプションを説明します。 次の操作を行うことができます。

- 使用して、アプリケーションをコンテナー化[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 またはそれ以降のバージョン)。

- 手動で追加することで、アプリケーションをコンテナー化、 [Dockerfile](https://docs.docker.com/engine/reference/builder/)、しを使用して、 [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)します。

- 使用して、アプリケーションをコンテナー化、 [Img2Docker](https://github.com/docker/communitytools-image2docker-win)ツール (Docker からオープン ソース ツール)。

このチュートリアルは、Docker 方法は、Visual Studio 2017 Tools について重点的に取り上げます。 が、その他の 2 つのアプローチは Dockerfile を使用してに関して類似しています。

### <a name="scenario-1-containerized-aspnet-web-apps"></a>シナリオ 1:コンテナー化された ASP.NET web アプリ

次の図は、コンテナー化された eShop 従来の web アプリのアプリケーションのシナリオを示します。

![簡素化されたアーキテクチャの図は、開発環境での ASP.NET アプリケーションをコンテナー化されました。](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>シナリオ 2:コンテナー化された WCF サービス

次の図は、コンテナー化された WCF サービスと 3 層アプリケーションのシナリオを示します。

![開発環境でコンテナー化された WCF サービスのアーキテクチャ図を簡略化](./media/image5-3.5.png)

### <a name="benefits"></a>利点

これには、コンテナーで、モノリシック アプリケーションを実行する利点があります。 最初に、アプリケーションのイメージを作成します。 その時点からは、すべてのデプロイは、同じ環境内で実行されます。 すべてのコンテナーで、同じ OS バージョンを使用して、同じバージョンの依存関係のインストールが同じ .NET framework のバージョンを使用しておよびは同じプロセスを使用して構築されています。 基本的には、Docker イメージを使用して、アプリケーションの依存関係を制御します。 依存関係は、コンテナーをデプロイするときに、アプリケーションと共に移動します。

その他の利点は、開発者が Windows のコンテナーによって提供される一貫した環境でアプリケーションを実行できることです。 特定のバージョンでのみ表示される問題は、ステージング環境または運用環境で表示することではなく、すぐに発見できます。 開発チームのメンバーで使用される開発環境での相違点は問題のコンテナーでアプリケーションの実行時に小さいです。

コンテナー化されたアプリケーションでは、flatter スケール アウト曲線もあります。 コンテナー化されたアプリには、VM または物理マシンのマシンあたりの定期的なアプリケーション展開と比較する複数のアプリケーションとサービス インスタンスが (コンテナーに基づく) が有効にします。 これにより、高密度、および必要な少なくリソース、Kubernetes や Service Fabric などのオーケストレーターを使用する場合に特にです。

コンテナリゼーションは、理想的な状況では、アプリケーション コードに変更を加える必要ありません (C\#)。 ほとんどのシナリオでは、Docker の展開のメタデータ ファイル (Dockerfile と Docker Compose ファイル) だけ必要です。

### <a name="next-steps"></a>次の手順

このコンテンツの詳細については、GitHub wiki 詳細します。

- [Windows コンテナーと Docker で .NET Framework web アプリをコンテナー化する方法](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [WCF サービスへの Docker サポートの追加](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>チュートリアル 3:Azure Vm への Windows コンテナー ベース アプリをデプロイします。

### <a name="technical-walkthrough-availability"></a>テクニカル チュートリアルの可用性

完全な技術チュートリアル、eShopModernizing GitHub リポジトリ wiki で提供されています。 [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>概要

Azure で Windows Server 2016 仮想マシン (VM) 上の Docker ホストに展開するには、開発/テスト/ステージング環境をすばやくセットアップすることができます。 アプリを検証するには、テスト担当者またはビジネス ユーザーの一般的な場所も提供します。 Vm は、サービス (IaaS) の実稼働環境として有効なインフラストラクチャをすることができます。

### <a name="goals"></a>目的

このチュートリアルの目的では、Windows Server 2016 またはそれ以降のバージョンに基づいて Azure Vm を Windows コンテナーを展開する場合がある複数の代替手段を説明します。

### <a name="scenarios"></a>シナリオ

このチュートリアルでは、いくつかのシナリオがについて説明します。

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>シナリオ a:Docker エンジンの接続を介して開発用 PC から Azure VM へのデプロイします。

![Docker エンジンの接続を介して開発用 PC から Azure VM へのデプロイします。](./media/image5-4.png)

**図 5-4** Docker エンジンの接続を介して開発用 PC から Azure VM へのデプロイします。

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>シナリオ b:Docker レジストリを使用して Azure VM にデプロイします。

![Docker レジストリを使用して Azure VM にデプロイします。](./media/image5-5.png)

**図 5-5** Docker レジストリを使用して Azure VM にデプロイします。

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>C: のシナリオAzure DevOps Services で CI/CD パイプラインから Azure VM へのデプロイします。

![Azure DevOps Services で CI/CD パイプラインから Azure VM へのデプロイします。](./media/image5-6.png)

**図 5-6** Azure DevOps Services で CI/CD パイプラインから Azure VM へのデプロイします。

### <a name="azure-vms-for-windows-containers"></a>Windows コンテナー用の azure Vm

Windows コンテナーの azure Vm は Vm の Windows Server 2016、Windows 10、またはそれ以降のバージョンに基づいて、Docker エンジンの両方を設定します。 ほとんどの場合は、Windows Server 2016 は Azure Vm で使用されます。

Azure は、現在という名前の VM を提供します。 **Windows Server 2016 with Containers**します。 この VM を使用すると、Windows Server Core または Windows Nano Server のいずれかで、新しい Windows Server コンテナー機能をお試しください。 コンテナー OS イメージがインストールされている場合、および Docker を使用する準備が VM でし。

### <a name="benefits"></a>利点

Windows コンテナーは、Azure にデプロイするときに、オンプレミス Windows Server 2016 の Vm を展開できますが、すぐに使用できる Windows Server コンテナーの Vm を開始する簡単な方法を取得します。 テスト担当者、および自動のスケーラビリティを Azure の仮想マシン スケール セットにアクセスできる一般的なオンラインの場所も表示します。

### <a name="next-steps"></a>次の手順

このコンテンツの詳細については、GitHub wiki 詳細します。

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>チュートリアル 4:Azure Container Instances (ACI) への Windows コンテナー ベースのアプリをデプロイします。

### <a name="technical-walkthrough-availability"></a>テクニカル チュートリアルの可用性

完全な技術チュートリアル、eShopModernizing GitHub リポジトリ wiki で提供されています。

[ACI (Azure Container Instances) に、アプリを展開します。](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>概要

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)はコンテナーの 1 つのインスタンスをデプロイするコンテナーの開発/テスト/ステージング環境に最も簡単な方法です。

### <a name="goals"></a>目的

このチュートリアルでは、主なシナリオ Azure Container Instances (ACI) ACI に eShopModernizing アプリをデプロイする方法を Windows コンテナーをデプロイするときにします。

### <a name="scenarios"></a>シナリオ

ACI に eShopModernizing アプリを展開する 1 つまたはすべてのアプリ (MVC アプリ、web フォーム アプリケーションまたは WCF サービス) の展開などについてのバリエーションがあります。 次のシナリオを次に示すことができます、コンテナーとして ACI (Azure Container Instances) に ASP.NET MVC アプリとこれらの両方に展開されている SQL Server のコンテナーを表示します。

![開発環境から ACI へのデプロイします。](./media/image5-3.5.6.png)

### <a name="benefits"></a>利点

Azure Container Instances では、簡単に作成し、仮想マシンをプロビジョニングしたり、上位レベルのサービスを採用したりしなくても、Azure で Docker コンテナーを管理します。 、ACI で直接 Azure で Windows コンテナーのデプロイし、への公開を完全修飾ドメイン名 (FQDN) を使用してインターネットに数秒 (Docker Hub や Azure コンテナーのような Docker レジストリで準備ができて、Windows コンテナー イメージがある場合にすることができますレジストリの場合)。

### <a name="considerations"></a>注意事項

いずれかの完全な .NET Framework と Windows コンテナーのデプロイ]、[ASP.NET または SQL Server Azure Container Instances (ACI) には、Docker イメージがあるためです (Windows コンテナーでの Windows Server 2016) などの通常の Docker ホストにデプロイする場合と非常に高速ではありません(Docker レジストリからプルされた) たびにダウンロードし、これは、独自の docker ホスト (永続的にオンラインを維持するよりもよりもコストは、SQL コンテナー イメージ (15.1 GB) と ASP.NET のコンテナー イメージ (13.9 GB) のサイズが非常に大きい場合、Azure で Windows コンテナーの VM で Windows Server 2016) することで、全体のオーケストレーターは、その一方で、運用環境のデプロイ用の優れた選択肢である Kubernetes (AKS/ACS) を Azure または Azure Service Fabric でのようにします。

メインの結論としては、Azure Container Instances を使用して開発/テスト シナリオの場合と CI/CD パイプラインの非常に魅力的なオプション。

## <a name="next-steps"></a>次の手順

このコンテンツの詳細については、GitHub wiki 詳細します。

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>チュートリアル 5:Windows コンテナー ベースのアプリを Azure Container Service で Kubernetes にデプロイします。

### <a name="technical-walkthrough-availability"></a>テクニカル チュートリアルの可用性

完全な技術チュートリアル、eShopModernizing GitHub リポジトリ wiki で提供されています。

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>概要

Windows コンテナーに基づいているアプリケーションはすばやく離れたから IaaS Vm の移動、さらに、プラットフォームを使用する必要があります。 これを簡単に高いスケーラビリティを実現するために必要なよりスケーラビリティ、自動し、大幅に向上のデプロイとバージョン管理を自動化します。 これらの目標を達成するには、orchestrator を使用して[Kubernetes](https://kubernetes.io/)で使用できる、 [Azure Container Services](https://azure.microsoft.com/services/container-service/)します。

### <a name="goals"></a>目的

このチュートリアルの目標は Kubernetes への Windows コンテナー ベースのアプリケーションをデプロイする方法を理解する (とも呼ばれる*K8s*) で Azure Container Service。 ゼロからの Kubernetes にデプロイすると、2 段階のプロセスです。

1. Azure Container Service に Kubernetes クラスターをデプロイします。

2. Kubernetes クラスターに、アプリケーションと関連リソースをデプロイします。

### <a name="scenarios"></a>シナリオ

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>シナリオ a:開発環境から Kubernetes クラスターに直接デプロイします。

![開発環境から Kubernetes クラスターに直接デプロイします。](./media/image5-7.png)

**図 5-7** 開発環境から Kubernetes クラスターに直接デプロイします。

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>シナリオ b:Azure DevOps Services で CI/CD パイプラインから Kubernetes クラスターにデプロイします。

![Azure DevOps Services で CI/CD パイプラインから Kubernetes クラスターにデプロイします。](./media/image5-8.png)

**図 5-8** Azure DevOps Services で CI/CD パイプラインから Kubernetes クラスターにデプロイします。

### <a name="benefits"></a>利点

Kubernetes でのクラスターにデプロイする多くの利点があります。 最大のメリットは (既存のノードでは内部スケーラビリティ) を使用して、クラスター (ノードまたは Vm の数に基づくコンテナー インスタンスの数に基づいて、アプリケーションをスケールすることができます、実稼働可能な環境を取得します。グローバルなスケーラビリティ、クラスターの)。

Azure Container Service では、Azure 向けに人気のあるオープン ソース ツールとテクノロジを最適化します。 移植性、コンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。 ホストの数、サイズを選択し、orchestrator ツール-コンテナーのサービスが他のすべてを処理します。

Kubernetes で開発者を他のユーザーの間で、次の機能を容易にするコンテナーを中心としたインフラストラクチャの計画に物理および仮想マシン、考えたに進むことができます。

- 複数のコンテナーに基づくアプリケーション

- Container instances と水平方向の自動スケールをレプリケートします。

- 名前付けと (たとえば、内部 DNS) の検出

- 負荷を分散

- ローリング アップデート

- シークレットを配布します。

- アプリケーションの正常性チェック

## <a name="next-steps"></a>次の手順

このコンテンツの詳細については、GitHub wiki 詳細します。 [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>チュートリアル 6:Azure Service Fabric への Windows コンテナー ベースのアプリをデプロイします。

### <a name="technical-walkthrough-availability"></a>テクニカル チュートリアルの可用性

完全な技術チュートリアル、eShopModernizing GitHub リポジトリ wiki で提供されています。

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>概要

Windows コンテナーをすばやくに基づいてアプリケーションでは、IaaS Vm から離れて移動、さらに、プラットフォームを使用する必要があります。 これを簡単に高いスケーラビリティを実現するために必要なよりスケーラビリティ、自動し、大幅に向上のデプロイとバージョン管理を自動化します。 Azure Service Fabric は、Azure のクラウドで使用できますが、オンプレミスでも実行できますが、オーケストレーターを使用して、または別のパブリック クラウドであっても、これらの目標を実現できます。

### <a name="goals"></a>目的

このチュートリアルの目的では、Azure で Service Fabric クラスターに Windows コンテナー ベースのアプリケーションをデプロイする方法について説明します。 最初からの Service Fabric にデプロイすると、2 段階のプロセスです。

1. Azure (または、別の環境) は、Service Fabric クラスターをデプロイします。

2. Service Fabric クラスターに、アプリケーションと関連リソースをデプロイします。

### <a name="scenarios"></a>シナリオ

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>シナリオ a:開発環境から Service Fabric クラスターに直接デプロイします。

![開発環境から Service Fabric クラスターに直接デプロイします。](./media/image5-9.png)

> **図 5-9** 開発環境から Service Fabric クラスターに直接デプロイします。

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a>シナリオ b:Azure DevOps Services で CI/CD パイプラインから Service Fabric クラスターにデプロイします。

![Azure DevOps Services で CI/CD パイプラインから Service Fabric クラスターにデプロイします。](./media/image5-10.png)

**図 5-10** Azure DevOps Services で CI/CD パイプラインから Service Fabric クラスターにデプロイします。

## <a name="benefits"></a>利点

Service fabric クラスターへのデプロイの利点は、Kubernetes を使用する利点と似ています。 1 つの違いは、Service Fabric には、さらに成熟した運用環境と比較する Kubernetes バージョン 1.9 で Windows コンテナーのベータ フェーズでは、Kubernetes と Windows アプリケーション (2017 年 12 月)。 Kubernetes は、Linux のさらに成熟した環境です。

Azure Service Fabric を使用する主な利点は、(既存のノードでは内部スケーラビリティ) を使用して数に基づいてするコンテナー インスタンスの数に基づいて、アプリケーションをスケールすることができます、実稼働可能な環境を取得します。ノードまたはクラスター (クラスターのグローバルなスケーラビリティ) 内の Vm。

Azure Service Fabric では、移植性をコンテナーと、アプリケーションの構成の両方を提供します。 Azure では、クラスター化または独自のデータ センターに、オンプレミス インストールに Service Fabric ことができます。 このようなでも別のクラウドでこの Service Fabric クラスターをインストールすることができます[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)します。

Service Fabric を使用開発者を他のユーザーの間で、次の機能を容易にするコンテナーを中心としたインフラストラクチャの計画に考えた物理および仮想マシンに進むことができます。

- 複数のコンテナーに基づくアプリケーション。

- Container instances と水平方向の自動スケールをレプリケートします。

- 名前付けと (たとえば、内部 DNS) を検出します。

- 負荷を分散します。

- ローリング更新。

- シークレットを配布します。

- アプリケーションの正常性を確認します。

次の機能では、(他のオーケストレーターとの比較)、Service Fabric で排他的です。

- ステートフル サービスの機能は、Reliable Services アプリケーションのモデルを使用します。

- アクター パターン、Reliable Actors アプリケーション モデルを使用します。

- Windows または Linux のコンテナーに加え、ベア ボーン プロセスを展開します。

- 高度なローリング アップデートと正常性チェック

### <a name="next-steps"></a>次の手順

このコンテンツの詳細については、GitHub wiki 詳細します。

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

> [!div class="step-by-step"]
> [前へ](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [次へ](conclusions.md)

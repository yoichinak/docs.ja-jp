---
title: 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
description: 実際の運用アプリケーションでは、デプロイし、正常性、ワークロードおよびすべてのコンテナーのライフ サイクルを処理するオーケストレーターで管理する必要があります。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: b8c947ffc34b62204b6a370f1133111a3e2d3198
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679048"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する

アプリケーションのマイクロ サービスに基づくまたは複数のコンテナーに分割する場合、実稼働可能なアプリケーションのオーケストレーターを使用したことが不可欠です。 前述のとおり、マイクロサービス ベースの方法では、マイクロサービスはそれぞれモデルとデータを所有しているため、開発と展開の観点から自立していることになります。 ただし、複数のサービスで構成される従来のアプリケーション (SOA など) を使用する場合でも、分散システムとして展開する必要がある単一のビジネス アプリケーションを構成する複数のコンテナーまたはサービスを使用する場合もあります。 この種のシステムはスケールアウトや管理が複雑であるため、運用可能でスケーラブルな複数のコンテナー アプリケーションを使用する場合、どうしてもオーケストレーターが必要になります。

図 4-6 は、複数のマイクロ サービス (コンテナー) から成るアプリケーションのクラスターへの展開を示しています。

![クラスター内での Docker アプリケーションの構成:サービス インスタンスごとに 1 つのコンテナーを使用します。 Docker コンテナーは "配置の単位" であり、コンテナーは Docker のインスタンスです。ホストでは多くのコンテナーが処理されます。](./media/image6.png)

**図 4-6** コンテナーのクラスター

これは論理的な方法のように見えます。 しかし、どのようにする処理の負荷分散、ルーティング、およびこれらの構成済みのアプリケーションを調整することでしょうか。

Docker コマンド ライン インターフェイス (CLI) には、1 つのホスト上の 1 つのコンテナーの管理のニーズより複雑な分散アプリケーションの複数のホストに展開されている複数のコンテナーを管理する際に短いなります。 ほとんどの場合は自動的にコンテナーを開始、スケール アウト イメージごとに複数のコンテナー、中断、またはシャット ダウンするときに、必要に応じて、理想的には制御したり、ネットワークとデータなどのリソースにアクセスする方法を管理プラットフォームが必要があります。記憶域。

だけでなく、個別のコンテナーまたは単純な構成アプリとマイクロ サービスで大規模なエンタープライズ アプリケーションへの移行の管理、オーケストレーション プラットフォームをクラスタ リングを有効にする必要があります。

アーキテクチャと開発の観点から、マイクロ サービス ベースの構築、大規模なエンタープライズをしているアプリケーションは次のプラットフォームと高度なシナリオをサポートする製品を理解しておく必要。

- **クラスターとオーケストレーター。** 多くの Docker ホストでアプリケーションをスケールする必要がある場合など、大規模なマイクロ サービス ベースのアプリケーションにすることが重要、基になるプラットフォームの複雑さを抽象化によって 1 つのクラスターとしてそれらのホストのすべてを管理できるようにします。 それは、コンテナー クラスターとオーケストレーターによって実現されるものです。 オーケストレーターの例としては、Azure Service Fabric や Kubernetes が挙げられます。 Kubernetes は、Azure Kubernetes Service を介して Azure で利用可能です。

- **スケジューラ。** *スケジューリング*スケジューラは、これを行うためのユーザー インターフェイスを提供することも、クラスターでは、コンテナーを起動するには管理者の機能を搭載することを意味します。 クラスター スケジューラにはいくつかの役割があります。たとえば、クラスターのリソースを効率的に使用すること、ユーザーによって指定される制約を設定すること、ノードまたはホスト全体でのコンテナーの負荷分散を効率的に行うこと、高可用性を提供すると同時にエラーに対して堅牢であることなどです。

クラスターとスケジューラの概念は密接に関連しており、さまざまなベンダーによって提供される製品では、多くの場合、両方の機能セットが提供されます。 以下のセクションでは、最も重要なプラットフォームとクラスターとスケジューラーがあるソフトウェアの選択肢を示します。 これらのオーケストレーターは、Azure などのパブリック クラウドに広く提供されます。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>コンテナーのクラスタリング、オーケストレーション、スケジューリングのためのソフトウェア プラットフォーム

| プラットフォーム | コメント |
|:---:|:---|
| **Kubernetes** <br/> ![Kubernetes のロゴ](./media/kubernetes-logo.png) | [*Kubernetes*](https://kubernetes.io/) はオープンソースの製品であり、クラスターのインフラストラクチャとコンテナーのスケジューリングからオーケストレーションまでのさまざまな機能を提供します。 ホストのクラスター全体のアプリケーション コンテナーの展開、スケーリング、操作を自動化できます。 <br/> <br/> *Kubernetes* ではコンテナー中心のインフラストラクチャが提供され、アプリケーション コンテナーを論理ユニットにグループ化し、管理と検出を容易にします。 <br/> <br/> *Kubernetes* は Linux では完成されていますが、Windows では未完成です。 |
| **Azure Kubernetes Service (AKS)** <br/> ![Azure Kubernetes サービスのロゴ](./media/aks-logo.png) | [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) は Azure でのマネージド Kubernetes コンテナー オーケストレーション サービスで。これによって Kubernetes クラスターの管理、デプロイ、および操作が簡略化されます。 |
| **Azure Service Fabric** <br/> ![Azure Service Fabric のロゴ](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) は、アプリケーションを構築するための Microsoft マイクロサービス プラットフォームです。 これはサービスの[オーケストレーター](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)であり、これによってマシンのクラスターが作成されます。 Service Fabric は、サービスをコンテナーまたはプレーン プロセスとして展開できます。 同じアプリケーションとクラスター内にコンテナーのサービスとプロセスのサービスを混在させることもできます。 <br/> <br/> *Service Fabric* クラスターは、Azure、オンプレミス、または任意のクラウドに配置できます。 ただし、Azure でのデプロイはマネージド アプローチで簡略化されます。 <br/> <br/> *Service Fabric* では、[ステートフル サービス](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/)や [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/) などの追加の省略可能な規範的な [Service Fabric プログラミング モデル](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/)が提供されます。 <br/> <br/> *Service Fabric* は Windows (年々進化している Windows) では完成されていますが、Linux では未完成です。 <br/> <br/> Linux と Windows の両方のコンテナーは、2017 年以降の Service Fabric でサポートされています。 |
| **Azure Service Fabric のメッシュ** <br/> ![Azure Service Fabric のメッシュのロゴ](./media/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric のメッシュ*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview)信頼性、ミッション クリティカルなパフォーマンスと Service Fabric では、小数点以下桁数を提供していますが、完全に管理およびサーバーレス プラットフォームも提供します。 クラスター、VM、ストレージ、またはネットワーク構成を管理する必要はありません。 ご自分のアプリケーションの開発に集中できます。 <br/> <br/> *Service Fabric のメッシュ*プログラミング言語や好みのフレームワークを使用した開発することができます、Windows と Linux の両方のコンテナーをサポートします。

## <a name="using-container-based-orchestrators-in-azure"></a>Azure でコンテナー ベースのオーケストレーターの使用

いくつかのクラウド ベンダーは、Docker コンテナーのサポートと Docker クラスターおよびオーケストレーション サポート (Azure、Amazon EC2 Container Service、および Google Container Engine を含む) を提供します。 Azure に Docker を介して Azure Kubernetes Service (AKS)、Azure Service Fabric、および Azure Service Fabric のメッシュのクラスターとオーケストレーターのサポートを提供します。

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes Service の使用

Kubernetes クラスターでは、いくつかの Docker ホストのプールし、クラスターおよびスケール アウトで任意のコンテナー インスタンスに複数のコンテナーをデプロイできるように、1 つの仮想 Docker ホストとして公開すること。 クラスターは、スケーラビリティや正常性など、複雑な管理機能をすべて処理します。

ACS には、コンテナー化されたアプリケーションを実行するように Azure 内で事前に構成されている仮想マシンのクラスターの作成、構成、および管理を簡略化する方法が用意されています。 一般的なオープンソースのスケジューリングおよびオーケストレーション ツールの最適化された構成を使用することで、AKS では、コンテナー ベースのアプリケーションを Microsoft Azure でデプロイして管理するための専門知識を持つ増加し続けるコミュニティを利用するか、既存のスキルを使用することができます。

Azure Kubernetes Service によって、一般的な Docker クラスタリング オープンソース ツールとテクノロジの構成が Azure 専用に最適化されます。 コンテナーとアプリケーションの構成の両方に移植性を提供するオープン ソリューションが得られます。 サイズ、ホストの数、オーケストレーター ツールを選択すると、他のことはすべて AKS によって処理されます。

![Kubernetes クラスター構造:DNS、スケジューラ、プロキシなどを処理するマスター ノードが 1 つと、コンテナーをホストするワーカー ノードが複数あります。](media/image36.png)

**図 4-7**. Kubernetes クラスターの簡略化された構造とトポロジ

図 4-7 は、マスター ノード (VM) は、クラスターの調整のほとんどを制御するコンテナーをデプロイするには、他のアプリケーションの観点から 1 つのプールとして管理されているノードには、Kubernetes クラスターの構造を示します。 これにより、数千または数千のコンテナーも数十にスケールできます。

## <a name="development-environment-for-kubernetes"></a>Kubernetes 用の開発環境

開発環境でを[2018 年 7 月に発表した Docker](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)、Kubernetes によっても実行できます (Windows 10 または macOS) は、1 つの開発マシンでをインストールし、 [Docker デスクトップ](https://www.docker.com/community-edition)します。 4 ~ 8 の図に示すようには、後でさらに統合テストでは、クラウド (AKS) を展開することができます。

![Docker は、Docker Desktop を使用した、Kubernetes クラスターに対する開発マシンのサポートを 2018 年 7 月に発表しました。](media/kubernetes-development-environment.png)

**図 4-8** 開発マシンとクラウドでの Kubernetes の実行

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) を開始します。

AKS を使用するには、Azure ポータルまたは CLI を使用して AKS クラスターをデプロイします。 Azure Container Service クラスターの詳細については、[Azure Kubernetes Service (AKS) クラスターのデプロイ](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)に関するページを参照してください。

AKS の一部として既定でインストールされるソフトウェアはいずれも無料です。 既定のすべてのオプションはオープン ソース ソフトウェアと共に実装されます。 AKS は Azure 内の複数の仮想マシンで使用できます。 選択したコンピューティング インスタンスと、ストレージやネットワーキングなどの利用された他の基になるインフラストラクチャ リソースにのみ課金されます。 AKS 自体に従量課金はありません。

Kubernetes へのデプロイでの情報がに基づいてさらに実装の`kubectl`と元`.yaml`ファイルでの投稿をご覧ください[AKS (Azure Kubernetes Service) で eShopOnContainers を設定する](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service))します。

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Kubernetes クラスターに Helm チャートをデプロイします。

Kubernetes クラスターにアプリケーションをデプロイするときに、元を使用することができます`kubectl.exe`展開ファイルを使用して、CLI ツールは、ネイティブ形式に基づく (`.yaml`ファイル)、前のセクションで既に説明したようにします。 ただし、複雑なマイクロサービス ベースのアプリケーションをデプロイする場合など、より複雑な Kubernetes アプリケーションについては、[Helm](https://helm.sh/) の使用をお勧めします。

Helm チャートを使用して、バージョン、インストール、共有、アップグレード、またはロールバックも非常に複雑な Kubernetes アプリケーションを定義できます。

さらに述べると、Azure におけるその他の Kubernetes 環境 ([Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) など) も Helm Chart に基づいているので、Helm の使用が推奨されます。

Helm は、[クラウド ネイティブ コンピューティング Foundation (CNCF)](https://www.cncf.io/) Microsoft、Google、Bitnami、Helm 共同作成者のコミュニティと協力します。

実装の詳細について Helm チャートと Kubernetes での投稿をご覧ください。 [eShopOnContainers を AKS にデプロイする Helm チャートを使用して](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts)します。

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Azure 開発の域を使用した Kubernetes アプリケーションのライフ サイクル

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) には、チーム向けの迅速で反復的な Kubernetes 開発エクスペリエンスが用意されています。 開発マシンのセットアップ最小限にして、Azure Kubernetes Service (AKS) で直接、コンテナーの実行およびデバッグを反復的に実行することができます。 Windows、Mac、または Visual Studio、Visual Studio Code、またはコマンド ラインなどの使い慣れたツールを使用して Linux で開発できます。

前述のように、Azure 開発用のスペースは、コンテナー ベースのアプリケーションをデプロイするときに Helm チャートを使用します。

Azure の Dev スペースにより、開発チームが迅速に反復処理し、Visual Studio 2017 または Visual Studio Code を使用するだけで、グローバルの Kubernetes クラスターを Azure に直接コードをデバッグすることを許容するために Kubernetes の生産性を向上させます。 Azure 内の Kubernetes クラスターは共有されたマネージド Kubernetes クラスターであるため、チームは共同で作業を行うことができます。 コードを個別に開発してから、グローバル クラスターにデプロイし、依存関係のレプリケートやモックアップの作成なしで、他のコンポーネントでエンドツーエンド テストを実行することができます。

図 4 ~ 9 のように Azure 開発用のスペースで最も差別化機能は、グローバル展開、クラスター内の残りの部分に統合された実行可能な ' スペース' を作成する機能です。

![Azure Dev Spaces では、運用環境のマイクロ サービスと開発コンテナー インスタンスをさまざまな形で透過的に組み合わせることができます。](media/image38.png)

**図 4-9** Azure Dev Spaces での複数のスペースの使用

基本的には、Azure での共有開発空間を設定することができます。 各開発者ことができます、アプリケーションの部分だけに集中し、ことができますを既に他のすべてのサービスを含む開発空間で「事前コミット」のコードを開発を繰り返しクラウドのシナリオが依存するリソース。 依存関係は常に最新の状態になります。開発者は運用環境を反映した方法で作業します。

Azure 開発用のスペースは、分離では、チーム メンバーの邪魔せず動作することができるスペースの概念を提供します。 この機能は URL のプレフィックスをに基づいてください。コンテナーの要求の URL で開発空間のプレフィックスを使用する場合、Azure 開発用のスペースは、1 つが存在する場合をその領域にデプロイするコンテナーの特別なバージョンを実行します。 それ以外の場合は、グローバル/統合されたバージョンが実行されます。

確認できます、 [Azure 開発用のスペースに eShopOnContainers wiki ページ](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS)具体的な例で実際的なビューを取得します。

詳細については、上、記事をご覧ください。 [Azure 開発用のスペースを使用したチーム開発](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore)します。

## <a name="additional-resources"></a>その他の技術情報

- **Azure Kubernetes Service (AKS) の使用の開始** \
  [*https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal*](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

- **Azure Dev Spaces** \
  [*https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces*](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)

- **Kubernetes。** 公式サイト。 \
  [*https://kubernetes.io/*](https://kubernetes.io/)

## <a name="using-azure-service-fabric"></a>Azure Service Fabric の使用

サービスの提供に「ボックス」の製品は、通常、モノリシック スタイルの実現を移行する Microsoft の azure Service Fabric が発生しました。 Service Fabric の構築と Azure SQL Database、Azure Cosmos DB、Azure Service Bus、Cortana のバックエンドなどの規模での大規模なサービスの運用の経験から形成されました。 プラットフォームは時間をかけてより多くのサービスを採用するように進化しました。 重要なのは、Service Fabric は、Azure 内だけでなく、スタンドアロン Windows Server の展開でも実行する必要があることです。

Service Fabric の目的は、サービスの構築と実行、インフラストラクチャ リソースの効率的な使用に関連する困難な問題を解決し、チームがマイクロサービス アプローチを使用してビジネスの問題を解決できるようにすることです。

Service Fabric は、マイクロサービス アプローチを使用するアプリケーションの構築に役立つ 2 つの広範な領域を提供します。

- 展開、拡張、アップグレード、検出のためのシステム サービス、失敗したサービスの再起動、サービスの場所の検出、状態の管理、正常性の監視を提供するプラットフォーム。 これらのシステム サービスによって、前に説明したマイクロサービスの特性の多くが実質的に有効になります。

- アプリケーションをマイクロサービスとして構築するために役立つプログラミング API またはフレームワーク: [Reliable Actors と Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 もちろん、マイクロサービスの構築にはどのようなコードも選択できますが、これらの API では作業がより簡単になり、より深いレベルでプラットフォームと統合できます。 この方法で正常性情報と診断情報を取得し、信頼できる状態管理を利用することができます。

Service Fabric は、サービスの構築方法に依存しないので、任意のテクノロジを使用することができます。 ただし、マイクロサービスをビルドしやすくする組み込みのプログラミング API を提供します。

図 4-10 に示すようには、作成し、単純なプロセスまたは Docker コンテナーとして、Service Fabric でマイクロ サービスを実行できます。 同じ Service Fabric クラスターには、コンテナーベースのマイクロサービスとプロセッサーベースのマイクロサービスを混在させることもできます。

![Fabric クラスターの Azure サービスの比較。各ノードが各マイクロ サービスは 1 つのプロセスを実行するプロセスとしてのマイクロ サービスマイクロ サービスの各ノードがいくつかのコンテナーで Docker を実行するコンテナーとしてマイクロ サービスごとに 1 つのコンテナー。](./media/azure-service-fabric-cluster-types.png)

**図 4-10** Azure Service Fabric 内のプロセッサーまたはコンテナーとしてマイクロサービスを展開する

Linux と Windows のホストに基づく Service Fabric クラスターは、Docker Linux コンテナーと Windows コンテナーをそれぞれ実行することができます。

Azure Service Fabric でのコンテナーのサポートの最新情報については、「[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)」を参照してください。

Service Fabric は異なる論理アーキテクチャ (ビジネス マイクロ サービスまたは有界コンテキスト) 物理的な実装を定義する、プラットフォームの良い例です。 実装する場合など、[ステートフル Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)で[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)、次のセクションで導入された"[ステートレスとステートフル マイクロ サービス](#stateless-versus-stateful-microservices)、"複数の物理サービスを含むビジネス マイクロ サービスの概念があります。

Service Fabric ステートフル Reliable Service を実装するときに論理的/ビジネス マイクロ サービスの観点から考えると、図 4-10 に示す、通常必要があります 2 層のサービスを実装します。 1 つ目は、バックエンド ステートフル Reliable Service で、複数のパーティションを処理します (各パーティションはステートフル サービスです)。 2 つ目は、フロントエンド サービスまたはゲートウェイ サービスで、複数のパーティションまたはステートフル サービス インスタンス間のルーティングとデータの集計を担当します。 そのゲートウェイ サービスは、バックエンド サービスにアクセスする再試行のループが使用されたクライアント側の通信も処理します。 これは、カスタム サービスを実装している場合は、ゲートウェイ サービスと呼ばれます。または、そのままで使用できる Service Fabric の[リバース プロキシ サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)を使用することもできます。

![Service Fabric では、コンテナーでいくつかのステートフル reliable services をサポートするために処方箋があります。](./media/service-fabric-stateful-business-microservice.png)

**図 4-11** ビジネス マイクロ サービスで複数のステートフル サービス インスタンスとカスタム ゲートウェイ フロント エンド

いずれの場合も、Service Fabric ステートフル Reliable Services を使用する場合もがある論理的/ビジネス マイクロ サービス (境界コンテキスト) が複数の物理サービスで構成されます。 それぞれに、ゲートウェイ サービス、およびパーティションのサービスのアドレスは、図 4-11 に示すように、ASP.NET Web API サービスとして実装できます。

Service Fabric では、サービスをグループ化して、サービスのグループを [Service Fabric アプリケーション](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)として展開することができます。これは、オーケストレーターおよびクラスター用のパッケージ化および展開の単位です。 そのため、Service Fabric アプリケーションをこの自律的なビジネスおよび論理マイクロサービス境界または境界指定されたコンテキストにマッピングすることができ、さらにこれらのサービスを自律的に展開することもできます。

### <a name="service-fabric-and-containers"></a>Service Fabric とコンテナー

Service Fabric 内のコンテナーに関して、Service Fabric クラスター内のコンテナー イメージにサービスを展開することもできます。 図 4-12 に示す、ほとんどの場合はだけサービスごとに 1 つのコンテナーです。

![Service Fabric アプリケーションが外部データベースにアクセスする複数のコンテナーを実行し、セット全体は、ビジネス マイクロ サービスの論理的な境界になります](./media/azure-service-fabric-business-microservice.png)

**図 4-12**.  Service Fabric 内に複数のサービス (コンテナー) を持つビジネス マイクロサービス

ただし、いわゆる "サイドカー" コンテナー (論理サービスの一部としてまとめて展開する必要がある 2 つのコンテナー) は Service Fabric でも可能です。 重要な点は、ビジネス マイクロサービスが、いくつかのまとまりのある要素を囲む論理的な境界であることです。 これは、多くの場合、1 つのデータ モデルの 1 つのサービスかもしれませんが、場合によっては複数の物理的なサービスがある場合もあります。

図 4-13 に示すようには、プロセス、サービスと同じ Service Fabric アプリケーションでのコンテナー内のサービスを混在させることことに注意してください。

![サービスとコンテナーの両方を同じノードで実行されている service fabric アプリケーションです。](./media/business-microservice-mapped-to-service-fabric-application.png)

**図 4-13**.  コンテナーとステートフル サービスを含む Service Fabric アプリケーションにマップされているビジネス マイクロサービス

Azure Service Fabric でのコンテナーのサポートの詳細については、「[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)」を参照してください。

## <a name="stateless-versus-stateful-microservices"></a>ステートレス マイクロサービスとステートフル マイクロサービスの比較

前述のように、各マイクロサービス (論理的な境界指定されたコンテキスト) は、ドメイン モデル (データとロジック) を所有している必要があります。 ステートレス マイクロサービスの場合、データベースはサービス外部に用意することになります。このデータベースには、SQL Server などのリレーショナル オプション、または Azure Cosmos DB や MongoDB などの NoSQL データベースを使用できます。

Service Fabric でサービス自体もステートフルにして、データをマイクロサービス内に常駐させることもできます。 このデータは、同じサーバー上に存在できるだけでなく、マイクロサービスのプロセス内であれば、メモリ内に存在することも、ハード ドライブに保存することも、他のノードにレプリケートすることもできます。 図 4-30 では、別の方法を示します。

![ステートレス サービスでは、マイクロ サービスから (永続化、データベース) の状態は保持されます。 ステートフル サービスでは、マイクロ サービスの内部状態は保持されます。](./media/stateless-vs-stateful-microservices.png)

**図 4-14**.  ステートレス マイクロサービスとステートフル マイクロサービスの比較

ステートレス アプローチは、完全に有効で、従来の既知のパターンに似ているので、ステートフルなマイクロサービスよりも容易に実装できます。 ステートレス マイクロサービスは、プロセスおよびデータ ソース間の遅延を強制します。 キャッシュとキューを追加してパフォーマンスを改善しようとしている場合は、移動する部分も増えます。 結果として、階層の数が多すぎる複雑なアーキテクチャになる可能性があります。

一方、[ステートフルなマイクロサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)は、ドメイン ロジックとデータの間に遅延が生じないため、高度なシナリオに優れています。 負荷の高いデータ処理、ゲームのバックエンド、サービスとしてのデータベースなど、あまり遅延が許されないシナリオでは、ローカルな状態で高速にアクセスできるステートフル サービスのメリットを生かすことができます。

ステートレス サービスおよびステートフル サービスは相互に補完します。 たとえば、図 4-31 の右の図に示すように、ステートフル サービスは複数のパーティションに分割できます。 それらのパーティションにアクセスするには、パーティション キーに基づく各パーティションへのアドレス指定方法を知っているゲートウェイ サービスとして、ステートレス サービスが動作する必要があります。

ステートフル サービスには欠点があります。 スケール アウトする複雑性が高いレベルが課せられます。通常外部データベース システムによって実装される機能は、ステートフル マイクロサービスにまたがるレプリケーションや、データのパーティション分割などの機能として対処する必要があります。 ただし、[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) などのオーケストレーターとその[ステートフル Reliable Service](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) が最も役立つ領域の 1 つです。これにより、[Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) と [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) を使用するステートフル マイクロサービスの開発とライフサイクルが簡素化されます。

ステートフル サービスを許可し、Actor パターンをサポートし、ビジネス ロジックとデータ間のフォールト トレランスと遅延を改善する他のマイクロサービス フレームワークは、Microsoft [Orleans](https://github.com/dotnet/orleans)、Microsoft Research、および [Akka.NET](https://getakka.net/) です。 両方のフレームワークは、現在 Docker のサポートを向上させています。

Docker コンテナーはそれ自身ステートレスなことに注意してください。 ステートフル サービスを実装する場合は、前に説明した追加の規範的で高度なフレームワークの 1 つが必要です。

## <a name="using-azure-service-fabric-mesh"></a>Azure Service Fabric Mesh の使用

Azure Service Fabric のメッシュは、開発者がビルドして、すべてのインフラストラクチャを管理することがなくミッション クリティカルなアプリケーションをデプロイすることができる完全管理型サービスです。 Service Fabric Mesh を使用すると、必要に応じて拡大縮小できる分散型マイクロサービス アプリケーションをビルドして安全に実行することができます。

Service Fabric のメッシュでホストされているアプリケーションが実行され、スケールすることがなく 4-15 の図に示すように電源をオン、インフラストラクチャについて心配することです。

![Docker のデスクトップで実行される複数コンテナー アプリは、インフラストラクチャについて悩むことがなく、Azure Service Fabric のメッシュにデプロイできます。](media/image39.png)

**図 4-15**.  Service Fabric Mesh にマイクロサービス/コンテナー アプリケーションをデプロイする

Service Fabric Mesh の背後には、何千ものマシンで構成されるクラスターがあります。 クラスターのすべての操作は、開発者には表示されません。 ユーザーは、コンテナーをアップロードし、必要なリソース、可用性の要件、リソース制限を単純に指定するだけです。 Service Fabric Mesh は、アプリケーション開発で要求されたインフラストラクチャを自動的に割り当て、インフラストラクチャの障害を処理し、アプリケーションの高可用性を保証します。 ユーザーは、インフラストラクチャではなく、アプリケーションの正常性と応答性のみを考慮します。

詳細については、次を参照してください。、[ドキュメントの Service Fabric のメッシュ](https://docs.microsoft.com/azure/service-fabric-mesh/)します。

## <a name="choosing-orchestrators-in-azure"></a>Azure でオーケストレーターを選ぶ

次の表では、ワークロードおよび OS が焦点を当てていることに応じて、どのオーケストレーターを使用するかを示します。

![Azure Kubernetes サービスよりも Windows での Linux でさらに成熟したは、主コンテナーに基づくマイクロ サービスをデプロイするために使用します。 Azure Service Fabric (クラスターとメッシュの両方) は Linux でよりも Windows でより成熟しており、コンテナーに基づくマイクロサービス、プレーンなプロセスおよびステートフル サービスに基づくマイクロサービスで一般に使用されます。](media/image40.png)

**図 4-16**.  Azure でのオーケストレーターの選択のガイダンス

>[!div class="step-by-step"]
>[前へ](soa-applications.md)
>[次へ](deploy-azure-kubernetes-service.md)

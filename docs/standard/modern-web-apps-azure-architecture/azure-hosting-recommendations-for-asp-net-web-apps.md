---
title: ASP.NET Core Web アプリ用の Azure ホスティングの推奨事項
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | ASP.NET Web アプリ用の Azure ホスティングの推奨事項
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 7cfb9ada4f963aa392a41cfb9f1b2df22f542d41
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758680"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Core Web アプリ用の Azure ホスティングの推奨事項

> "基幹業務のリーダー everywhere クラウド (SaaS とも呼ばれます) からアプリケーションを取得する、it 部門のバイパスは、雑誌を購読するかのようにそれらの料金を支払います。 そして、サービスが不要になったら、無駄なくサブスクリプションを取り消すことができます。"  
> _\- Daryl Plummer、Gartner アナリスト_

これは、Microsoft Azure とサポート、アプリケーションのニーズとアーキテクチャにします。 ホスティングのニーズは静的な web サイトまたは多数のサービス構成の高度なアプリケーションとして簡単にできます。 ASP.NET Core のモノリシックな Web アプリケーションとサポートされるサービスには、推奨されるいくつかのよく知られている構成が含まれています。 この記事の推奨事項は、完全なアプリケーション、個別のプロセス、またはデータであっても、ホスティングされるリソースの種類に基づいてグループ化されています。

## <a name="web-applications"></a>Web アプリケーション

Web アプリケーションは次を使用してホスティングできます。

- App Service Web Apps

- コンテナー (いくつかのオプション)

- 仮想マシン (VM)

これらのうちは、App Service Web Apps は、単純なコンテナー ベースのアプリを含む、ほとんどのシナリオの推奨されるアプローチです。 マイクロサービス アーキテクチャでは、コンテナー ベースの方法を検討してください。 アプリケーションを実行しているマシンをさらに制御する必要がある場合は、Azure Virtual Machines を検討してください。

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps は、Web アプリケーションのホスティングに最適化されたフル マネージド プラットフォームを提供します。 これは、サービスとしてのプラットフォーム (PaaS) 製品です。Azure がアプリの実行とスケーリングに必要なインフラストラクチャに対処するため、ビジネス ロジックに集中することができます。 App Service Web Apps の主な機能:

- DevOps の最適化 (継続的インテグレーションと継続的配信、複数の環境、A/B テスト、スクリプトのサポート)

- グローバルなスケーリングと高可用性

- SaaS プラットフォームとオンプレミス データへの接続

- セキュリティとコンプライアンス

- Visual Studio の統合

Azure App Service は、ほとんどの Web アプリに最適な選択肢です。 デプロイと管理はプラットフォームに統合されており、サイトは高い負荷を処理できるように素早くスケーリングでき、組み込みの負荷分散とトラフィック マネージャーが高可用性を提供します。 オンライン移行ツールを使用して既存のサイトを簡単に Azure App Service に移動したり、Web アプリケーション ギャラリーからオープンソース アプリを使用したり、選択したフレームワークとツールを使用して新しいサイトを作成したりできます。 Web ジョブ機能により、バックグラウンド ジョブ処理を App Service Web アプリに簡単に追加できます。 既にある場合は、ASP.NET アプリケーションには、ローカル データベースを使用してオンプレミスがホストされている、アプリを App Service の Web アプリを Azure SQL Database (または、オンプレミス データベース サーバー、優先する場合に安全にアクセス) に移行する明確なパスがあります。

![推奨される移行戦略のオンプレミスを Azure App Service に .NET アプリ](./media/image1-6.png)

ほとんどの場合、ローカルでホストされる ASP.NET アプリから App Service Web アプリへの移行は簡単なプロセスです。 ほとんどまたはまったく変更は、アプリ自体の必要があり、Azure App Service Web Apps が提供する多くの機能を活用するために、すばやく開始できます。

だけでなく、クラウド向けに最適化されていないアプリは、Azure App Service Web Apps は、多くの単純なモノリシック (非分散) アプリケーション、多くの ASP.NET Core アプリなどの優れたソリューションが。 この方法で、アーキテクチャは基本的なと簡単に理解し、管理です。

![基本的な Azure のアーキテクチャ](./media/image1-5.png)

1 つのリソース グループ内のリソースの数が少ないが、通常、このようなアプリを管理するための十分です。 多くの個別のプロセスで構成されているこれらのアプリではなく、1 つの単位として展開される通常のアプリはこれに適した候補[基本的なアーキテクチャ アプローチ](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app)します。 この方法がまだ (ノードごとにリソース) の両方をスケール アウトをホスト型アプリを許可、アーキテクチャ的に単純な (よりホスト ノード) を需要の増加を満たすようにします。 自動スケールと、ノード間で需要と負荷の平均に基づいてアプリをホストするノードの数を自動的に調整する、アプリを構成できます。

### <a name="app-service-web-apps-for-containers"></a>App Service Web Apps for Containers

Web アプリを直接ホストするためのサポートに加えて[App Service Web Apps for Containers](https://azure.microsoft.com/services/app-service/containers/) Windows および Linux でコンテナー化されたアプリケーションを実行するために使用できます。 このサービスを使用して、簡単にデプロイでき、業務に合わせて拡張できるコンテナー化されたアプリケーションを実行できます。 アプリでは、すべての App Service Web Apps が上記の機能があります。 さらに、Web Apps for Containers のサポートは、Docker Hub、Azure Container Registry、および GitHub を使用した CI/CD を簡素化します。 Azure DevOps を使用すると、レジストリに変更を発行するビルドと配置のパイプラインを定義します。 これらの変更がステージング環境でテストし、ダウンタイムのアップグレードのためのデプロイ スロットを使用して運用環境に自動的にデプロイします。 以前のバージョンにロールバックするには、同じくらい簡単に実行できます。

Web Apps for Containers は、最も意味を行ういくつかのシナリオがあります。 Windows または Linux のコンテナーであるかどうか、コンテナー化でく既存のアプリがあれば、このツールセットを使用して簡単にこれらをホストすることができます。 コンテナーを簡単に発行し、し、Web Apps for Containers を任意のレジストリから最新バージョンのイメージをプルするを構成します。 これは、クラウドに最適化されたモデルにモデルをホストしているクラシック アプリからの移行に「リフトとシフト」アプローチです。

![Azure Web Apps for Containers へのオンプレミスでコンテナー化された .NET アプリケーションを移行します。](./media/image1-8.png)

このアプローチでは、開発チームは、コンテナー ベースの開発プロセスに移動する場合にも動作します。 コンテナーでアプリの開発の「内部ループ」は、コンテナーでアプリの構築が含まれます。 コンテナーの構成に関する同様のコードに加えられた変更は、ソース管理にプッシュし、自動化されたビルドが Docker Hub などのレジストリまたは Azure コンテナー レジストリに新しいコンテナー イメージの発行を担当します。 これらのイメージは、基礎として使用の追加の開発と運用環境にデプロイ次の図に示すように。

![エンド ツー エンドの Docker DevOps ライフ サイクル ワークフロー](./media/image1-7.png)

コンテナーが運用環境で使用される場合は特に、多くの利点を提供するコンテナーを使用した開発。 同じコンテナー構成は、実行されている、ビルドとテスト システム運用からシステムのローカル開発用コンピューターから各環境でアプリをホストに使用されます。 これにより、マシンの構成やソフトウェアのバージョンの違いに起因する障害が発生する可能性が大幅に削減されます。 開発者は、任意のツールになるオペレーティング システムを含む、使用すると、最も生産的なコンテナーは、任意の OS で実行できるためも使用できます。 多くのコンテナーに関連する分散アプリケーションのリソースを大量に消費 1 つの開発マシンで実行することがあります。 このシナリオでことは合理的です Kubernetes と Azure 開発用のスペース、次のセクションで説明を使用してにアップグレードします。

大規模なアプリケーションの特定の部分に分割されます独自小さく、独立した、*マイクロ サービス*、追加のデザイン パターンは、アプリの動作を向上させるために使用できます。 個々 のサービスを直接操作ではなく、 *API ゲートウェイ*へのアクセスを簡素化し、そのバック エンドからクライアントを切り離すことができます。 別のサービスで別のフロント エンド用バックエンドと、サービス コンシューマーと連携して進化をもできます。 一般的なサービスを個別のを介してアクセスできる*サイドカー*を使用して、一般的なクライアント接続のライブラリを含めることが、コンテナー、*アンバサダー*パターン。

![マイクロ サービスに注意していくつかの一般的な設計パターンとアーキテクチャをサンプルします。](./media/image1-10.png)

[マイクロ サービス ベースのシステムのビルド時に考慮する設計パターンについて説明します。](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) は、ホストされている Kubernetes 環境を管理するサービスで、コンテナー オーケストレーションの専門知識がなくても、コンテナー化したアプリケーションのデプロイと管理をすばやく簡単に行うことができます。 また、アプリケーションをオフラインにせずに、オンデマンドでリソースのプロビジョニング、アップグレード、スケーリングを実行できるため、継続的に行う操作と保守の負担も解消されます。

AKS では、Azure に対する責任の多くをオフロードすることによって、Kubernetes クラスターの管理における複雑な運用のオーバーヘッドを削減します。 ホストされている Kubernetes サービスとして、Azure では、正常性の監視や保守などの重要なタスクが処理されます。 また、マスターではなく、クラスター内のエージェント ノードのみの料金を支払います。 マネージド Kubernetes サービスとして、AKS では次が提供されます。

- 自動化された Kubernetes バージョンのアップグレードと修正。
- 簡単なクラスターのスケーリング。
- 自己復旧のホストされているコントロール プレーン (マスター)。
- コストの削減 - 実行中のエージェント プール ノードの料金のみを支払う。

Azure で AKS クラスター内のノードの管理を処理することで、クラスターのアップグレードなど、多くのタスクを手動で実行する必要がなくなりました。 Azure ではこれらの重要な保守タスクが処理されるため、AKS ではクラスターへの直接アクセスを提供しません (SSH の使用など)。

AKS を活用しているチームでは、Azure 開発用のスペースのも利用できます。 Azure の Dev スペースには、チームは、全体のマイクロ サービス アーキテクチャや AKS で実行されているアプリケーションを直接操作を許可することで、開発とマイクロ サービス アプリケーションの迅速な反復処理に注目するチームが役立ちます。 Azure の Dev スペースには、AKS クラスターまたは他の開発者の残りの部分に影響を与えずに単独で、マイクロ サービス アーキテクチャの特定の部分を個別に更新する方法も提供します。

![Azure 開発用のスペースのワークフローの例](./media/image1-9.gif)

Azure 開発のスペース:

- ローカル コンピューターのセットアップの時間とリソース要件を最小限に抑える
- チームがより迅速に反復処理を許可します。
- チームで必要な統合環境の数を減らす
- 削除は、開発/テストするときに、分散システムで特定のサービスをモックする必要があります。

[Azure 開発用のスペースを詳細します。](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

既存のアプリケーションにおいて App Service で実行するための大幅な変更が必要になった場合は、クラウドへの移行を簡略化するために Virtual Machines を選択できます。 ただし、Azure App Service と比較すると、VM の構成、セキュリティ保護、保守を正しく行うには、さらなる時間と IT の専門知識が必要になります。 Azure Virtual Machines を検討している場合は、現在の VM 環境のパッチ適用、更新、管理に必要な、継続的な保守作業を考慮してください。 Azure 仮想マシンはサービスとしてのインフラストラクチャ (IaaS) であり、App Service は PaaS です。 また、アプリを Windows Container として Web App for Containers にデプロイすることが、シナリオにとって有効なオプションになり得るかどうかも検討する必要があります。

## <a name="logical-processes"></a>論理プロセス

アプリケーションから分離できる個々の論理プロセスは、Azure Functions に関係なく "サーバーレス" な方法でデプロイできます。 Azure Functions では、アプリケーションまたはインフラストラクチャの実行を気にせずに、特定の問題で必要なコードのみを記述できます。 C\#、F\#、Node.js、Python、PHP などのさまざまなプログラミング言語を選択できるため、当面のタスクに対して最も生産性の高い言語を使用できます。 ほとんどのクラウドベースのソリューションと同様、使用した時間に対してのみ料金を支払います。Azure Functions は必要に応じて確実にスケール アップされます。

## <a name="data"></a>データ

Azure はさまざまなデータ記憶域のオプションを提供しているため、アプリケーションが対象となるデータに適したデータ プロバイダーを使用できます。

トランザクションに基づくリレーショナル データの場合、Azure SQL Database が最も適しています。 高パフォーマンスの読み取りが多くのデータの場合、Azure SQL Database に基づく Redis キャッシュが適しています。

構造化されていない JSON データは、SQL Database 列から Azure Storage の Blob またはテーブル、DocumentDB まで、さまざまな方法で格納できます。 このうち、DocumentDB がクエリ機能では最も優れており、クエリのサポートを必要とする JSON ベースのドキュメントが多数ある場合は、このオプションが推奨されます。

アプリケーションの動作を調整するために使用する一時的なコマンドベースの、またはイベントベースのデータでは、Azure Service Bus または Azure Storage キューを使用できます。 Azure Storage Bus はより柔軟性に優れているため、アプリケーション内、およびアプリケーション間で重要なメッセージをやり取りする場合に推奨されるサービスです。

## <a name="architecture-recommendations"></a>アーキテクチャに関する推奨事項

アプリケーションの要件で、アーキテクチャについて指示している必要があります。 利用できるさまざまな Azure サービスが多くあります。 適切なサービスを選ぶことが重要です。 Microsoft では、一般的なシナリオに最適化された典型的なアーキテクチャを特定できるように、参照アーキテクチャのギャラリーを提供しています。 アプリケーションの要件に最も近い、または少なくとも使い始めに適している参照アーキテクチャを見つけることができます。

図 11-2 は、参照アーキテクチャの例です。 この図は、マーケティングに最適化された Sitecore コンテンツ管理システム Web サイトに推奨されるアーキテクチャの手法を示しています。

![](./media/image11-2.png)

**図 11-1** Sitecore マーケティング Web サイトの参照アーキテクチャ。

**参照 – Azure のホスティングの推奨事項**

- Azure ソリューション アーキテクチャ\
  <https://azure.microsoft.com/solutions/architecture/>

- Azure の基本的な Web Application architecture \
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Microservices\ の設計パターン
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Azure の開発者ガイド\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Web Apps の概要\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Web App for Containers\
  <https://azure.microsoft.com/services/app-service/containers/>

- Azure Kubernetes Service (AKS) の概要\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[前へ](development-process-for-azure.md)

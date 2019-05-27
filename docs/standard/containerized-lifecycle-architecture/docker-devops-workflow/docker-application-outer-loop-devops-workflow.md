---
title: Docker アプリケーションの外側のループ DevOps ワークフローの手順
description: DevOps ワークフローの「外側のループ」手順を説明します
ms.date: 02/15/2019
ms.openlocfilehash: e7a82d2e5a5d503e5efbe9ac8242b163baab1286
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195616"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker アプリケーションの外側のループ DevOps ワークフローの手順

図 5-1 は、DevOps の外側のループのワークフローを構成する手順の説明、エンド ツー エンドの図を表示します。

![この図では、DevOps の「外側のループ」を示します。 にコードをリポジトリにプッシュすると、CI のパイプラインが開始し、アプリケーションがデプロイされる、CD パイプラインを開始します。 デプロイされたアプリケーションから収集されたメトリックが「内部ループ」が発生する、開発ワークロードに送られる開発チームがユーザーとビジネスのニーズに対応する実際のデータ。](./media/image1.png)

**図 5-1**します。 Microsoft ツールと Docker アプリケーション DevOps 外側のループのワークフロー

次に、それぞれの手順を詳しく見ていきましょう。

## <a name="step-1-inner-loop-development-workflow"></a>手順 1: 内部ループ開発ワークフロー

この手順は、第 4 章で詳しく説明を要約すると、ここでは、外側のループ開始位置となる、開発者が CI パイプラインのアクションの開始 (Git) のようなソース コントロール管理システムにコードをプッシュする時点。

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>手順 2: ソース コード管理の統合と Azure DevOps サービスと Git による管理

この手順では、チームのさまざまな開発者から、すべてのコードの統合されたバージョンを収集するバージョン管理システムに用意する必要があります。

アプリケーションを Docker イメージを送信する必要がありますいないを強調するために重要な場合でも、ソース コード管理 (SCC) とソース コード管理には、習慣にほとんどの開発者、DevOps ライフで Docker アプリケーションを作成するときのサイクルと思われる場合があります、直接、グローバル Docker レジストリに (Azure Container Registry や Docker Hub) など、開発者のマシンから。 反対に、グローバル ビルドまたはソース コード リポジトリ (Git) などに基づく CI パイプラインで、統合されることは、ソース コードのみにリリースされ、運用環境に展開する Docker イメージを作成する必要があります。

独自のマシン内でテストするときに、それらにより、開発者によって生成される、ローカルのイメージを使用だけください。 その理由は DevOps パイプラインを SCC コードからアクティブ化することが重要です。

Azure DevOps サービスと Team Foundation Server は、Git と Team Foundation バージョン管理をサポートします。 それらの間を選択し、エンド ツー エンドの Microsoft エクスペリエンスを使用できます。 ただし、管理することもできます (GitHub、Git リポジトリをオンプレミス、または Subversion) ような外部リポジトリでは、コードとそれに接続し、DevOps の CI パイプラインの開始点としてコードを取得できます。

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>手順 3: ビルド、CI、統合、および Azure DevOps を使用してテスト サービスと Docker

CI が最新のソフトウェアのテストおよび配信のための標準として登場しました。 Docker ソリューションでは、開発および運用チーム間での問題を明確に分離を維持します。 Docker イメージの不変性により、どのような開発、CI、テストおよび運用環境で実行が間に反復可能なデプロイ。 Docker エンジン開発者向けのノート パソコンに展開し、テスト インフラストラクチャは、環境間で、コンテナーを移植性。

この時点で、送信された正しいコードにバージョン管理システムがある必要があります、*サービスを構築*コードを選択し、グローバル ビルドとテストを実行します。

(CI、ビルド、テスト) この手順の内部ワークフローとは、ビルド サーバー (Azure DevOps サービス)、Docker エンジンと Docker レジストリをコード リポジトリ (Git など) から成る CI パイプラインを作成する方法。

できますサービスを使用する Azure DevOps の基盤として、アプリケーションを構築および、CI のパイプラインを設定するため、組み込みの「アイテム」を公開するため"アーティファクト リポジトリに、"については、次の手順で説明します。

Docker を使用して、展開は、「最終的な成果物」ときに展開するのには、アプリケーションやサービスを使用した Docker イメージ内に埋め込まれます。 これらのイメージのプッシュまたは発行を*Docker レジストリ*(Azure Container Registry で使用できるはまたはの公式の基本イメージの一般的な使用の Docker Hub レジストリなどのパブリック 1 などのプライベート リポジトリ)。

基本的な概念を次に示します。CI パイプラインは、Git などのソース コード管理リポジトリにコミットしてから開始されます。 図 5-2 に示すように、コミットは、Docker コンテナー内のビルド ジョブを実行し、そのジョブが正常に完了すると、Docker レジストリに Docker イメージをプッシュする DevOps サービスを Azure になります。

![外側のループの最初の部分を実行、コードから、手順 1 ~ 3 では、デバッグ、および検証し、ビルドとテストの CI 手順まで、コード リポジトリ](./media/image2.png)

**図 5-2** CI で必要な手順

Docker と Azure DevOps サービスの基本的な CI ワークフロー手順を次に示します。

1. 開発者は、ソース コード管理リポジトリ (Git または Azure DevOps Services、GitHub など) にコミットをプッシュします。

2. Azure DevOps Services または Git を使用している場合は、CI ビルドは、Azure DevOps サービスのチェック ボックスを選択するだけであることを意味します。 (GitHub) などの外部の SCC を使用している場合、`webhook`更新プログラムの DevOps サービスを Azure に通知または Git と GitHub にプッシュされます。

3. Azure DevOps サービスは、イメージだけでなく、アプリケーションとテストのコードを記述する Dockerfile を含む、SCC リポジトリをプルします。

4. Azure DevOps サービスは、Docker イメージをビルドおよびビルド番号のラベルします。

5. Azure DevOps サービスは、プロビジョニング済みの Docker ホスト内の Docker コンテナーをインスタンス化し、適切なテストを実行します。

6. 「試みられたビルド」がわかるように、イメージが最初にわかりやすい名前を付け、テストが成功した場合は、(のように"/1.0.0"またはその他の任意のラベル)、(Docker Hub、Azure Container Registry、DTR など)、Docker レジストリにプッシュし、

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Azure DevOps サービス用の Azure DevOps サービスと Docker 拡張機能を使用して、CI パイプラインの実装

Visual Studio の Azure DevOps サービスには、ビルド (&)、CI/CD パイプラインを Docker イメージを作成、認証済みの Docker レジストリに Docker イメージをプッシュ、または実行する Docker イメージ、によって提供されるその他の操作を実行に使用できるリリース テンプレートが含まれています。Docker CLI。 また、ビルド、プッシュ、およびマルチ コンテナー Docker アプリケーションを実行または図 5-3 に示すように Docker Compose CLI によって提供されるその他の操作を実行に使用できる Docker Compose のタスクを追加します。

![Azure DevOps での Docker の CI パイプラインのブラウザー ビュー](./media/image3.png)

**図 5-3** ビルド & リリース テンプレートと関連するタスクを含む Azure DevOps サービスで Docker CI パイプラインです。

これらのテンプレートとタスクを使用するにはビルド/テストおよびデプロイする CI/CD アーティファクトを作成する Azure Service Fabric、Azure Kubernetes サービス、および類似のサービスです。

これらの Visual Studio Team Services タスクとビルドを Linux Docker ホスト/VM Azure でプロビジョニングし、(Azure Container Registry、Docker Hub、プライベート Docker DTR、またはその他の任意の Docker レジストリ)、優先の Docker レジストリの Docker の CI パイプラインをアセンブルできます、非常に一貫した方法です。

***要件:***

- Azure DevOps サービス、またはオンプレミス インストールの場合、Team Foundation Server 2015 Update 3 またはそれ以降。

- Docker バイナリを含む Azure DevOps サービス エージェント。

  これらのエージェントのいずれかを作成する簡単な方法では、Docker を使用して、Azure DevOps サービス エージェントの Docker イメージに基づくコンテナーを実行します。

> [!情報] をクリックし、Azure DevOps サービスの Docker CI のアセンブリについての詳細はパイプラインし、チュートリアルの表示を読み取り、これらのサイトを参照してください。
>
> - Docker コンテナーとして、Visual Studio Team Services (今すぐ Azure DevOps サービス) エージェントを実行します \。
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Azure DevOps サービスを使用した .NET Core Linux Docker イメージを構築します \。
>   <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>
>
> - Docker サポートし、マシンを構築する Linux ベースの Visual Studio チーム サービスの構築: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>統合、テスト、およびマルチ コンテナー Docker アプリケーションの検証

通常、1 つのコンテナーではなく、複数のコンテナーの Docker アプリケーションのほとんどがで構成されます。 良い例は、マイクロ サービスごとに 1 つのコンテナーが、マイクロ サービス指向アプリケーションです。 ただし、マイクロ サービス アプローチのパターンに厳密に従うと、なくては Docker アプリケーションは、複数のコンテナーまたはサービスの構成は可能性の高い。

そのため、CI パイプラインでアプリケーション コンテナーをビルドした後も必要があります、展開、統合、およびすべての統合の Docker ホスト内で、またはさらには、コンテナーがテスト クラスターには、そのコンテナー全体のアプリケーションをテストするには分散されます。

1 つのホストを使用している場合は、docker などの Docker コマンドを使用することができます-ビルドしてデプロイをテストし、1 つの VM で Docker 環境を検証関連のコンテナーを作成します。 しかし、DC/OS、Kubernetes、Docker Swarm などをオーケストレーター クラスタを使用している場合、別のメカニズムや、選択したクラスター/スケジューラによって、orchestrator、コンテナーをデプロイする必要があります。

次に、Docker コンテナーに対して実行できるテストの種類をいくつか示します。

- Docker コンテナー用の単体テスト

- 相互に関連するアプリケーションやマイクロ サービスのグループのテスト

- 運用環境と「カナリア」のリリースでのテストします。

重要な点は、統合と機能テストを実行するときに、コンテナーの外部からそれらのテストを実行する必要があります。 テストは含まれているまたはコンテナーが必要がありますが、運用環境にデプロイするものとまったく同じように静的なイメージに基づいているため、デプロイするコンテナーで実行できません。

実用的なオプションでは、いくつかのクラスター (クラスター、クラスターのステージング、および運用環境のクラスターのテスト) を含むなどのシナリオより高度なテスト時に、さまざまなクラスターでテストできますのでをレジストリにイメージを発行することです。

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>グローバルな Docker レジストリをカスタム アプリケーションの Docker イメージをプッシュします。

Docker イメージをテストおよび検証した後にタグ付けし、Docker レジストリに公開します。 Docker レジストリは重要な部分を Docker アプリケーションのライフ サイクルの QA および実稼動環境にデプロイするのには、カスタム テスト (「試みられたイメージ」とも呼ばれます) を格納する中央の場所です。

方法、ソース コード管理リポジトリ (Git など) に格納されているアプリケーション コードは、「普遍の情報源」と同様に、Docker レジストリは、「ソース実のところの」、QA 環境または運用環境にデプロイするには、バイナリのアプリケーションやビットです。

通常、Azure コンテナー レジストリまたは Docker Trusted Registry のように、オンプレミスのレジストリまたは (制限付きのアクセス権を持つパブリック クラウドのレジストリで、カスタム イメージのプライベート リポジトリをプライベート リポジトリのいずれかがする可能性があります。Docker Hub)、この最後の場合、コードがオープン ソースの場合でも、ベンダーのセキュリティを信頼する必要があります。 どちらの方法を使用するメソッドはのようなに基づいて、`docker push`コマンド、図 5-4 に示すようにします。

![統合を構築して (CI) のテスト手順 3 では、プライベートまたはパブリック レジストリに結果の docker イメージを発行する可能性があります。](./media/image4.png)

**図 5-4** カスタム イメージを Docker レジストリに発行

Azure Container Registry、Amazon Web Services Container Registry、Google Container Registry、Quay レジストリなどのクラウド ベンダーからの Docker レジストリの複数のサービス提供しています。

Docker タスクを使用して、定義したサービスのイメージのセットをプッシュすることができます、`docker-compose.yml`ファイル (Azure Container Registry) などの認証済みの Docker レジストリに、複数のタグと図 5-5 に示すようにします。

![Azure DevOps からレジストリにイメージを発行する手順のブラウザー ビュー。](./media/image5.png)

**図 5-5** Azure DevOps サービスを使用して Docker レジストリにカスタム イメージを発行する

> [!情報] Azure Container Registry の詳細については、次を参照してください。<https://aka.ms/azurecontainerregistry>します。

## <a name="step-4-cd-deploy"></a>手順 4: CD、展開

Docker イメージの不変性により、反復可能な展開に何が開発、CI、テストし、運用環境で実行します。 所持している複数の環境に展開したり、Docker レジストリ (プライベートまたはパブリック) で公開されているアプリケーションの Docker イメージを作成したら、(運用、QA、ステージングなど) Azure DevOps サービスを使用して、CD パイプラインからパイプラインのタスクまたは Azure DevOps サービス リリース管理されます。

ただし、この時点でそれに依存展開する Docker アプリケーションの種類。 簡単なアプリケーション (構成と展開の観点から)、モノリシックのように、いくつかのコンテナーやサービスを構成するアプリケーションと展開をいくつかのサーバーまたは Vm を展開するとは異なるような複雑なアプリケーションを展開します。ハイパー スケール機能を備えたマイクロ サービス指向アプリケーションです。 これら 2 つのシナリオは、次のセクションについて説明します。

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>複数の Docker 環境への Docker アプリケーションの展開で構成されています

最初に、複雑なシナリオを見てみましょう。 単純で Docker ホスト (Vm またはサーバー) 環境を 1 つまたは複数の環境に展開する (品質保証、ステージング、および運用)。 このシナリオで内部的には、CD パイプラインできますを使用して docker-図 5-6 に示すようにコンテナーやサービス、その関連する一連の Docker アプリケーションを展開する (Azure DevOps サービス展開タスク) から作成します。

![CD のデプロイ手順 (4) q などのさまざまな環境に発行することができます (&)、ステージングと運用します。](./media/image6.png)

**図 5-6**します。 単純な Docker ホスト環境のレジストリにアプリケーション コンテナーのデプロイ

図 5-7 は、タスクの追加 ダイアログ ボックスの Docker Compose をクリックして、Azure DevOps サービスを使用して、QA/テスト環境にビルド、CI を接続する方法を示しています。 ただし、ステージング環境または運用環境を展開する場合は、通常使用する Release Management の機能が複数の環境を処理 (などの QA、ステージング、および運用)。 Azure DevOps サービスを使用して単一の Docker ホストにデプロイする場合は"Docker Compose"タスク (を呼び出すことは、`docker-compose up`内部的にはコマンド)。 Azure Kubernetes Service (AKS) をデプロイする場合は、以下のセクションで説明したように、Docker のデプロイ タスクを使用します。

![ブラウザー ビューの Docker Compose のタスクを追加します。](./media/image7.png)

**図 5-7** Azure DevOps サービス パイプラインで Docker Compose のタスクを追加します。

Azure DevOps サービスで、リリースを作成するときに、一連の入力の成果物がかかります。 これらの成果物が意図されていない変更可能なリリースの有効期間のすべての環境で。 コンテナーを導入するときに、入力の成果物を展開する、レジストリ内のイメージを識別します。 これらのイメージの識別方法に応じてする保証はありません、最も明白なケースが参照すると、リリースの全期間にわたって同じまま`myimage:latest`から、`docker-compose`ファイル。

Azure DevOps サービス テンプレートが表示ダイジェストとなる特定のレジストリのイメージが含まれているビルド成果物を生成する機能と同じイメージのバイナリを一意に識別することが保証されます。 これらは実際に、リリースへの入力として使用します。

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Azure DevOps Services Release Management を使用して Docker 環境にリリースを管理します。

Azure DevOps サービス テンプレートを新しいイメージをビルド、Docker レジストリに発行して、Linux または Windows のホストで実行してのコマンドを使用します`docker-compose`Azure DevOps などのアプリケーションが全体として複数のコンテナーをデプロイするには。図 5-8 に示すように複数の環境用リリース管理機能をサービスします。

![Azure DevOps, Docker の構成のブラウザー ビューでは、リリースを作成します。](./media/image8.png)

**図 5-8**. Azure DevOps サービス Release Management から Azure DevOps サービスの Docker Compose のタスクを構成します。

ただし、図 5-6 に示すように、図 5-8 の実装のシナリオは、単純なものにしてください (単一の Docker ホストと Vm への展開は、および 1 つのコンテナーまたはイメージごとのインスタンス) と、おそらく、開発またはテスト sce に対してのみ使用する必要がありますnarios します。 高可用性 (HA) と管理が容易なスケーラビリティが複数のノード、サーバー、Vm、および「インテリジェントなフェールオーバー」の間で負荷分散をするほとんどのエンタープライズ運用環境シナリオで、サーバーまたはノードが失敗した場合、そのサービスとコンテナー別のホスト サーバーまたは VM に移動されます。 その場合は、クラスターのコンテナー、オーケストレーター、およびスケジューラなどのより高度なテクノロジ必要があります。 したがって、これらのクラスターにデプロイする方法は、高度なシナリオを処理することで、[次へ] のセクションで説明します。

### <a name="deploying-docker-applications-to-docker-clusters"></a>Docker クラスターへの Docker アプリケーションの展開

分散アプリケーションの性質も分散されるコンピューティング リソースが必要です。 運用規模の機能には、高いスケーラビリティとプールされたリソースに基づく、高可用性を提供する機能をクラスタ リングにする必要があります。

コンテナーを CLI ツールまたは web UI からこれらのクラスターに手動でデプロイできますが、その種のスポット展開のテストに手動の作業を予約する必要があります。 またはスケール アウトや監視などの管理のため。

CD の観点と Azure DevOps サービスから具体的には、タスクを実行できます特別に作成された展開から、Azure DevOps サービス リリース管理環境をコンテナーに分散クラスターにコンテナー化されたアプリケーションを展開します。図 5-9 に示すようには、サービスです。

![CD のデプロイ手順 (4) はオーケストレーターを使ってクラスターにも発行できます。](./media/image9.png)

**図 5-9** 分散アプリケーションをコンテナー サービスを展開します。

最初を特定のクラスターやオーケストレーターに展開する場合は従来使用して特定の展開スクリプトと各オーケストレーター (Kubernetes およびさまざまな展開メカニズムがある Service Fabric) メカニズムではなく、単純です使いやすい`docker-compose`に基づいてツール、`docker-compose.yml`定義ファイル。 ただし、図 5-10 に示すように、Azure DevOps サービスの Docker デプロイ タスクに協力してくれたするようになりましたデプロイこともできますサポートされているオーケストレーターを使い慣れたを使用するだけで`docker-compose.yml`ツールが「変換」を実行するためのファイル (、から`docker-compose.yml`をオーケストレーターで必要な形式のファイル)。

![タスク カタログ内の Kubernetes タスクへの配置を示す、Azure DevOps のブラウザー ビュー。](./media/add-deploy-to-kubernetes-task.png)

**図 5-10** 環境に Kubernetes タスクへの展開の追加

図 5-11 では、Kubernetes 構成の使用可能なセクションでは、タスクへのデプロイを編集する方法について説明します。 これは、すぐに使用できるカスタム Docker イメージとして、クラスター内のコンテナー デプロイを取得するタスク。

![Azure DevOps, のブラウザー ビューは、タスクの定義を Kubernetes にデプロイします。](./media/edit-deploy-to-kubernetes-task.png)

**図 5-11** Docker デプロイ タスクの定義を展開する ACS DC/OS

> [!詳細情報] に関する Azure DevOps サービスと Docker の CD パイプラインを次を参照してください。 <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>手順 5: 実行し、管理

エンタープライズ運用レベルは、し、それ自体のと操作の種類のための主要なサブジェクトと、ユーザーがこの領域の大きなスコープとそのレベル (IT 運用) にとって、全体の次の章に充てるを実行していると、アプリケーションを管理するため、これを説明します。

## <a name="step-6-monitor-and-diagnose"></a>手順 6: 監視し、診断

このトピックでは、次についても説明、タスクの一部として章実稼働システムでその IT を実行しますただしが、アプリケーションが頻繁に改善するために、開発チームにこの手順で得られた知見をフィードする必要がありますを強調表示に重要です。 そのポイントの表示からもの一部では、DevOps タスクと操作によって実行が一般的ですが IT です。

監視と診断は、DevOps の領域内の 100% の場合にのみは、監視のプロセスとまたはベータ版のテスト環境に対して、開発チームによって実行された分析です。 これは、ロード テストを実行するか、ベータ版またはベータ テスト担当者が新しいバージョンを試みている、QA 環境を監視します。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)

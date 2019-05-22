---
title: Azure Service Fabric の使用
description: 単にコンテナーを調整する用途で使用する以外に、どの Azure Service Fabric アプリケーション モデルを使用できるかを説明します。
ms.date: 09/20/2018
ms.openlocfilehash: 3c629b473a429b64243b5756c96fef6585c939b7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644527"
---
# <a name="using-azure-service-fabric"></a>Azure Service Fabric の使用

Azure Service Fabric は、マイクロソフトの通常のモノリシックなスタイルのボックス製品の提供から、サービスの提供への変換から生まれました。 Azure SQL Database、Azure Cosmos DB、Azure Service Bus、Cortana のバックエンド、成形された Service Fabric などの大規模なサービスの構築と運用の経験からです。 プラットフォームは時間をかけてより多くのサービスを採用するように進化しました。 重要なのは、Service Fabric は、Azure 内だけでなく、スタンドアロン Windows Server の展開でも実行する必要があることです。

Service Fabric の目的は、サービスの構築と実行、インフラストラクチャ リソースの効率的な使用に関連する困難な問題を解決し、チームがマイクロサービス アプローチを使用してビジネスの問題を解決できるようにすることです。

Service Fabric は、マイクロサービス アプローチを使用するアプリケーションの構築に役立つ 2 つの広範な領域を提供します。

- 展開、拡張、アップグレード、検出のためのシステム サービス、失敗したサービスの再起動、サービスの場所の検出、状態の管理、正常性の監視を提供するプラットフォーム。 これらのシステム サービスによって、前に説明したマイクロサービスの特性の多くが実質的に有効になります。

- アプリケーションをマイクロサービスとして構築するために役立つ、[Reliable Actors と Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) というプログラミング API またはフレームワーク。 もちろん、マイクロサービスの構築にはどのようなコードも選択できますが、これらの API では作業がより簡単になり、より深いレベルでプラットフォームと統合できます。 この方法で正常性情報と診断情報を取得し、信頼できる状態管理を利用することができます。

Service Fabric は、サービスの構築方法に依存しないので、任意のテクノロジを使用することができます。 ただし、マイクロサービスをビルドしやすくする組み込みのプログラミング API を提供します。

図 4-27 に示すように、Service Fabric 内でマイクロサービスを単純なプロセスまたは Docker コンテナーとして作成して実行することができます。 同じ Service Fabric クラスターには、コンテナーベースのマイクロサービスとプロセッサーベースのマイクロサービスを混在させることもできます。

![Azure Service Fabric クラスター (各ノードがマイクロサービスごとに 1 つのプロセスを実行するプロセスとしてのマイクロサービス、各ノードがマイクロサービスごとに 1 つのコンテナーを使用して、複数のコンテナーで Docker を実行するコンテナーとしてのマイクロサービス) の比較。](./media/image30.png)

**図 4-27** Azure Service Fabric 内のプロセッサーまたはコンテナーとしてマイクロサービスを展開する

Linux と Windows のホストに基づく Service Fabric クラスターは、Docker Linux コンテナーと Windows コンテナーをそれぞれ実行することができます。

Azure Service Fabric でのコンテナーのサポートの最新情報については、「[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)」を参照してください。

Service Fabric は、「[論理アーキテクチャと物理アーキテクチャ](logical-versus-physical-architecture.md)」のセクションで紹介されている物理的な実装とは異なる論理アーキテクチャ (ビジネス マイクロサービスまたは境界指定されたコンテキスト) を定義できるプラットフォームの良い例です。 たとえば、後で「[ステートレス マイクロサービスとステートフル マイクロサービスの比較](#stateless-versus-stateful-microservices)」で紹介する[ステートフル リライアブル サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)を実装する場合、複数の物理的なサービスがあるビジネス マイクロサービスの概念を持っていることになります。

図 4-28 に示すように、論理的/ビジネス マイクロサービスの観点から考えた場合、Service Fabric ステートフル リライアブル サービスを実装するには、通常 2 層のサービスを実装する必要があります。 1 つ目は、バックエンド ステートフル Reliable Service で、複数のパーティションを処理します (各パーティションはステートフル サービスです)。 2 つ目は、フロントエンド サービスまたはゲートウェイ サービスで、複数のパーティションまたはステートフル サービス インスタンス間のルーティングとデータの集計を担当します。 そのゲートウェイ サービスは、バックエンド サービスにアクセスする再試行のループが使用されたクライアント側の通信も処理します。 これは、カスタム サービスを実装している場合は、ゲートウェイ サービスと呼ばれます。または、そのままで使用できる Service Fabric の[リバース プロキシ サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)を使用することもできます。

![](./media/image31.png)

**図 4-28** いくつかのステートフルなサービス インスタンスとカスタム ゲートウェイ フロントエンドを含むビジネス マイクロサービス

いずれの場合でも、Service Fabric ステートフル リライアブル サービスを使用する場合、通常は複数の物理サービスで構成される論理的/ビジネス マイクロサービス (境界指定されたコンテキスト) も使用できます。 図 4-28 に示すように、それぞれにゲートウェイ サービスおよびパーティションのサービスは ASP.NET Web API サービスとして実装できます。

Service Fabric では、サービスをグループ化して、サービスのグループを [Service Fabric アプリケーション](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)として展開することができます。これは、オーケストレーターおよびクラスター用のパッケージ化および展開の単位です。 そのため、Service Fabric アプリケーションをこの自律的なビジネスおよび論理マイクロサービス境界または境界指定されたコンテキストにマッピングすることができ、さらにこれらのサービスを自律的に展開することもできます。

## <a name="service-fabric-and-containers"></a>Service Fabric とコンテナー

Service Fabric 内のコンテナーに関して、Service Fabric クラスター内のコンテナー イメージにサービスを展開することもできます。 図 4-29 に示すように、ほとんどの場合、コンテナーはサービスごとに 1 つのみがあります。

![Service Fabric アプリケーションは、外部データベースにアクセスする複数のコンテナーを実行でき、セット全体は、ビジネス マイクロサービスの論理的な境界になります。](./media/image32.png)

**図 4-29** Service Fabric 内に複数のサービス (コンテナー) を持つビジネス マイクロサービス

ただし、いわゆる "サイドカー" コンテナー (論理サービスの一部としてまとめて展開する必要がある 2 つのコンテナー) は Service Fabric でも可能です。 重要な点は、ビジネス マイクロサービスが、いくつかのまとまりのある要素を囲む論理的な境界であることです。 これは、多くの場合、1 つのデータ モデルの 1 つのサービスかもしれませんが、場合によっては複数の物理的なサービスがある場合もあります。

図 4-30 に示すように、同じ Service Fabric アプリケーションにプロセスのサービスとコンテナーのサービスを混在させることができることに注意してください。

![同じノードでサービスとコンテナーの両方を実行する Service Fabric アプリケーション。](./media/image33.png)

**図 4-30** コンテナーとステートフル サービスを含む Service Fabric アプリケーションにマップされているビジネス マイクロサービス

Azure Service Fabric でのコンテナーのサポートの詳細については、「[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)」を参照してください。

## <a name="stateless-versus-stateful-microservices"></a>ステートレス マイクロサービスとステートフル マイクロサービスの比較

前述のように、各マイクロサービス (論理的な境界指定されたコンテキスト) は、ドメイン モデル (データとロジック) を所有している必要があります。 ステートレス マイクロサービスの場合、データベースはサービス外部に用意することになります。このデータベースには、SQL Server などのリレーショナル オプション、または Azure Cosmos DB や MongoDB などの NoSQL データベースを使用できます。

Service Fabric でサービス自体もステートフルにして、データをマイクロサービス内に常駐させることもできます。 このデータは、同じサーバー上に存在できるだけでなく、マイクロサービスのプロセス内であれば、メモリ内に存在することも、ハード ドライブに保存することも、他のノードにレプリケートすることもできます。 図 4-30 では、別の方法を示します。

![ステートレス サービスでは、状態 (永続化、データベース) はマイクロサービス外で保持されます。 ステートフル サービスでは、状態はマイクロ サービス内で保持されます。](./media/image34.png)

**図 4-31**。 ステートレス マイクロサービスとステートフル マイクロサービスの比較

ステートレス アプローチは、完全に有効で、従来の既知のパターンに似ているので、ステートフルなマイクロサービスよりも容易に実装できます。 ステートレス マイクロサービスは、プロセスおよびデータ ソース間の遅延を強制します。 キャッシュとキューを追加してパフォーマンスを改善しようとしている場合は、移動する部分も増えます。 結果として、階層の数が多すぎる複雑なアーキテクチャになる可能性があります。

一方、[ステートフルなマイクロサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)は、ドメイン ロジックとデータの間に遅延が生じないため、高度なシナリオに優れています。 負荷の高いデータ処理、ゲームのバックエンド、サービスとしてのデータベースなど、あまり遅延が許されないシナリオでは、ローカルな状態で高速にアクセスできるステートフル サービスのメリットを生かすことができます。

ステートレス サービスおよびステートフル サービスは相互に補完します。 たとえば、図 4-31 でわかるように、右側の図では、ステートフル サービスを複数のパーティションに分割することができます。 それらのパーティションにアクセスするには、パーティション キーに基づく各パーティションへのアドレス指定方法を知っているゲートウェイ サービスとして、ステートレス サービスが動作する必要があります。

ステートフル サービスには欠点があります。 スケール アウト可能なある程度の複雑さを強制します。通常外部データベース システムによって実装される機能は、ステートフル マイクロサービスにまたがるレプリケーションや、データのパーティション分割などの機能として対処する必要があります。 ただし、[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) などのオーケストレーターとその[ステートフル Reliable Service](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) が最も役立つ領域の 1 つです。これにより、[Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) と [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) を使用するステートフル マイクロサービスの開発とライフサイクルが簡素化されます。

ステートフル サービスを許可し、Actor パターンをサポートし、ビジネス ロジックとデータ間のフォールト トレランスと遅延を改善する他のマイクロサービス フレームワークは、Microsoft [Orleans](https://github.com/dotnet/orleans)、Microsoft Research、および [Akka.NET](https://getakka.net/) です。 両方のフレームワークは、現在 Docker のサポートを向上させています。

Docker コンテナーはそれ自身ステートレスなことに注意してください。 ステートフル サービスを実装する場合は、前に説明した追加の規範的で高度なフレームワークの 1 つが必要です。

## <a name="using-azure-service-fabric-mesh"></a>Azure Service Fabric Mesh の使用 

Azure Service Fabric Mesh は、開発者がインフラストラクチャをまったく管理せずに、ミッション クリティカルなアプリケーションをビルドすることができる完全に管理されたサービスです。 Service Fabric Mesh を使用すると、必要に応じて拡大縮小できる分散型マイクロサービス アプリケーションをビルドして安全に実行することができます。 

図 4-32 のとおり、Service Fabric Mesh にホストされているアプリケーションは、その基礎になっているインフラストラクチャを考慮する必要なく、実行および拡大縮小できます。

![Docker のデスクトップで実行する複数のコンテナー アプリを、インフラストラクチャを心配することなく Azure Service Fabric Mesh にデプロイできます。](media/image39.png)

**図 4-32**。 Service Fabric Mesh にマイクロサービス/コンテナー アプリケーションをデプロイする

Service Fabric Mesh の背後には、何千ものマシンで構成されるクラスターがあります。 クラスターのすべての操作は、開発者には表示されません。 ユーザーは、コンテナーをアップロードし、必要なリソース、可用性の要件、リソース制限を単純に指定するだけです。 Service Fabric Mesh は、アプリケーション開発で要求されたインフラストラクチャを自動的に割り当て、インフラストラクチャの障害を処理し、アプリケーションの高可用性を保証します。 ユーザーは、インフラストラクチャではなく、アプリケーションの正常性と応答性のみを考慮します。

詳細については、[Service Fabric Mesh のドキュメント](https://docs.microsoft.com/azure/service-fabric-mesh/)を参照してください。

## <a name="choosing-orchestrators-in-azure"></a>Azure でオーケストレーターを選ぶ

次の表では、ワークロードおよび OS が焦点を当てていることに応じて、どのオーケストレーターを使用するかを示します。

![Azure Kubernetes Services は、Windows でよりも Linux でより成熟しており、コンテナーに基づいてマイクロサービスをデプロイするのに多く使用されています。 Azure Service Fabric (クラスターとメッシュの両方) は Linux でよりも Windows でより成熟しており、コンテナーに基づくマイクロサービス、プレーンなプロセスおよびステートフル サービスに基づくマイクロサービスで一般に使用されます。](media/image40.png)

**図 4-33**。 Azure でのオーケストレーターの選択のガイダンス

>[!div class="step-by-step"]
>[前へ](scalable-available-multi-container-microservice-applications.md)
>[次へ](../docker-application-development-process/index.md)

---
title: コンテナー化アプリ用の Microsoft プラットフォームとツールの概要
description: Docker アプリケーションのライフ サイクルをサポートするために Microsoft の内容を把握するを取得します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 811ebd46c97b53176bf8bb9e47a366575e273efb
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680194"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Microsoft プラットフォームとコンテナー化アプリ用ツールの概要

*ビジョン:作成する、柔軟性の高いエンタープライズ グレードのコンテナー化されたアプリケーションのライフ サイクルにまたがる、開発、IT の運用および運用管理します。*

図 3-1 は、複数のチーム (アプリの開発、DevOps インフラストラクチャ プロセス、および IT 管理および運用) によって提供される作業の種類で分類された Docker アプリのライフ サイクルの主要な柱を示しています。 通常、企業では、それぞれの領域を代表する "ペルソナ" のプロファイルは異なります。 そのため、スキルも異なります。

![Microsoft のツールです。 開発/デザイン ワークロード。Windows、VS および VS Code、.NET Core, Azure Kubernetes サービスの docker エンジンです。 出荷/ビルド/テスト ワークロード。Azure DevOps, は Team Foundation Server、Docker CLI, Azure Kubernetes サービスです。 ワークロードの実行/モニター/管理。Application Insights、Azure Portal の Azure Kubernetes サービス、Service Fabric、他のオーケストレーターです。](./media/image1.png)

**図 3-1.** Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフ サイクルの主要な柱

コンテナー化された Docker ライフ サイクル ワークフローできます最初に規範的な既定で製品の選択"、"高速で開始する開発者が簡単に基づくが、内部的にが必要になる、オープンなフレームワークがなりますように基本的なことを各組織または企業から別のコンテキストに合わせて調整できる柔軟なワークフローです。 ワークフロー インフラストラクチャ (コンポーネントと製品) は、各企業が将来使用する環境をカバーできるだけの十分な柔軟性が必要であり、開発製品や DevOps 製品を他と交換することさえ可能になっている必要があります。 この柔軟性とオープンさ、プラットフォームとインフラストラクチャの広い選択肢は、以下の章で説明するように、コンテナー化された Docker アプリケーションで Microsoft がまさに優先していることです。

表 3-1 は、コンテナー化された Docker アプリケーション用 Microsoft DevOps の目的が、オープンな DevOps ワークフローを提供し、各フェーズ (Microsoft またはサード パーティ) で使用する製品を選択できるようにすることであり、同時に、既に接続された "既定の製品" を提供する簡素化されたワークフローを提供することを示しています。これにより、Docker アプリ用のエンタープライズレベルの DevOps の使用をすばやく開始することができます。

**表 3-1。** DevOps ワークフローの任意のテクノロジを開く

| ホスト | マイクロソフト テクノロジ | サード パーティ — Azure 接続可能 |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker アプリのプラットフォーム   | • Microsoft Visual Studio および Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Container Service<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • 任意のコード エディター (Sublime など)<br /> • 任意の言語 (Node.js、Java、Go など)<br /> • 任意のオーケストレーターとスケジューラ<br /> • 任意の Docker レジストリ<br /> |
| Docker アプリ用の DevOps     | • Azure DevOps サービス<br /> • Microsoft Team Foundation Server<br /> • Azure Container Service<br /> • Azure Service Fabric<br /> | • GitHub、Git、Subversion など<br /> • Jenkins、Chef、Puppet、Velocity、CircleCI、TravisCI など<br /> • On-premises Docker Datacenter、Docker Swarm、Mesos DC/OS、Kubernetes など<br /> |
| 管理と監視  | • Operations Management Suite<br /> • Applications Insights<br /> | • Marathon、Chronos など<br />

Microsoft プラットフォームとコンテナー化された Docker アプリ用ツールは表 3-1 に示すように、定義されている次のコンポーネントから成ります。

- **Docker アプリ開発用プラットフォーム** サービス、または "アプリ" を構成するサービスのコレクションの開発。 開発プラットフォームは、コードを共有コード リポジトリにプッシュする前に開発者が実行する必要があるすべての作業を提供します。 開発サービスは、コンテナーとして展開では、同じアプリまたは Docker を使用しないサービスの開発に似ています。 優先する言語 (.NET、Node.js、Go など) と好みのエディターまたは Visual Studio または Visual Studio Code などの IDE を使用する続行するとします。 ただし、展開先として Docker を考慮するのではなく、Docker 環境でサービスを開発します。 コンテナーでローカルでコードを構築、実行、テスト、およびデバッグ、開発時に配置先の環境を提供します。 ローカルで配置先の環境を提供することで、Docker コンテナーは、DevOps のライフ サイクルを改善するために大きく役立ちます。 Visual Studio および Visual Studio Code には、開発プロセス内で Docker コンテナーを統合するための拡張機能があります。

- **Docker アプリ用の DevOps** Docker アプリケーションを作成する開発者が使用できる[Azure DevOps サービス](https://azure.microsoft.com/services/devops/)または包括的な自動アプリケーションのライフ サイクルを構築するための Jenkins のようなその他のサード パーティ製品管理 (ALM)。

  コンテナーに重点を置いた Azure DevOps サービスを使用する開発者を作成できます (Azure DevOps サービス-Git、GitHub、リモート Git リポジトリ、または Subversion) 任意の場所から継続的インテグレーション (CI) 制御、高速で反復的なプロセスでソース コードをカバーする DevOps、内部単体テスト、container 間/サービスの統合テスト、継続的デリバリー (CD)、およびリリース管理 (RM)。 開発者は、開発からステージング環境と実稼働環境の Azure コンテナー サービスへの Docker アプリケーションのリリースを自動化することもできます。

- **管理と監視**IT 管理および実稼働アプリケーションと統合されたエクスペリエンスの両方のパースペクティブを統合するいくつかの方法でサービスを監視できます。

  - **Azure portal** Azure Kubernetes Service (AKS)、Service Fabric、およびその他のオーケストレーターはヘルプを設定し、Docker の環境を維持することでオープン ソース オーケストレーターを使用している場合。 Azure Service Fabric を使用している場合、Service Fabric Explorer ツールを利用すると、クラスターを視覚化して構成できます。

  - **Docker ツール** 使い慣れたツールを使用して、コンテナー アプリケーションを管理することができます。 コンテナーのワークロードをクラウドに移動するために、既存の Docker 管理方法を変更する必要はありません。 既に精通している任意のアプリケーション管理ツールを使用し、選択したオーケストレーター用の標準 API エンドポイント経由で接続します。 Docker Datacenter や CLI Docker ツールなどの他のサードパーティ製ツールを使用して、Docker アプリケーションを管理することもできます。 

    Linux コマンドを使い慣れている、場合でも、クライアントを使用して Microsoft Windows と PowerShell Linux サブシステムのコマンドラインや (Docker、Kubernetes...)、製品のこの Linux サブシステム機能で実行されているコンテナー アプリケーションを管理できます。 この書籍の後半で、お気に入りの Microsoft Windows OS を使用して Linux サブシステムでこれらのツールを使用する方法について学びます。

  - **オープン ソース ツール** オーケストレーション エンジン用の標準 API エンドポイントを公開するため、AKS、最も人気のあるツールは、AKS と互換性があるし、ほとんどの場合は、ボックスから機能、ビジュアライザー、監視などコマンドライン ツール、および利用可能になった後のツール。

  - **Application Insights**運用環境のあらゆる側面を監視するには、Azure のグローバルコンテンツサプライします。 運用環境の Docker アプリケーションを監視するには、単に SDK サービスをセットアップ、アプリケーションからシステムによって生成されたログ データを取得できます。

このように、Microsoft は、エンド ツー エンドのコンテナー化 Docker アプリケーションのライフ サイクルの完全な基盤を提供します。 ただし、*の製品とテクノロジを必要に応じて選択し、既存の統合を許可する一連のツールやプロセス*します。 広範囲なアプローチの柔軟性、および機能の綿密さによる強みにより、Microsoft は、コンテナー化 Docker アプリケーション開発において強力な位置を築いています。

>[!div class="step-by-step"]
>[前へ](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[次へ](../design-develop-containerized-apps/index.md)

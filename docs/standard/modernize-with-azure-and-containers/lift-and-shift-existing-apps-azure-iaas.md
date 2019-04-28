---
title: リフト アンド既存の .NET アプリを Azure IaaS (クラウド インフラストラクチャの準備完了) にシフト
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 0f9ff19c8e346560960a09d3b7c52976c478f2f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651201"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>リフト アンド既存の .NET アプリを Azure IaaS (クラウド インフラストラクチャの準備完了) にシフト

> ビジョン:最初の手順として、オンプレミスへの投資とハードウェアやネットワークのメンテナンスの総コストを削減するだけのリホスト、既存のアプリケーションをクラウドで。

入る前に*方法*a service (IaaS) プラットフォームとして Azure インフラストラクチャに既存のアプリケーションを移行することが理由を分析する重要*なぜ*IaaS に直接移行します。azure。 この最新化成熟度レベルにあるシナリオは、基本的に、現在のオンプレミス インフラストラクチャの使用を継続するのではなく、クラウドで Vm の使用を開始します。

分析に別のポイントは*なぜ*を Azure で管理されたサービスをより高度なを追加するだけではなく純粋な IaaS クラウドに移行する可能性があります。 特定のケースで可能性があります、最初に IaaS を必要とします。

図 2-1 は、クラウド インフラストラクチャの準備完了アプリケーションを近代化の成熟度レベルで位置します。

![クラウド インフラストラクチャの準備完了アプリケーションの配置](./media/image2-1.png)

> **図 2-1** クラウド インフラストラクチャの準備完了アプリケーションの配置

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Azure IaaS への既存の .NET web アプリケーションを移行する理由

コストの削減を実現する主な理由は、初期の IaaS レベルでも、クラウドに移行することです。 その他の管理対象のインフラストラクチャ サービスを使用すると、組織はハードウェアのメンテナンス、サーバーまたは VM のプロビジョニングし展開、およびインフラストラクチャの管理への投資を下げることができます。

アプリをクラウドに移行する意思決定を行うと、選択する理由が IaaS PaaS が単純にするようより高度なオプションではなく、IaaS 環境の主な理由についての理解になります。 オンプレミス環境には、現在次のような環境への移動、クラウドに移行する最も簡単なパスを下の学習曲線を提供します。

ただし、クラウドに移行する最も簡単なパスを取得とは限りませんと、アプリケーションをクラウドで実行されている必要がなくなりますほとんどメリットが得れていること。 任意の組織には、既に導入された、クラウド最適化とクラウド ネイティブの成熟度レベルのクラウド移行の最も重要な利点を享受できます。

なったアプリケーションが簡単に最新化して、IaaS 上であっても、クラウドで既に実行されている場合、将来再設計が明らかです。 アプリケーション データの移行は既に実現されています。 組織をクラウドでの作業に必要なスキルを獲得し、"クラウド culture"で動作させること、shift キーを押しがさらに、

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Paas の代わりに IaaS に移行するときに

次のセクションでは、PaaS プラットフォームおよびサービスに基づくほとんどの場合、クラウドに最適化されたアプリケーションについて説明します。 これらのアプリを提供するからクラウドへの移行ほとんどメリットです。 

既存のアプリケーションをクラウドに移行するだけが目的の場合は、まず、Azure App Service で実行する大幅な変更を必要とせず、既存のアプリケーションを特定します。 これらのアプリが行う最有力候補にする必要がありますクラウドに最適化されました。 

アプリをまだことはできませんを移動 Windows コンテナーと PaaS など、App Service または Azure Service Fabric、などのオーケストレーターされた単純なプレーンな Vm (IaaS) に移行します。 

ただし、正しく構成、セキュリティ保護、および Vm の保守が必要であるさらに多くの時間と IT の専門知識と比較して、Azure で PaaS サービスの使用に注意してください。 Azure Virtual Machines を検討している場合の修正、更新、および VM 環境を管理するための継続的なメンテナンス労力を考慮することを確認します。 Azure Virtual Machines は、IaaS です。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Azure Migrate を使用して分析し、既存のアプリケーションを Azure に移行

クラウドへの移行は必ずしも難しくはありません。 多くの組織が、環境とアプリケーション、ワークロード、およびデータ間の緊密な依存関係に詳細な可視性を取得する - 開始するのに苦労します。 その可視性、なしは、道筋を計画する困難なことができます。 移行を成功させるために必要な内容の詳細については、なし、組織内で、適切な会話ことはできません。 考えられる利点、コストの話が不明またはワークロードのだけリフト アンド シフトだったかどうかまたは正常に移行する重要な作業のやり直しが必要になります。 無理は多くの組織で問題ありません。

[Azure Migrate](https://aka.ms/azuremigrate)ガイダンス、洞察、および Azure への移行を支援するために必要なメカニズムを提供する新しいサービスです。 Azure Migrate を提供します。

- 検出と、オンプレミスの仮想マシンの評価

- 多階層アプリケーションの信頼性の高い検出用の組み込みの依存関係マッピング

- Azure 仮想マシンへのインテリジェントな適切なサイズ変更

- 互換性の潜在的な問題を修復するためのガイドラインでレポートの作成

- データベースの検出と移行のための Azure Database Management Service との統合

Azure Migrate では、ワークロードの移行、ビジネスに影響を最小限および Azure で想定どおりに実行できる状況を回避できます。 適切なツールとガイダンスでは、最大の重要なパフォーマンスを確保しながら投資回収を実現でき、信頼性の要件を満たしています。

図 2-2 では、Azure Migrate によって実行されるすべてのサーバーとアプリケーションの接続の組み込みの依存関係マッピングを示します。

![クラウド インフラストラクチャの準備完了アプリケーションの配置](./media/image2-2.png)

> **図 2-2 です。** クラウド インフラストラクチャの準備完了アプリケーションの配置

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Azure Site Recovery を使用して Azure Vm に、既存の Vm を移行するには

エンド ツー エンドの一部として[Azure Migrate](https://aka.ms/azuremigrate)、 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)は、web アプリを Azure で Vm を簡単に移行するために使用できるツールです。 オンプレミスの Vm と物理サーバーを Azure にレプリケートする、またはセカンダリ オンプレミスの場所にこれらをレプリケートするには、Site Recovery を使用することができます。 オンプレミス上で、サポートされている Azure VM で実行されているワークロードをレプリケートすることもできます*HYPER-V* VM の*VMware* VM、または Windows または Linux の物理サーバー。 Azure へのレプリケーションでは、コストとセカンダリ データ センターの管理の複雑さがなくなります。

Site Recovery が部分的であるハイブリッド環境向けでも、オンプレミスと Azure の一部にします。 Site Recovery により、Vm で実行されているアプリを保持することでビジネス継続性を確保し、オンプレミスで使用可能な物理サーバー、サイトがダウンした場合。 したまま利用可能なセカンダリの場所にプライマリ サイトが利用できない場合は、Vm と物理サーバーで実行されているワークロードをレプリケートします。 ワークロードを再実行して、プライマリ サイトが稼働状態を回復します。

図 2-3 は、Azure Site Recovery を使用して、複数の仮想マシンの移行の実行を示しています。

![クラウド インフラストラクチャの準備完了アプリケーションの配置](./media/image2-3.png)

> **図 2-3。** クラウド インフラストラクチャの準備完了アプリケーションの配置

### <a name="additional-resources"></a>その他の技術情報

- **Azure Migrate のデータシート**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate します。**

    <https://aka.ms/azuremigrate>

- **Azure 移行センター**

    <https://azure.microsoft.com/migration/>

- **Site Recovery を使用した Azure への移行します。**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure Site Recovery サービスの概要**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Azure Vm への aws Vm の移行**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](migrate-your-relational-databases-to-azure.md)

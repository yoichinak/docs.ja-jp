---
title: 既存の .NET アプリを Azure IaaS にリフトアンドシフトする (クラウドインフラストラクチャの準備完了)
description: Azure クラウドおよび Windows コンテナーを使用して、既存の .NET アプリケーションを最新化します。
ms.date: 04/28/2018
ms.openlocfilehash: e25ddbf9b6e62c264f3f4d4580d7df3553d262ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660750"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>既存の .NET アプリを Azure IaaS にリフトアンドシフトする (クラウドインフラストラクチャの準備完了)

> 展望:最初の手順として、オンプレミスの投資とハードウェアとネットワークのメンテナンスの総コストを削減するために、単にクラウド内の既存のアプリケーションを再ホストします。

既存のアプリケーションを azure infrastructure as a Service (iaas) プラットフォームに移行する前に、Azure の iaas に直接移行する理由を分析することが重要です。 この近代化成熟度レベルのシナリオでは、基本的に、現在のオンプレミスインフラストラクチャを引き続き使用するのではなく、クラウドで Vm の使用を開始します。

さらに、Azure に高度な管理サービスを追加するのではなく、純粋な IaaS クラウドに移行することが必要になる場合もあります。 最初の場所で IaaS を必要とするケースを特定します。

図2-1 では、クラウドインフラストラクチャ対応アプリケーションを最新化成熟度レベルで位置付けます。

![クラウドインフラストラクチャ対応アプリケーションの配置](./media/image2-1.png)

> **図 2-1** クラウドインフラストラクチャ対応アプリケーションの配置

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>既存の .NET web アプリケーションを Azure IaaS に移行する理由

最初の IaaS レベルでもクラウドに移行する主な理由は、コスト削減を実現することです。 より多くの管理されたインフラストラクチャサービスを使用することにより、組織はハードウェアメンテナンス、サーバーまたは VM のプロビジョニングとデプロイ、インフラストラクチャ管理への投資を削減できます。

アプリをクラウドに移動するかどうかを決定した後、PaaS などのより高度なオプションではなく IaaS を選択する主な理由は、IaaS 環境の方が使い慣れているということです。 現在のオンプレミス環境に似た環境に移行することで、クラウドへの最短のパスを実現する、より低い学習曲線が得られます。

ただし、クラウドへのパスを最も簡単にすることは、アプリケーションをクラウドで実行することによって最も大きなメリットを得られるわけではありません。 組織では、クラウドに最適化されたクラウドネイティブの成熟度レベルで、クラウドの移行によって最も大きなメリットを得ることができます。

また、アプリケーションが既にクラウドで実行されている場合、IaaS 上でも、アプリケーションの最新化と再設計が容易になることが明らかになりました。 アプリケーションデータの移行は既に完了しています。 また、お客様の組織はクラウドでの作業に必要なスキルを獲得し、"クラウド文化" で稼働させることができます。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>PaaS ではなく IaaS に移行する場合

次のセクションでは、ほとんどが PaaS プラットフォームとサービスに基づいているクラウド向けに最適化されたアプリケーションについて説明します。 これらのアプリでは、クラウドへの移行によって最も大きなメリットが得られます。 

既存のアプリケーションをクラウドに移行するだけの場合は、まず、Azure App Service で実行するために大幅な変更を必要としない既存のアプリケーションを特定します。 これらのアプリは、クラウドに最適化された最初の候補です。 

その後も、Azure Kubernetes Service などの Windows コンテナーや App Service PaaS に移行できないアプリの場合は、それらを単純な plain Vm (IaaS) に移行します。 

ただし、Azure で PaaS サービスを使用する場合と比べて、Vm の構成、セキュリティ保護、およびメンテナンスには、より多くの時間と IT の専門知識が必要であることに注意してください。 Azure Virtual Machines を検討している場合は、VM 環境を修正、更新、管理するために必要な継続的なメンテナンス作業を必ず考慮してください。 Azure Virtual Machines は IaaS です。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Azure Migrate を使用して既存のアプリケーションを分析し、Azure に移行する

クラウドへの移行は困難である必要はありません。 しかし、多くの組織では、環境を深く可視化し、アプリケーション、ワークロード、データ間の密接な相互依存関係を把握することが困難になっています。 このような可視性がないと、パスの計画が困難になる可能性があります。 移行を成功させるために必要な情報の詳細がないと、組織内で適切な会話を行うことができません。 潜在的なコスト上の利点については十分ではありません。また、ワークロードが急激に増加したり、移行を成功させる必要があるかどうかがわかりません。 多くの組織には何もありません。

[Azure Migrate](https://aka.ms/azuremigrate)は、Azure への移行を支援するために必要なガイダンス、洞察、およびメカニズムを提供する新しいサービスです。 Azure Migrate は次のとおりです。

- オンプレミスの仮想マシンの検出と評価

- 多階層アプリケーションの信頼性の高い検出のための組み込みの依存関係マッピング

- Azure 仮想マシンへのインテリジェントなサイズ変更

- 修復の潜在的な問題に関するガイドラインを含む互換性レポート

- データベースの検出と移行のための Azure Database Management Service との統合

Azure Migrate を使用すると、ビジネスへの影響を最小限に抑えながら、ワークロードを移行し、Azure で期待どおりに実行することができます。 適切なツールとガイダンスを使用すると、重要なパフォーマンスと信頼性のニーズが満たされていることを確認しながら、投資収益率を最大限に高めることができます。

図2-2 は、Azure Migrate によって実行されるすべてのサーバーとアプリケーションの接続に対する組み込みの依存関係マッピングを示しています。

![クラウドインフラストラクチャ対応アプリケーションの配置](./media/image2-2.png)

> **図 2-2** クラウドインフラストラクチャ対応アプリケーションの配置

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Azure Site Recovery を使用して既存の Vm を Azure Vm に移行する

[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)は、エンドツーエンドの[Azure Migrate](https://aka.ms/azuremigrate)の一部として、Azure の vm に web アプリを簡単に移行するために使用できるツールです。 Site Recovery を使用して、オンプレミスの Vm と物理サーバーを Azure にレプリケートしたり、オンプレミスのセカンダリの場所にレプリケートしたりすることができます。 サポートされている Azure VM、オンプレミスの*Hyper-v* Vm、 *VMware* VM、または Windows または Linux の物理サーバーで実行されているワークロードをレプリケートすることもできます。 Azure へのレプリケーションにより、セカンダリデータセンターを維持するためのコストと複雑さが解消されます。

Site Recovery は、一部がオンプレミスで、一部が Azure 上にあるハイブリッド環境に対しても特に作成されます。 Site Recovery は、サイトがダウンした場合に、Vm 上で実行されているアプリとオンプレミスの物理サーバーを使用できるようにすることで、ビジネス継続性を確保するのに役立ちます。 Vm と物理サーバーで実行されているワークロードをレプリケートして、プライマリサイトが利用できない場合にセカンダリの場所でも使用できるようにします。 ワークロードは、起動して再実行されると、プライマリサイトに回復します。

図2-3 は Azure Site Recovery を使用した複数の VM の移行の実行を示しています。

![クラウドインフラストラクチャ対応アプリケーションの配置](./media/image2-3.png)

> **図 2-3.** クラウドインフラストラクチャ対応アプリケーションの配置

### <a name="additional-resources"></a>その他の技術情報

- **Azure Migrate データシート**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Azure Migration Center**

    <https://azure.microsoft.com/migration/>

- **Site Recovery を使用した Azure への移行**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure Site Recovery サービスの概要**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **AWS 内の Vm の Azure Vm への移行**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->

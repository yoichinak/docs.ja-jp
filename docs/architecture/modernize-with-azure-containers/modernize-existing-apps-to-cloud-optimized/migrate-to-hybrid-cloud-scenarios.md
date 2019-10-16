---
title: ハイブリッド クラウド シナリオへの移行
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |ハイブリッドクラウドシナリオへの移行
ms.date: 04/30/2018
ms.openlocfilehash: 4348a9b538042fee7ebd9c08f480491f17425937
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394546"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>ハイブリッド クラウド シナリオへの移行

一部の組織や企業では、規制や独自のポリシーによって、アプリケーションの一部を Microsoft Azure やその他のパブリッククラウドに移行することはできません。 ただし、組織によっては、パブリッククラウドやその他のアプリケーションにオンプレミスのアプリケーションを配置することでメリットが得られる可能性があります。 ただし、混在環境では、パブリッククラウドとオンプレミス環境の間で使用されるプラットフォームやテクノロジが異なるため、環境が複雑になる可能性があります。

Microsoft は最適なハイブリッドクラウドソリューションを提供しています。1つは、オンプレミスとパブリッククラウドの既存の資産を最適化しながら、Azure ハイブリッドクラウドの一貫性を確保することです。 Azure Stack (オンプレミス) と Azure (パブリッククラウド) を使用して、クラウドまたはオンプレミスで実行できるアプリを構築するための柔軟で統合されたアプローチを実現できます。

セキュリティに関しては、ハイブリッドクラウド全体で管理とセキュリティを一元化することができます。 オンプレミスとクラウドのアプリにシングルサインオンを提供することで、データセンターからクラウドへのすべての資産を制御できます。 これを実現するには、Active Directory をハイブリッドクラウドに拡張し、id 管理を使用します。

最後に、データをシームレスに分散して分析し、クラウドとオンプレミスの資産に同じクエリ言語を使用し、ソースに関係なく、データを強化するために Azure で分析とディープラーニングを適用できます。

## <a name="azure-stack"></a>Azure Stack

Azure Stack は、組織のデータセンターから Azure サービスを提供できるハイブリッドクラウドプラットフォームです。 Azure Stack は、エッジ環境や接続されていない環境など、主要なシナリオにおける最新のアプリケーションの新しいオプションをサポートするように設計されています。また、特定のセキュリティ要件やコンプライアンス要件を満たすことができます

図4-13 は、Microsoft が提供する真のハイブリッドクラウドプラットフォームの概要を示しています。

![Azure Stack と Azure を使用した Microsoft ハイブリッドクラウドプラットフォームの図。](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**図 4-13.** Azure Stack と Azure を使用した Microsoft ハイブリッドクラウドプラットフォーム

Azure Stack は、ニーズに合わせて2つのデプロイオプションで提供されます。

- Azure Stack 統合システム

- Azure Stack Development Kit

### <a name="azure-stack-integrated-systems"></a>Azure Stack 統合システム

Azure Stack 統合システムは、Microsoft とハードウェアパートナーのパートナーシップを通じて提供されます。 このパートナーシップにより、管理の簡略化とバランスを取るクラウドペースのイノベーションを提供するソリューションが作成されます。 Azure Stack はハードウェアとソフトウェアの統合システムとして提供されているので、クラウドからイノベーションを採用するだけでなく、柔軟性と制御性が適切に得られます。 Azure Stack 統合システムは、4 ~ 12 のノードのサイズの範囲であり、ハードウェアパートナーと Microsoft によって共同でサポートされています。 Azure Stack 統合システムを使用して、運用環境のワークロードに新しいシナリオを実装します。

### <a name="azure-stack-development-kit"></a>Azure Stack Development Kit

Microsoft Azure Stack Development Kit は、Azure Stack の単一ノードデプロイであり、Azure Stack の評価と学習に使用できます。 開発環境として Azure Stack Development Kit を使用することもできます。この環境では、Azure と一貫性のある Api とツールを使用して開発できます。 Azure Stack Development Kit は、運用環境として使用するためのものではありません。

### <a name="additional-resources"></a>その他の技術情報

- **Azure ハイブリッドクラウド**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Windows コンテナーのサービスアカウントの Active Directory**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Active Directory サポートを持つコンテナーを作成する**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Azure ハイブリッド特典ライセンス**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[前へ](life-cycle-ci-cd-pipelines-devops-tools.md)
>[次へ](../walkthroughs-technical-get-started-overview.md)

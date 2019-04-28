---
title: ハイブリッド クラウド シナリオへの移行
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |ハイブリッド クラウドのシナリオへの移行します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b04c6edecf5b63f191cb2e0f808fb1d0f801d0a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936730"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>ハイブリッド クラウド シナリオへの移行

一部の組織や企業は、Microsoft Azure などのパブリック クラウドにアプリケーションの一部または規制や独自のポリシーのための他のパブリック クラウドを移行できません。 ただし、すべての組織がパブリック クラウドとその他のアプリケーションをオンプレミスでのアプリケーションの一部がメリットが高くなります。 混在する環境がさまざまなプラットフォームやパブリック クラウドとオンプレミス環境で使用するテクノロジにより環境での過剰な複雑さを招くことができます。

Microsoft では、最適なハイブリッド クラウド ソリューションを提供する、既存の資産を最適化できますいずれか、オンプレミスとパブリック クラウド中、Azure のハイブリッド クラウドでの一貫性を確保します。 既存のスキルを最大化し、クラウドまたはオンプレミス、Azure Stack (オンプレミス) と Azure (パブリック クラウド) のおかげで実行できるアプリを構築するための柔軟かつ統合されたアプローチを取得できます。

セキュリティに関しては、ハイブリッド クラウドの間での管理とセキュリティを一元化できます。 オンプレミスへのシングル サインオンを提供することで、クラウドにデータ センターからすべての資産の制御を取得し、クラウド アプリできます。 ために Active Directory、ハイブリッド クラウドを拡張および id 管理を使用して、します。

最後に、配布しシームレスにデータを分析、クラウドとオンプレミスの資産に対して同じクエリ言語を使用し、適用できます分析とディープ ラーニング、azure にそのソースに関係なく、データを操作します。

## <a name="azure-stack"></a>Azure Stack

Azure Stack は、ハイブリッド クラウド プラットフォーム、組織のデータ センターから Azure サービスを提供することができます。 Azure Stack は edge および接続されていない環境では、または特定のセキュリティとコンプライアンス要件を満たすように、主要なシナリオで、最新のアプリケーション用の新しいオプションをサポートするために設計されています。

図 4-13 は、Microsoft が提供する、真のハイブリッド クラウド プラットフォームの概要を示します。

![Azure Stack と Azure での Microsoft ハイブリッド クラウド プラットフォーム](./media/image13.jpg)

> **図 4-13。** Azure Stack と Azure での Microsoft ハイブリッド クラウド プラットフォーム

Azure Stack は、ニーズに合わせて、2 つのデプロイ オプションで提供されています。

- Azure Stack 統合システム

- Azure Stack Development Kit

### <a name="azure-stack-integrated-systems"></a>Azure Stack 統合システム

Azure Stack 統合システムは、Microsoft とハードウェア パートナーのパートナーシップによって提供されます。 パートナーシップは、わかりやすくするための管理とのバランスがとれてクラウド歩調のイノベーションを実現するソリューションを作成します。 ハードウェアとソフトウェアの統合システムとして Azure Stack が提供されるため、まだクラウドの革新技術を採用することに適切な量の柔軟性と制御が表示します。 Azure Stack 統合システムはまでのサイズを 4 から 12 個のノードにあり、ハードウェア パートナーと Microsoft によって共同でサポートされます。 Azure Stack 統合システムを使用すると、実稼働ワークロード向けの新しいシナリオを実装します。

### <a name="azure-stack-development-kit"></a>Azure Stack Development Kit

Microsoft Azure Stack Development Kit は、評価し、Azure Stack の学習に使用できる Azure Stack の単一ノード デプロイです。 Api を使用して開発することができます、Azure と一貫性のあるツールを開発環境として Azure Stack Development Kit を使用することもできます。 Azure Stack Development Kit は、運用環境として使用するものではありません。

### <a name="additional-resources"></a>その他の技術情報

- **Azure のハイブリッド クラウド**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Windows コンテナーの active Directory サービス アカウントします。**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Active Directory のサポートによってコンテナーを作成します。**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Azure Hybrid Benefit のライセンス**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[前へ](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[次へ](../walkthroughs-technical-get-started-overview.md)

---
title: Service Fabric に Windows コンテナーを展開するタイミング
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |Service Fabric に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 01d76f325480c7cf09fef36b02589a602e3ee11e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973655"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Service Fabric に Windows コンテナーを展開するタイミング

Windows コンテナーに基づくアプリケーションは簡単に IaaS Vm から離れて、さらに移動するプラットフォームを使用する必要があります。 これは、自動のスケーラビリティが向上し、高いスケーラビリティ、および展開では、完全な管理エクスペリエンスが大幅に向上できるアップグレード バージョン管理、ロールバック、および正常性の監視します。 Azure Service Fabric、または Microsoft Azure クラウドではまた、オンプレミスの別のクラウドであっても使用できます。 orchestrator と、これらの目標を実現できます。

多くの組織はのリフト アンド シフト既存のモノリシック アプリケーションをコンテナーに 2 つの理由。

- コストの削減、いずれかの理由の統合と既存のハードウェア、またはより高密度でアプリケーションを実行してから削除します。

- 開発と運用の間で一貫したデプロイ コントラクト。

わかりやすいものには、コストの削減を追求し、すべての組織がその目標を追跡は高くなります。 評価するために一貫した展開が困難が重要なこととしては、同じようになります。 一貫したデプロイ コントラクトは、開発者は、それに合ったテクノロジを使用して選択する自由を運用チームは、アプリケーション デプロイおよび管理する方法を取得します。 を述べています。 本契約は、多くのさまざまなテクノロジの複雑さを処理操作または強制的に特定のテクノロジだけで使用する開発者の苦労を軽減します。 基本的には、各アプリケーションは自己完結型の展開イメージにコンテナー化されました。

一部の組織はマイクロ サービス (クラウド ネイティブ アプリケーション) を追加することで最新化を続行しますが、その他の多くの組織がここで (クラウドに最適化されたアプリケーション) で停止されます。 図 4-8 に示すようにする必要がある可能性がありますいないために、これらの組織がマイクロ サービス アーキテクチャに移動しません。 いずれの場合も、これらは、コンテナーと Service Fabric を使用して、展開を含む完全な管理を提供するエクスペリエンスのアップグレードの特典、バージョン管理、ロールバック、および正常性の監視に既に取得します。

> ![リフト アンド シフトを Service Fabric アプリケーション](./media/image8.png)
>
> **図 4-8。** リフト アンド シフトを Service Fabric アプリケーション

既存のコードを再利用し、リフト アンド シフトすることを Service Fabric の重要なアプローチです。 そのため、Windows のコンテナーを使用して、現在の .NET Framework アプリケーションを移行し、それらを Service Fabric にデプロイできます。 移動を最新化、最終的には、新しいマイクロ サービスを追加することで維持しやすくなります。

Service Fabric を他のオーケストレーターを比較する場合は、Service Fabric は Windows ベースのアプリケーションとサービスの実行に成熟したことを強調表示する必要があります。 Windows ベースのサービスと年の第 1 層、ミッション クリティカルな Microsoft 製品を含む、アプリケーションは、Service Fabric が実行されているがされています。 Windows コンテナーの一般的な可用性を最初の orchestrator がありました。 Kubernetes、DC/OS、Docker Swarm などの他のコンテナーは、Service Fabric の Windows ベースのアプリケーションと Windows コンテナーより成熟していないが、Linux より成熟したです。

Service Fabric の最終的な目標では、マイクロ サービス アプローチを使用してアプリケーションを構築するための複雑性を低減します。 特定の種類をコストのかかる再設計を避けるためにアプリケーションのマイクロ サービスを最終的にします。 最初は小規模、必要に応じて拡張する、サービスを非推奨に、新しいサービスを追加してお客様による使用を使用してアプリケーションを進化できます。 ほとんどの開発者にマイクロ サービスをよりわかりやすくために解決するにはまだ他の多くの問題があります。 現在がだけリフト アンド シフトと Windows コンテナーでは、アプリケーション、将来のコンテナーに基づくマイクロ サービスを追加する方法について検討している場合は、Service Fabric の得意分野です。

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[次へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
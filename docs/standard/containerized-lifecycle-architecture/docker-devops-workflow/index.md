---
title: Microsoft ツールを使用した Docker アプリケーション DevOps ワークフロー
description: Microsoft のツールを使用して Microsoft プラットフォームとツールの DevOps ワークフローにコンテナー化された Docker アプリケーション ライフ サイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 80acd58d08900da8e79f6b7388da3b10f9e4e566
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672304"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft ツールを使用した Docker アプリケーション DevOps ワークフロー

*Microsoft Visual Studio、Azure DevOps サービス、Team Foundation Server、および Azure Monitor のテスト、および展開の開発と IT 運用チームのプロジェクト管理と迅速にビルドすると、ツールを提供するコンテナー化包括的なエコシステムを提供します。アプリケーション。*

Visual Studio Team Foundation Server、オンプレミス、と共に、クラウドでの Azure DevOps サービスを開発チームできます生産的ビルド、テスト、およびコンテナー化されたアプリケーションを Windows または Linux を対象とするリリースします。

マイクロソフトのツールは、コンテナー化されたアプリケーションの特定の実装のパイプラインを自動化できます: Docker、.NET Core、またはその他のプラットフォームで任意の組み合わせ、グローバル ビルドと継続的インテグレーション (CI) および Azure DevOps サービスまたはチームでのテストからFoundation Server に継続的デプロイ (CD) Docker 環境 (開発、ステージング、運用)、および Azure Monitor を通じて開発チームにサービスに関する分析情報を送信します。 すべてのコードのコミットでビルド (CI) を開始して、特定のコンテナー化された環境 (CD) に自動的にサービスを展開できます。

開発者およびテスト担当者は、Microsoft Azure のテンプレートを使用して、Docker に基づく運用環境のような開発とテストの環境を、簡単かつ迅速にプロビジョニングできます。

コンテナー化アプリケーションの開発は、ビジネスが複雑であり、拡張のニーズがあればあるほど、着実に複雑になります。 このような複雑さの良い例は、マイクロ サービス アーキテクチャに基づくアプリケーションです。 プロジェクトには、このような環境で成功のライフ サイクル全体を自動化する必要があります: テレメトリの収集とバージョンを管理する必要がありますも、ビルドと展開、だけでなく、します。 Azure DevOps サービスと Azure は次の機能を提供します。

- Azure DevOps Services と Team Foundation Server ソース コード管理 (Git または Team Foundation バージョン管理に基づく)、アジャイル計画 (アジャイル、スクラム、CMMI がサポートされています)、CI、リリース管理、およびアジャイル チームの他のツール。

- Azure DevOps サービスと Team Foundation Server には、使用して簡単にできます構築 CI、ビルド、テスト、配信、リリース管理パイプライン マイクロ サービスの 1 つ目とサード パーティの拡張機能の増加し、強力なエコシステムが含まれます。

- Azure DevOps サービスのビルド パイプラインの一部として自動テストを実行します。

- Azure DevOps サービスは複数の環境への配信を使用した DevOps ライフ サイクル、実稼働環境でだけでなく、テストに対してもを強化できる A を含む/B 実験、[カナリア リリース](https://martinfowler.com/bliki/CanaryRelease.html)など。

- 組織は簡単に Azure のコンポーネント (Data、PaaS など) への依存関係と共に、Azure Container Registry に格納されているプライベート イメージから Docker コンテナーをプロビジョニングできます、使い慣れているツールを使用して Azure Resource Manager テンプレートを使用します。

>[!div class="step-by-step"]
>[前へ](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[次へ](docker-application-outer-loop-devops-workflow.md)

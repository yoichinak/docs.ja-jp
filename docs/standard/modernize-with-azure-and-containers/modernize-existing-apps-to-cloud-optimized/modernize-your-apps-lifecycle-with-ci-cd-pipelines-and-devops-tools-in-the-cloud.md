---
title: クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。
ms.date: 04/30/2018
ms.openlocfilehash: 7a0005da56e2d8ab7a2348f9032f887451132558
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638954"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する

今日の企業では、市場で競争力のある迅速なペースでイノベーションを実現する必要があります。 高品質を提供するには、最新のアプリケーションには、DevOps ツールと技術革新のこの定数のサイクルを実装するために不可欠なプロセスが必要です。 適切なの DevOps ツールでは、開発者は継続的なデプロイを合理化し、ユーザーの手に革新的なアプリケーションを迅速に取得します。

継続的インテグレーションとデプロイのプラクティスは準備されていますが、マルチ コンテナー アプリケーションを使用する場合に特にコンテナーの概要、新しい考慮事項について説明します。

Azure DevOps サービスには、継続的インテグレーションとさまざまな公式の Azure DevOps サービス展開作業を環境に複数コンテナー アプリケーションの展開がサポートされています。

- [スタンドアロンの Docker ホスト VM にデプロイ](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm)(Linux または Windows Server 2016 以降)

- [Service Fabric へのデプロイします。](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

- [Azure Container Service と Kubernetes にデプロイします。](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

展開できますが、 [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)または DC/OS Azure DevOps サービス スクリプト ベースのタスクを使用しています。

デプロイの機敏性を促進することを続行するには、は、これらのツールは、コンテナーのワークロードでは、開発と CI/CD の解決策の選択肢を備えた優れた開発-テスト-運用デプロイのエクスペリエンスを提供します。

図 4-12 には、Azure Container Service で Kubernetes クラスターにデプロイする継続的配置パイプラインが表示されます。

![Azure DevOps サービスの継続的なデプロイ パイプライン、Kubernetes クラスターへのデプロイ](./media/image12.png)

> **図 4-12。** Azure DevOps サービスの継続的なデプロイ パイプライン、Kubernetes クラスターへのデプロイ

>[!div class="step-by-step"]
>[前へ](modernize-your-apps-with-monitoring-and-telemetry.md)
>[次へ](migrate-to-hybrid-cloud-scenarios.md)

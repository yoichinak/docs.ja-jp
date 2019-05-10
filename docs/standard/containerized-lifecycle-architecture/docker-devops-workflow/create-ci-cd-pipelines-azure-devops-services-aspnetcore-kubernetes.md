---
title: Docker アプリケーションの外側のループ DevOps ワークフローの手順
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e11c9ec61ea7d5131595f01ce76b5bb810bb70c0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063313"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>コンテナーで.NET Core 2.0 アプリケーション用の Azure DevOps Services で CI/CD パイプラインを作成し、Kubernetes クラスターにデプロイする

図 5-12 でコードの管理、コードのコンパイルをカバーするエンド ツー エンド DevOps シナリオを参照できます、Docker イメージを構築、Docker レジストリと最後に Azure での Kubernetes クラスターに展開する Docker イメージをプッシュします。

![ワークフロー:開発用コンピューターで開始します。 カスタムのイメージを Docker レジストリにプッシュし、使用して、CD/デプロイ タスクで最後に、AKS へのプッシュを使用して、ビルド/CI タスクを開始するをリポジトリにプッシュします。](media/docker-workflow-ci-cd-aks.png)

**図 5-12** Docker イメージを作成して、Azure で Kubernetes クラスターへのデプロイの CI/CD シナリオ

(Docker Hub や Azure Container Registry) などの Docker レジストリを使用して 2 つのパイプライン、ビルド/CI、およびリリース/CD が接続されていることを強調表示に重要です。 Docker レジストリでは、Docker を使用しない従来の CI/CD プロセスと比較する主な相違点の 1 つです。

図 5-13 に示すように、最初のフェーズは、ビルド/CI パイプラインにします。 Azure DevOps サービスでは、コードをコンパイル、Docker イメージを作成およびそれらを Docker Hub や Azure Container Registry のような Docker レジストリにプッシュされるビルド/CI パイプラインを作成できます。

![Azure DevOps、ビルド プロセスのタスク定義のブラウザー ビュー。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**図 5-13** Azure DevOps Docker イメージをビルドし、Docker レジストリにイメージをプッシュのビルド/CI パイプライン

2 番目のフェーズでは、展開/リリース パイプラインを作成します。 Azure DevOps サービスで、図 5-14 に示すように、Azure DevOps サービス、Kubernetes タスクを使用して Kubernetes クラスターを対象とするデプロイ パイプラインを簡単に作成することができます。

![Azure DevOps, のブラウザー ビューは、タスクの定義を Kubernetes にデプロイします。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**図 5-14** Azure DevOps サービスが Kubernetes クラスターに展開するリリース/CD パイプライン

> [!チュートリアル] eShopModernized を Kubernetes にデプロイします。
>
> Azure DevOps CI/CD パイプラインの詳細なチュートリアルについては、Kubernetes に展開するこの投稿を表示します \。
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[前へ](docker-application-outer-loop-devops-workflow.md)
>[次へ](../run-manage-monitor-docker-environments/index.md)

---
title: Azure Container Instances (ACI) に Windows コンテナーを展開するタイミング
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |Azure Container Instances (ACI) に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 03ee7c8b65e1a92dcc7fd40b44e9ba081f571487
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674407"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Azure Container Instances (ACI) に Windows コンテナーを展開するタイミング

Azure Container Instances は、主な価値提案は、すぐにコンテナーをデプロイすることができ、その環境を維持する必要はありません、基になるオペレーティング システムまたは Vm すべてに対して透過的なアップグレード/修正する必要はありませんし、展開します。コンテナーをすぐに使用できる環境にします。

上の理由から、ACI を使用する場合のシナリオは主なシナリオのような基本的に、コンテナーを Azure Vm を使用すると、Azure Container Instances を使用する主なシナリオは。

- **開発/テスト シナリオ**
- **タスクの自動化**
- **エージェントの CI/CD**
- **小規模スケール/バッチ処理**
- **単純な web アプリ**

単純な web アプリのシナリオは ACI の公正なシナリオが ACI でコンテナー イメージごとの 1 つのコンテナー インスタンスでのみ設定できる、ので高可用性はありませんをスケーラビリティが制限を考慮します。

ただし、ACI は 1 つのコンテナー インスタンスを提供するだけであるために、インフラストラクチャと見なされます、できなくては大きなメリットを Windows Server の通常の Azure Vm と比較します。 ACI、自己保持型の環境にのみ、コンテナーをデプロイしてそれらのコンテナーだけ支払います。 場所を使用している Vm、コンテナーを含むほとんどのシナリオの多くにより良いプラットフォームのため、保守/更新/パッチ適用、Vm に必要はありません。 ACI を使用して簡単には、コンテナーを配置する、だけにコンテナーをデプロイする VM 環境を作成する必要はありません。

Azure Container Instances (ACI) の主な利点は次のとおりです。

- サーバーを管理することがなくコンテナーを実行します。
- オンデマンドでのコンテナーでの機敏性を高める
- 前例のないシンプルさと速度で、クラウドへのコンテナーのデプロイ-1 つのコマンドを使用します。
- ハイパーバイザー分離を使用したセキュリティで保護されたアプリケーション

つまり、ACI では、仮想マシンを管理または新しいツールを学習することがなく高速アプリを開発できます。 クラウドで実行しているコンテナーで、アプリケーションだけになります。

> [!div class="step-by-step"]
> [前へ](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [次へ](when-to-deploy-windows-containers-to-service-fabric.md)

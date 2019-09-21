---
title: Windows コンテナーを Azure Container Instances (ACI) に展開する場合
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |Windows コンテナーを Azure Container Instances (ACI) に展開する場合
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577935"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Windows コンテナーを Azure Container Instances (ACI) に展開する場合

主な価値の提案は、コンテナーをすぐにデプロイでき、その環境を維持する必要がなく、基になるオペレーティングシステムまたは Vm をアップグレード/修正する必要がないことです。これはすべて透過的で、デプロイするだけです。 Azure Container Instancesコンテナーをすぐに使用可能な環境にします。

ACI を使用する理由とシナリオは、コンテナーで Azure Vm を使用する場合の主なシナリオに似ています。基本的に、Azure Container Instances を使用する主なシナリオは次のとおりです。

- **開発/テストシナリオ**
- **タスクの自動化**
- **CI/CD エージェント**
- **小/小数点以下のバッチ処理**
- **単純な web アプリ**

単純な web apps シナリオは、ACI の公正なシナリオですが、ACI ではコンテナーイメージごとに1つのコンテナーインスタンスしか持つことができないため、高可用性はなく、スケーラビリティも制限されています。

ただし、1つのコンテナーインスタンスだけを提供するため、ACI がインフラストラクチャと見なされる場合でも、Windows Server を使用した通常の Azure Vm と比較して大きな利点があります。 ACI を使用すると、コンテナーを自己保守環境にデプロイするだけで、これらのコンテナーに対して料金が請求されます。 Vm を管理/更新/修正する必要はありません。そのため、コンテナーで Vm を使用している可能性のあるほとんどのシナリオでは、はるかに優れたプラットフォームとなります。 ACI を使用すると、コンテナーをデプロイするだけで、コンテナーをデプロイするだけで VM 環境を作成する必要がなくなります。

Azure Container Instances (ACI) の主な利点は次のとおりです。

- サーバーを管理せずにコンテナーを実行する
- コンテナーの俊敏性をオンデマンドで向上
- 1つのコマンドを使用して、従来よりもシンプルで高速な方法でコンテナーをクラウドにデプロイできます。
- ハイパーバイザー分離を使用したアプリケーションのセキュリティ保護

つまり、ACI を使用すると、仮想マシンを管理したり、新しいツールを習得したりすることなく、アプリを迅速に開発できます。 これは、クラウドで実行されているコンテナー内のアプリケーションにすぎません。

> [!div class="step-by-step"]
> [前へ](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [次へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)

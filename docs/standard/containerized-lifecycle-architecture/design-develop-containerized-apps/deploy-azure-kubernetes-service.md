---
title: 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
description: Azure Kubernetes サービスを使用してアプリをデプロイする方法について説明します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 82a1cf7f3cc367bfb8b8f67a130600815f2a21c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006544"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) へのデプロイ

推奨されるクライアント オペレーティング システムを使用する AKS と対話できます、ここ方法について説明しますで Microsoft Windows と埋め込みのバージョンでは、Windows、Ubuntu Linux の Bash コマンドを使用しています。

AKS を使用する前に前提条件は次のとおりです。

- Linux または Mac の開発用コンピューター
- Windows 開発用コンピューター
  - Windows で有効になって、開発者モード
  - Windows Subsystem for Linux
- Azure CLI にインストールされている[Windows、Mac または Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> 完全な情報の検索について。
>
> Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest>
>
> Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Azure での AKS 環境を作成します。

AKS の環境を作成するいくつかの方法はあります。 これは、Azure CLI コマンドを使用して、または Azure portal を使用して実行できます。

ここで、Azure CLI を使用して、クラスターと、結果を確認する、Azure ポータルを作成する例をいくつかを調べることができます。 また、Kubectl と Docker 開発用コンピューターにある必要があります。  

## <a name="create-the-aks-cluster"></a>AKS クラスターを作成します。

このコマンドを使用して AKS クラスターを作成します。

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

作成ジョブが完了したら後、は、Azure portal で作成された AKS を確認できます。

リソース グループ:

![Azure AKS リソース グループのブラウザー ビュー。](media/aks-resource-group-view.png)

**図 4-17**.  Azure から AKS リソース グループ ビュー。

AKS クラスター:

![AKS リソース グループのブラウザー ビュー。](media/aks-cluster-view.png)

**図 4-18**. AKS は、Azure から表示します。

使用して作成されたノードを表示することもできます。`Azure-CLI`と`Kubectl`します。

最初に、資格情報の取得。

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上記のコマンドから出力コンソール:マージされた"MsSampleK8Cluster/root/.kube/config で現在のコンテキストとして選択します。](media/get-credentials-command-result.png)

**図 4-19** `aks get-credentials` コマンドの結果。

その後、Kubectl からノードを取得する:

```console
kubectl get nodes
```

![コンソールは、上記のコマンドの出力:状態、経過時間 (時間実行されている)、およびバージョンを持つノードの一覧](media/kubectl-get-nodes-command-result.png)

**図 4-20** `kubectl get nodes` コマンドの結果。

>[!div class="step-by-step"]
>[前へ](orchestrate-high-scalability-availability.md)
>[次へ](docker-apps-development-environment.md)

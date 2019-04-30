---
title: Azure Container Service (つまり Kubernetes) に Windows コンテナーを展開するタイミング
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |Azure Container Service (つまり Kubernetes) に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 0b803b104f905fddac7939d7b070c206aabffeda
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011971"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Azure Container Service (つまり Kubernetes) に Windows コンテナーを展開するタイミング

Azure Container Service では、Azure 向けに人気のあるオープン ソース ツールとテクノロジの構成を最適化します。 コンテナーと、アプリケーションの構成の両方の移植性を提供する、開いているソリューションが表示されます。 サイズ、ホスト数およびオーケストレーション ツールを選択します。 Azure Container Service では、インフラストラクチャを処理します。

Kubernetes、Docker Swarm、DC/OS などのオープン ソース オーケストレーターを使用して既に場合、は、コンテナー ワークロードをクラウドに移動する、既存の管理方法を変更する必要はありません。 使い慣れているアプリケーションの管理ツールを使用し、好みの orchestrator の標準 API エンドポイント経由で接続します。

これらすべてのオーケストレーターは、Linux Docker コンテナーなどを使用している Windows コンテナー用のプレビュー状態である可能性がありますのみ場合の完成度の高い環境です。

たとえば、Kubernetes では、サポートのコンテナーは Kubernetes で Windows コンテナーを使用してネイティブ (優良市民) も (2018 年初頭の時点で、ACS でプレビュー) で効果的です。

重要な注意事項:進化、および"以上の PaaS"Kubernetes 用 ACS (Azure Container Service) のバージョンは、AKS (Azure Kubernetes Service)、ただし、Windows コンテナーはまだサポートされていません、第 2 四半期 2018 がまもなくサポートされます。

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-to-service-fabric.md)
>[次へ](choosing-azure-compute-options-for-container-based-applications.md)
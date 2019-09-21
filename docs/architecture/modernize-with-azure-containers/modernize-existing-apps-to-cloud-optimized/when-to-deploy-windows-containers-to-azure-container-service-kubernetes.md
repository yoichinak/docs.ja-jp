---
title: Azure Container Service に Windows コンテナーを展開する場合 (つまり、Kubernetes)
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |Azure Container Service に Windows コンテナーを展開する場合 (つまり、Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577945"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Azure Container Service に Windows コンテナーを展開する場合 (つまり、Kubernetes)

Azure Container Service は、Azure 専用の一般的なオープンソースのツールとテクノロジの構成を最適化します。 コンテナーとアプリケーションの構成の両方で移植性を提供するオープンソリューションを利用できます。 サイズ、ホスト数、および orchestrator ツールを選択します。 インフラストラクチャは、Azure Container Service によって処理されます。

Kubernetes、Docker の群れ、DC/OS などのオープンソースのオーケストレーター既に使用している場合は、コンテナーのワークロードをクラウドに移行するために、既存の管理方法を変更する必要はありません。 使い慣れているアプリケーション管理ツールを使用し、任意の orchestrator の標準 API エンドポイントを介して接続します。

Linux Docker コンテナーを使用している場合は、これらのすべてのオーケストレーター成熟した環境になりますが、Windows コンテナーのプレビュー状態のみになる可能性があります。

たとえば、Kubernetes では、コンテナーのサポートはネイティブ (ファーストクラスの市民) であるため、Kubernetes で Windows コンテナーを使用することもできます (ACS でのプレビュー版は2018以前)。

重要な注意:AKS (Azure Kubernetes Service) の ACS (Azure Container Service) の進化した "その他の PaaS" バージョンは Kubernetes ですが、Windows コンテナーは2018年2四半期時点ではまだサポートされていませんが、まもなくサポートされる予定です。

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[次へ](choosing-azure-compute-options-for-container-based-applications.md)

---
title: Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |Windows コンテナーを Azure Vm にデプロイする場合 (IaaS クラウド)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577905"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング

組織で Azure Vm を使用している場合は、Windows コンテナーも使用している場合でも、引き続き IaaS を扱うことになります。 つまり、負荷分散されたインフラストラクチャ内の複数の Vm に展開する必要がある場合は、インフラストラクチャ操作、VM OS パッチ、インフラストラクチャの複雑さを、拡張性の高いアプリケーションのために処理することになります。 Azure VM で Windows コンテナーを使用する主なシナリオは次のとおりです。

- **開発/テスト環境**:クラウド内の VM は、クラウドでの開発とテストに最適です。 必要に応じて、環境を迅速に作成または停止できます。

- **小規模および中規模のスケーラビリティのニーズ**:運用環境に 2 ~ 3 個の Vm が必要になる場合がありますが、少数の Vm を管理すると、orchestrators ようなより高度な PaaS 環境に移行するまで、低価格になります。

- **既存の展開ツールを使用した運用環境**:Vm またはベアメタルサーバー (パペットや同様のツールなど) に複雑なデプロイを行うためのツールに投資しているオンプレミス環境から移行している可能性があります。 運用環境のデプロイ手順に最小限の変更を加えてクラウドに移行するには、引き続きこれらのツールを使用して Azure Vm にデプロイすることができます。 ただし、展開の単位として Windows コンテナーを使用して、デプロイのエクスペリエンスを向上させる必要があります。

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[次へ](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)

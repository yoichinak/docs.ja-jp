---
title: コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833851"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択

前のセクションを読むことがわかりました、Azure は、複数の選択肢を提供するオープン クラウドです。 ただし、これも明らかになります、コンテナー化アプリケーションを使用する必要があります製品/テクノロジに関する質問、ニーズに最適を使用できます。

として、*既定*、推奨事項を次にこのガイドで推奨されている主要な基準。

- **1 つのモノリシック アプリ:** Azure App Service を選択します。
- **N 層アプリ:** 1 つまたはいくつかのバックエンド サービスがある場合は、Azure Kubernetes Service (AKS) または App Service などのオーケストレーターを選択します。
- **マイクロ サービス:** AKS または Azure Web アプリ コンテナーを選択します。
- **サーバーレス関数 (&) のイベント ハンドラー:** Azure Functions を選択します。
- **大規模なバッチの場合:** Azure Batch を選択します。

製品の選択は、特定のアプリケーションのニーズと特性に依存するようにこの推奨事項にわずかな salt、従う必要があります。 すべてのアプリケーションは、最初に類似した種類を検索する場合でも同じです。

さらに詳しく分析のアプリケーションのニーズに応じて、後に選択されている製品が異なる場合があります。 評価を開始からの初期のガイダンスもよいが、開始点として、特定の優先順位に基づくテストします。

次の図には、アプリとホスティングのシナリオに最適ですが Azure のさまざまな種類の内訳を確認できます。

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)

---
title: コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: f251aecfeaf2421a5cecf218577369963bc736fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811760"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択

前のセクションを読むことがわかりました、Azure は、複数の選択肢を提供するオープン クラウドです。 ただし、これも明らかになります、コンテナー化アプリケーションを使用する必要があります製品/テクノロジに関する質問、ニーズに最適を使用できます。

として、*既定*、推奨事項を次にこのガイドで推奨されている主要な基準。

- **1 つのモノリシック アプリ:** Azure App Service を選択します。
- **N 層アプリ:** 1 つまたはいくつかのバックエンド サービスがある場合は、Azure Kubernetes Service (AKS)、Service Fabric (SF) または App Service などのオーケストレーターを選択します。
- **Linux のマイクロ サービス:** AKS と Kubernetes を選択します。
- **Windows のマイクロ サービス:** Service Fabric を選択します。
- **サーバーレス関数 (&) のイベント ハンドラー:** Azure Functions を選択します。
- **大規模なバッチの場合:** Azure Batch を選択します。

製品の選択は、特定のアプリケーションのニーズと特性に依存するようにこの推奨事項にわずかな salt、従う必要があります。 すべてのアプリケーションは、最初に類似した種類を検索する場合でも同じです。

さらに詳しく分析のアプリケーションのニーズに応じて、後に選択されている製品が異なる場合があります。 評価を開始からの初期のガイダンスもよいが、開始点として、特定の優先順位に基づくテストします。

次の図より詳細な意思決定テーブル中にグローバルを分析できます。

![](./media/image8.5.png)

通知方法 (Windows と OS の基になります。Linux) では、一部のオーケストレーターはより完成度の高い Linux コンテナーやその他の Windows コンテナーで、意思決定係数こともできます。 たとえば、Linux コンテナーでは、Service Fabric では未完成ですが、Kubernetes (Azure での AKS) で非常に成熟しました。 その一方で、Windows コンテナーは、(2017 年 5 月にリリースされた) Service Fabric でさらに成熟した AKS では未完成です。

ただし、OS の成熟度でそれらの相違点は今後のフェードインし複数のプラットフォームは比較可能な OS の成熟度られ、意思決定をアプリケーションが必要になるか、各プラットフォームのエコシステムに基づく特定の機能に基づく基本設定の詳細に配置されます。理由があります。

> [!div class="step-by-step"]
> [前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)

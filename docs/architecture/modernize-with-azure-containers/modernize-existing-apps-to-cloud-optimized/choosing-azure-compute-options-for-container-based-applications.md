---
title: コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |コンテナーベースのアプリケーションのための Azure コンピューティングプラットフォームの選択
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318673"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択

前のセクションを読んだ後、Azure は複数の選択肢を提供するオープンクラウドです。 ニーズに最適なものを使用できますが、コンテナー化されたアプリケーションに使用する製品やテクノロジに関する質問も表示されます。

*既定*の推奨事項として、このガイダンスで推奨される主な基準は次のとおりです。

- **単一モノリシックアプリ:** Azure App Service の選択
- **N 層アプリ:** Azure Kubernetes Service (AKS) などのオーケストレーター選択するか、バックエンドサービスが1つまたは少数の場合は App Service を選択します。
- **マイクロサービス**コンテナーに対して AKS または Azure Web Apps を選択する
- **サーバーレス関数 & イベントハンドラー:** Azure Functions の選択
- **大規模なバッチ:** Azure Batch の選択

ただし、この推奨事項は、特定のアプリケーションのニーズと特性に応じて製品の選択が変化するため、salt のピンチを使用することをお勧めします。 すべてのアプリケーションが同じであるとは限りません。

アプリケーションのニーズをより詳しく分析した後、選択された製品が異なる場合があります。 ただし、出発点として、特定の優先順位に基づいて評価とテストを開始できる最初のガイダンスを用意することをお勧めします。

図1では、さまざまな種類のアプリの内訳と、Azure ホスティングの理想的なシナリオを確認できます。

![図 1](./media/image8.5.png)

> [!div class="step-by-step"]
> [前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)

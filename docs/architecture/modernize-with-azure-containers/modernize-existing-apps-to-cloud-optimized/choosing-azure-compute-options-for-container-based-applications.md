---
title: コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |コンテナーベースのアプリケーションのための Azure コンピューティングプラットフォームの選択
ms.date: 05/04/2018
ms.openlocfilehash: 54c5945326fb8a50a39c50552a413580926da2c7
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331965"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択

前のセクションを読んだ後、Azure は複数の選択肢を提供するオープンクラウドです。 ニーズに最適なものを使用できますが、コンテナー化されたアプリケーションに使用する製品やテクノロジに関する質問も表示されます。

*既定*の推奨事項として、このガイダンスで推奨される主な基準は次のとおりです。

- **単一モノリシックアプリ:** Azure App Service の選択
- **N 層アプリ:** バックエンドサービスが1つでも少ない場合でも、Azure Kubernetes Service (AKS) や App Service などのオーケストレーター選択できます。
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

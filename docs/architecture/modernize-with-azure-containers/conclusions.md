---
title: まとめ
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |わかり
ms.date: 10/26/2017
ms.openlocfilehash: c7c4042b224577238ae74bd786d4803e487998e7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578485"
---
# <a name="conclusions"></a>まとめ

- コンテナーベースのソリューションでは、最終的にコストの節約効果が得られます。 コンテナーは、運用環境での依存関係の欠如によって生じる摩擦を取り除くため、デプロイの問題に対するソリューションです。 これらの問題を削除することで、開発/テスト、DevOps、運用の各操作が大幅に改善されます。

- Docker コンテナーは、サーバー ベースのアプリケーションまたはサービスの配置の標準的な単位になっています。

- 運用環境では、orchestrator (Kubernetes など) を使用して、スケーラブルなコンテナーベースのアプリケーションをホストする必要があります。

- コンテナーをホストする Azure Vm は、小規模な開発/テスト環境をクラウドに作成するための迅速で簡単な方法です。

- 既存のアプリケーションから Azure にリレーショナルデータベースを移行する場合、既定では Azure SQL Database Managed Instance が推奨されます。

- Visual Studio 2017 と Image2Docker は、Windows コンテナーで既存の .NET アプリケーションの最新化を開始するための基本的なツールです。これには、作業の開始に関する曲線を加速させる必要があります。

- コンテナー化されたアプリケーションを運用環境に配置するときは、Azure DevOps Services や Jenkins のように、CI/CD パイプライン用の DevOps カルチャと DevOps ツールを常に作成または採用します。

- Microsoft Azure は、Windows コンテナー、クラウドインフラストラクチャ、PaaS サービスを使用して既存の .NET Framework アプリケーションを最新化するための最も包括的で完全な環境を提供します。

>[!div class="step-by-step"]
>[前へ](walkthroughs-technical-get-started-overview.md)

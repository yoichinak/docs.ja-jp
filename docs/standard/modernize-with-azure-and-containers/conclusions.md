---
title: まとめ
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |結論
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 62a9a38ccbe696c34ef799b574c0f5a95bc8f726
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628328"
---
# <a name="conclusions"></a>まとめ

- コンテナー ベースのソリューションは、最終的にはコスト削減のメリットを提供します。 コンテナーは、運用環境での依存関係の欠落によって引き起こされる不整合を削除するための展開に関する問題の解決策です。 これらの問題を削除して、開発/テスト、DevOps、および運用操作大幅に向上します。

- Docker コンテナーは、サーバー ベースのアプリケーションまたはサービスの配置の標準的な単位になっています。

- 運用環境では、拡張性の高い Windows コンテナー ベースのアプリケーションをホストする (Service Fabric、または Kubernetes) などのオーケストレーターを使用する必要があります。

- コンテナーをホストする azure Vm は、クラウドで小規模な開発/テスト環境を作成する高速で簡単な方法です。

- 既存のアプリケーションを Azure から、リレーショナル データベースを移行する場合に、既定で azure SQL Database マネージ インスタンスがお勧めします。

- Visual Studio 2017 と Image2Docker は、作業の開始の学習曲線を向上させることにより、Windows コンテナーで既存の .NET アプリケーションを最新化を開始するための基本的なツールです。

- 実稼働環境でコンテナー化されたアプリケーションを配置するときに作成または DevOps の文化と CI/CD パイプラインで、Azure DevOps サービスや Jenkins などの DevOps ツールを採用するは常に。

- Microsoft Azure では、Windows コンテナー、クラウド インフラストラクチャおよび PaaS サービスで、既存の .NET Framework アプリケーションを近代化する最も包括的な完全な環境を提供します。

>[!div class="step-by-step"]
>[前へ](walkthroughs-technical-get-started-overview.md)
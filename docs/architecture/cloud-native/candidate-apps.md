---
title: クラウド ネイティブの候補アプリ
description: クラウドネイティブアプローチのメリットを享受するアプリケーションの種類を確認する
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805618"
---
# <a name="candidate-apps-for-cloud-native"></a>クラウド ネイティブの候補アプリ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ポートフォリオ内のアプリを見てください。 そのうちの何人がクラウドネイティブアーキテクチャの資格を得ていますか? 全部ですか。 おそらくいくつか?

コスト/メリット分析を適用すると、クラウド ネイティブに必要な高価な値札がサポートされない可能性が高くなります。 クラウド ネイティブのコストは、アプリケーションのビジネス価値をはるかに上回ります。

クラウド ネイティブの候補となるアプリケーションの種類は何ですか。

- ビジネス機能/機能を絶えず進化させる必要がある、大規模で戦略的なエンタープライズシステム

- 高いリリース速度を必要とするアプリケーション - 高い信頼性を持つ

- システム全体を完全に再展開*することなく*、個々の機能を解放する必要があるシステム

- 異なるテクノロジー・スタックの専門知識を持つチームが開発したアプリケーション

- 個別に拡張する必要があるコンポーネントを持つアプリケーション

その後、レガシーシステムがあります。 新しいアプリケーションを構築したいと考えていますが、多くの場合、ビジネスにとって重要なレガシーワークロードのモダナイゼーションを担当しています。 時間が経つにつれて、従来のアプリケーションはマイクロサービスに分解され、コンテナ化され、最終的にはクラウドネイティブアーキテクチャに「再プラットフォーム化」される可能性があります。

### <a name="modernizing-legacy-apps"></a>レガシーアプリの最新化

Azure[クラウドと Windows コンテナーを使用した既存の .NET アプリケーションの最新化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)の無料の Microsoft 電子書籍では、オンプレミスのワークロードをクラウドに移行するためのガイダンスを提供します。 図 1-10 は、レガシー アプリケーションをモダナイゼーションするための単一の万能戦略がないことを示しています。

![レガシーワークロードの移行戦略](./media/strategies-for-migrating-legacy-workloads.png)

**図 1-10**. レガシーワークロードの移行戦略

重要でないモノリシック アプリは、リフト アンド シフト ([クラウド インフラストラクチャ対応](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) の移行のメリットが大きくなります。 ここでは、オンプレミスのワークロードは変更されずにクラウドベースの VM に再ホストされます。 このアプローチでは[、IaaS (サービスとしてのインフラストラクチャ) モデルを](https://azure.microsoft.com/overview/what-is-iaas/)使用します。 Azure には、このような移行を容易にするための[Azure 移行](https://azure.microsoft.com/services/azure-migrate/)[、Azure サイトの回復](https://azure.microsoft.com/services/site-recovery/) [、Azure データベース移行サービス](https://azure.microsoft.com/campaigns/database-migration/)などのいくつかのツールが含まれています。 この戦略ではコストをいくらか節約できますが、このようなアプリケーションは通常、クラウド コンピューティングのメリットを引き出して活用するように設計されていませんでした。

ビジネスにとって重要なモノリシック アプリは、リフト アンド シフト (*クラウド最適化*) の移行の強化によって恩恵を受けることがよくあります。 このアプローチには、アプリケーションのコア アーキテクチャを変更することなく、主要なクラウド サービスを有効にするデプロイの最適化が含まれます。 たとえば、アプリケーションを[コンテナー化](https://docs.microsoft.com/virtualization/windowscontainers/about/)し、このガイドで後述する[Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/)などのコンテナー オーケストレーターにデプロイできます。 クラウドに入ると、アプリケーションはデータベース、メッセージ キュー、監視、分散キャッシュなどの他のクラウド サービスを使用できます。

最後に、戦略的なエンタープライズ機能を実行するモノリシック アプリは、この書籍の主題である*クラウドネイティブ*アプローチのメリットを最も高くします。 このアプローチは、敏捷性と速度を提供します。 しかし、コードの再プラットフォーム化、再設計、および書き換えが必要になります。

クラウドネイティブのアプローチが適切であると考える場合は、組織で決定を合理化します。 クラウドネイティブアプローチで解決されるビジネス上の問題は何ですか? ビジネス ニーズとどのように連携するのでしょうか。

- 信頼性の高い機能の迅速なリリース?

- きめ細かなスケーラビリティ - リソースのより効率的な使用法

- システムの回復性が向上しましたか?

- システムパフォーマンスの改善

- 操作の可視性を高めますか?

- 開発プラットフォームとデータストアをブレンドして、仕事に最適なツールに到達しますか?

- 将来性に関するアプリケーション投資?

適切な移行戦略は、組織の優先順位と対象とするシステムによって異なります。 多くの場合、モノリシック アプリケーションをクラウド最適化したり、粒度の粗いサービスを N 層アプリに追加したりする方がコスト効率が高い場合があります。 このような場合でも、Azure App Service が提供するクラウド PaaS 機能のような機能を最大限に活用できます。

## <a name="summary"></a>まとめ

この章では、クラウドネイティブコンピューティングについて紹介しました。 クラウド ネイティブ アプリケーションを駆動する主要な機能と共に定義を提供しました。 この投資と労力を正当化するアプリケーションの種類を見ました。

この後の導入で、クラウドネイティブについてより詳細に説明します。

### <a name="references"></a>References

- [クラウド ネイティブ コンピューティングの基礎](https://www.cncf.io/)

- [.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Azure クラウドと Windows コンテナーを使用して既存の .NET アプリケーションを最新化する](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [コーネリア・デイビスによるクラウドネイティブパターン](https://www.manning.com/books/cloud-native-patterns)

- [12要素アプリケーションを超えて](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [コードとしてのインフラストラクチャとは](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Uber エンジニアリングのマイクロデプロイ:自信を持って毎日展開](https://eng.uber.com/micro-deploy/)

- [ネットフリックスがコードを展開する方法](https://www.infoq.com/news/2013/06/netflix/)

- [WeChat マイクロサービスのスケーリングの過負荷制御](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[前へ](definition.md)
>[次へ](introduce-eshoponcontainers-reference-app.md)

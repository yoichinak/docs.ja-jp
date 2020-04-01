---
title: サービス メッシュ通信インフラストラクチャ
description: サービス メッシュ テクノロジがクラウドネイティブマイクロサービス通信を効率化する方法を学習する
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 6b177ef33b804ec35f3acb919539a97683e5a487
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523520"
---
# <a name="service-mesh-communication-infrastructure"></a>サービス メッシュ通信インフラストラクチャ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

この章では、マイクロサービス通信の課題について説明しました。 開発チームは、バックエンド サービスが相互に通信する方法に注意を向ける必要があると述べています。 理想的には、サービス間通信が少ないほど、より良い方法です。 ただし、バックエンド サービスは、多くの場合、操作を完了するために互いに依存しているので、回避は常に可能ではありません。

同期 HTTP 通信と非同期メッセージングを実装するためのさまざまなアプローチを検討しました。 いずれの場合も、開発者は通信コードの実装に負担をかかえています。 通信コードは複雑で時間がかかります。 誤った決定は、パフォーマンス上の重大な問題を引き起こす可能性があります。

マイクロサービス通信に対するより現代的なアプローチは、*サービスメッシュ*と題された新しく急速に進化する技術を中心にしています。 [サービス メッシュ](https://www.nginx.com/blog/what-is-a-service-mesh/)は、サービス間の通信、復元性、および多くの横断的な懸念事項を処理する組み込み機能を備えた構成可能なインフラストラクチャ 層です。 これらの懸念事項に対する責任をマイクロサービスからサービス メッシュ層に移動します。 通信は、マイクロサービスから分離されます。

サービス メッシュの重要なコンポーネントはプロキシです。 クラウド ネイティブ アプリケーションでは、プロキシのインスタンスは通常、各マイクロサービスと共に配置されます。 これらは別々のプロセスで実行されますが、2 つは密接にリンクされており、同じライフサイクルを共有します。 このパターンは[、Sidecar パターン](https://docs.microsoft.com/azure/architecture/patterns/sidecar)と呼ばれ、図 4-24 に示されています。

![サイドカーを使用したサービスメッシュ](./media/service-mesh-with-side-car.png)

**図 4-24** サイドカーを使用したサービスメッシュ

前の図では、各マイクロサービスと一緒に実行されるプロキシによってメッセージが傍受される方法に注意してください。 各プロキシは、マイクロサービスに固有のトラフィック ルールで構成できます。 メッセージを理解し、サービスや外部にルーティングできます。

サービス間通信の管理に加えて、サービス・メッシュはサービス検出と負荷分散をサポートします。

設定すると、サービス メッシュは高機能になります。 メッシュは、サービス検索エンドポイントから対応するインスタンスプールを取得します。 要求を特定のサービス インスタンスに送信し、結果の待機時間と応答の種類を記録します。 最近の要求に対して観察された待機時間など、さまざまな要因に基づいて高速応答を返す可能性が最も高いインスタンスを選択します。

サービス メッシュは、トラフィック、通信、およびネットワークの問題をアプリケーション レベルで管理します。 メッセージと要求を理解します。 通常、サービス メッシュはコンテナー オーケストレーターと統合されます。 Kubernetes は、サービス メッシュを追加できる拡張可能なアーキテクチャをサポートしています。

第 6 章では、アーキテクチャと利用可能なオープン ソース実装に関する議論を含む、Service Mesh テクノロジについて詳しく説明します。

## <a name="summary"></a>まとめ

この章では、クラウドネイティブの通信パターンについて説明しました。 まず、フロントエンド クライアントがバックエンド マイクロサービスと通信する方法を調べることから始めました。 その過程で、APIゲートウェイプラットフォームとリアルタイムコミュニケーションについて話しました。 次に、マイクロサービスが他のバックエンド サービスと通信する方法を確認しました。 ここでは、同期 HTTP 通信と非同期メッセージングの両方を複数のサービスで見ました。 クラウドネイティブの世界で今後の技術であるgRPCを取り上げました。 最後に、マイクロサービス通信を合理化できる「Service Mesh」という新しい急速に進化する技術を導入しました。

クラウド ネイティブ システムでの通信の実装に役立つマネージド Azure サービスに特に重点を置いています。

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)
- [Azure Storage キュー](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Hub](https://azure.microsoft.com/services/event-hubs/)

次に、クラウドネイティブシステムで分散データを導入し、そのメリットと課題を抱えています。

### <a name="references"></a>References

- [.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [マイクロサービスのサービス間通信の設計](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR サービスは、リアルタイム機能を追加する完全に管理されたサービスです。](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Azure API ゲートウェイイングレス コントローラー](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Azure Kubernetes サービス (AKS) での入力について](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [gRPC ドキュメント](https://grpc.io/docs/guides/)

- [WCF 開発者向け gRPC](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [gRPC サービスと HTTP API の比較](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [NET ビデオを使用した gRPC サービスの構築](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[前次](grpc.md)
>[Next](Database-per-microservice.md)

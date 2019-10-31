---
title: サーバーレス設計の例-サーバーレスアプリ
description: サーバーレスアーキテクチャでサポートされるさまざまなシナリオについて説明します。スケジュール設定やイベントベースの処理からファイルトリガーやストリームプロセスまでを対象としています。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093555"
---
# <a name="serverless-design-examples"></a>サーバーレス設計の例

サーバーレス用に存在する設計パターンは多数あります。 このセクションでは、サーバーレスを使用する一般的なシナリオをいくつか紹介します。 すべての例で共通しているのは、イベントトリガーとビジネスロジックの基本的な組み合わせです。

## <a name="scheduling"></a>上

タスクのスケジュール設定は、共通の機能です。 次の図は、適切な整合性チェックが行われていないレガシデータベースを示しています。 データベースは定期的にスキャンされされている必要があります。 サーバーレス関数は、無効なデータを検索して消去します。 トリガーは、スケジュールに基づいてコードを実行するタイマーです。

![サーバーレススケジューリング](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>コマンドクエリ責務分離 (CQRS)

コマンドクエリ責務分離 (CQRS) は、データの読み取り (またはクエリ) とデータを変更する操作のためのさまざまなインターフェイスを提供するパターンです。 いくつかの一般的な問題に対処します。 従来の Create Read Update Delete (CRUD) ベースのシステムでは、同じデータストアに対する読み取りと書き込みの両方の大容量から競合が発生する可能性があります。 ロックが頻繁に発生し、読み取り速度が大幅に低下することがあります。 多くの場合、データは複数のドメインオブジェクトの複合として表示され、読み取り操作では異なるエンティティのデータを結合する必要があります。

CQRS を使用する場合、読み取りには、使用方法によってデータをモデル化する特別な "フラット化" エンティティが含まれる場合があります。 読み取りは、格納方法とは異なる方法で処理されます。 たとえば、データベースでは、連絡先を子アドレスレコードを含むヘッダーレコードとして格納することができますが、読み取りには、ヘッダーと住所の両方のプロパティを持つエンティティが含まれる可能性があります。 読み取りモデルを作成する方法は多数あります。 ビューから具体化されている可能性があります。 更新操作は、2つの異なるモデルに対する更新をトリガーする分離イベントとしてカプセル化できます。 読み取りと書き込みのための個別のモデルが存在します。

![CQRS の例](./media/cqrs-example.png)

サーバーレスでは、分離されたエンドポイントを提供することにより、CQRS パターンに対応できます。 1つのサーバーレス関数がクエリまたは読み取りに対応し、別のサーバーレス関数または関数のセットによって更新操作が処理されます。 サーバーレス関数は、読み取りモデルを最新の状態に保つ役割を担い、データベースの[変更フィード](https://docs.microsoft.com/azure/cosmos-db/change-feed)によってトリガーすることもできます。 フロントエンド開発は、必要なエンドポイントに接続するために簡略化されています。 イベントの処理はバックエンドで処理されます。 このモデルは、さまざまなチームがさまざまな操作を実行する可能性があるため、大規模なプロジェクトにも適しています。

## <a name="event-based-processing"></a>イベントベースの処理

メッセージベースのシステムでは、多くの場合、イベントはキューまたはパブリッシャー/サブスクライバーのトピックで収集されます。 これらのイベントは、サーバーレス関数をトリガーしてビジネスロジックを実行することができます。 イベントベースの処理の例としては、イベントソースシステムがあります。 "イベント" は、タスクを完了としてマークするために発生します。 イベントによってトリガーされたサーバーレス関数は、適切なデータベースドキュメントを更新します。 2番目のサーバーレス関数では、イベントを使用してシステムの読み取りモデルを更新できます。 [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)には、イベントをサブスクライバーとして関数と統合する方法が用意されています。

> イベントは情報メッセージです。 詳細については、「[イベントソーシングパターン](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)」を参照してください。

## <a name="file-triggers-and-transformations"></a>ファイルトリガーと変換

抽出、変換、読み込み (ETL) は、一般的なビジネス機能です。 サーバーレスは、パイプラインの一部としてコードをトリガーできるため、ETL のための優れたソリューションです。 個々のコードコンポーネントは、さまざまな側面に対応できます。 1つのサーバーレス関数は、ファイルをダウンロードし、別の関数によって変換が適用され、別の関数によってデータが読み込まれます。 コードを個別にテストしてデプロイできるため、必要に応じて簡単に保守し、スケーリングすることができます。

![サーバーレスファイルのトリガーと変換](./media/serverless-file-triggers.png)

図では、"クールストレージ" は[Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics)で解析されるデータを提供します。 データストリームで発生した問題が発生すると、異常に対処する Azure 関数がトリガーされます。

## <a name="asynchronous-background-processing-and-messaging"></a>非同期のバックグラウンド処理とメッセージング

非同期メッセージングおよびバックグラウンド処理を使用すると、アプリケーションは待機しなくてもプロセスを開始できます。 非同期処理の例としては、OCR アプリがあります。 画像が送信され、処理のためにキューに入れられます。 テキストを抽出するためにイメージをスキャンすると時間がかかる場合があり、完了すると通知が送信されます。 サーバーレスは、このシナリオの呼び出しと結果の両方を処理できます。

## <a name="web-apps-and-apis"></a>Web アプリと Api

サーバーレスの一般的なシナリオは N 層アプリケーションであり、最も一般的なのは UI レイヤーが web アプリである場合です。 シングルページアプリケーション (SPA) が広く普及しています。 SPA アプリは1ページをレンダリングし、API 呼び出しと返されたデータに依存して、ページ全体を再読み込みせずに新しい UI を動的に表示します。 クライアント側のレンダリングでは、エンドユーザーにより高速で応答性の高いアプリケーションが提供されます。

HTTP 呼び出しによってトリガーされるサーバーレスエンドポイントは、API 要求を処理するために使用できます。 たとえば、ad サービス会社は、ユーザープロファイル情報を持つサーバーレス関数を呼び出して、カスタム広告を要求する場合があります。 サーバーレス関数はカスタム広告を返し、web ページはそれをレンダリングします。

![サーバーレス web API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>データパイプライン

サーバーレス関数は、データパイプラインを容易にするために使用できます。 この例では、ファイルによって関数がトリガーされ、CSV ファイルのデータがテーブルのデータ行に変換されます。 整理されたテーブルにより、Power BI ダッシュボードはエンドユーザーに分析を提示できます。

![サーバーレスデータパイプライン](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>ストリーム処理

デバイスとセンサーでは、多くの場合、リアルタイムで処理する必要があるデータのストリームが生成されます。 [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)からメッセージやストリームをキャプチャしたり、 [Service Bus](https://docs.microsoft.com/azure/service-bus)に[IoT Hub](https://docs.microsoft.com/azure/iot-hub)たりできるさまざまなテクノロジがあります。 サーバーレスは、トランスポートに関係なく、メッセージとデータストリームを処理するための最適なメカニズムです。 サーバーレスは、大量のデータの需要に合わせて迅速に拡張できます。 サーバーレスコードでは、ビジネスロジックを適用してデータを解析し、アクションと分析のために構造化された形式で出力することができます。

![サーバーレスストリーム処理](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API ゲートウェイ

API ゲートウェイは、クライアントに対して単一のエントリポイントを提供し、要求をバックエンドサービスにインテリジェントにルーティングします。 大規模なサービスのセットを管理する場合に便利です。 また、クライアントをさまざまな環境に簡単に接続することで、バージョン管理を処理し、開発を簡素化することもできます。 サーバーレスでは、個々のマイクロサービスのバックエンドスケーリングを処理しながら、API ゲートウェイを介して1つのフロントエンドを提供できます。

![サーバーレス API ゲートウェイ](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>推奨されるリソース

- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [分散データ管理に関する課題とソリューション](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [マイクロサービスの設計: マイクロサービス境界の識別](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [イベントソーシングパターン](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [直流高速度遮断器パターンの実装](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Service Bus](https://docs.microsoft.com/azure/service-bus)
- [Azure Cosmos DB での change feed サポートの使用](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[前へ](serverless-architecture-considerations.md)
>[次へ](azure-serverless-platform.md)

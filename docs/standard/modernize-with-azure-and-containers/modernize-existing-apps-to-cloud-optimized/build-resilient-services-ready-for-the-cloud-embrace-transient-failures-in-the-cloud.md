---
title: 回復力のあるサービス、クラウドの準備をビルドします。 クラウド内の一時的な障害を受け入れる
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |回復力のあるサービス、クラウドの準備をビルドします。 クラウド内の一時的な障害を受け入れる
ms.date: 04/30/2018
ms.openlocfilehash: ca5d5e0c3af772ac52a02894c96889c776cf7d48
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643736"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>クラウドの準備が整っている回復力のあるサービスの構築:クラウド内の一時的な障害を受け入れる

回復性は、障害から回復し、引き続き機能する能力です。 回復性は、障害を回避、障害が発生するという事実を受け入れてがそれに応答するダウンタイムやデータの損失を回避する方法でについてではありません。 回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。

アプリケーションは、回復性のソフトウェア ベースのモデルではなく、ハードウェアに基づくモデルを実装するには、少なくとも場合は、クラウドの準備が。 クラウド アプリケーションでは、確かに発生する部分的な障害を受け入れる必要があります。 デザインまたは部分的に予想される部分的な障害に回復性を実現するために、アプリケーションをリファクターします。 一時的なネットワーク障害、ノード、または Vm のクラウドでのクラッシュなどの部分的な障害に対処するために設計する必要があります。 偶数のコンテナー オーケストレーター クラスタ内の別のノードに移動するには、アプリケーション内での断続的な短いエラー可能性があります。

## <a name="handling-partial-failure"></a>部分的なエラーの処理

クラウド ベースのアプリケーションでは、常につきまとう部分的な障害のリスクがあります。 たとえば、1 つの web サイト インスタンスまたはコンテナーが失敗する、または利用できない、または短時間応答しない場合があります。 または、1 つの VM またはサーバーがクラッシュする可能性があります。

クライアントとサービスは個別のプロセスであるため、サービス可能性があります、クライアントの要求にタイムリーに応答することができません。 サービスがオーバー ロードされたされ、要求に応答が遅くまたは必要はありません、短い時間でアクセス可能なネットワークの問題により。

たとえば、Azure SQL Database のデータベースにアクセスするモノリシック .NET アプリケーションを検討してください。 Azure SQL データベースまたはその他のサード パーティのサービスがについて簡単に応答していない場合 (Azure SQL データベースを別のノードやサーバーに移動される可能性および数秒応答できません) は、時間、アプリケーションがクラッシュする場合、ユーザーが任意のアクションを実行しようとすると、および表示w 同じ時間に例外を発生します。

同様のシナリオには、HTTP サービスを使用するアプリで発生する可能性があります。 ネットワークまたはサービス自体できない可能性があります、クラウドで、短い一時的な障害の発生時にします。

図 4-9 に示すような回復力のあるアプリケーションでは、アプリケーションのリソースの一時的なエラーを処理する機会を提供する「指数関数的バックオフによる再試行」などの手法を実装する必要があります。 また、「サーキット ブレーカー」をアプリケーションで使用することも必要があります。 サーキット ブレーカーは、実際に長期的な障害の場合、リソースにアクセスしようとしてからアプリケーションを停止します。 サーキット ブレーカーを使用すると、アプリケーションを富んだ自体をサービス拒否攻撃を回避できます。

![指数関数的バックオフによる再試行によって処理される部分的な障害](./media/image9.png)

> **図 4-9 です。** 指数関数的バックオフによる再試行によって処理される部分的な障害

HTTP リソースとデータベース リソースの両方に、これらの手法を使用できます。 図 4-9 では、アプリケーションはこれらの手法は、サービス レベル (HTTP) とデータ層 (TCP) を作成する必要があるため、3 層アーキテクチャに基づきます。 (その他のサービスまたはマイクロ サービス) のデータベースだけでなく、1 つのアプリ レベルのみを使用してモノリシック アプリケーションをデータベースの接続レベルで一時的な障害を処理する可能性があります十分。 このシナリオでは、特定のデータベース接続の構成だけが必要です。

回復力のある通信を使用している .NET のバージョンに応じて、データベースへのアクセスを実装するときに簡単なできます (たとえば、 [Entity Framework 6 以降](/ef/ef6/fundamentals/connection-resiliency/retry-logic)します。 データベース接続を構成するだけで済みます)。 またはなどの他のライブラリを使用する必要があります、 [Transient Fault Handling Application Block](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (以前のバージョンの .NET)、独自のライブラリを実装します。

使用する .NET の推奨事項は、HTTP の再試行、サーキット ブレーカーを実装する場合、 [Polly](https://github.com/App-vNext/Polly)ライブラリで、.NET Framework 4.0、.NET Framework 4.5、および .NET Core のサポートを含む .NET Standard 1.1 を対象とします。

クラウドでの部分的な障害を処理するための戦略を実装する方法については、次の参照を参照してください。

### <a name="additional-resources"></a>その他の技術情報

- **部分的なエラーを処理するために回復力のある通信を実装します。**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework 接続の回復性と再試行ロジック (バージョン 6 以降)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Transient Fault Handling Application Block**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **回復力のある HTTP 通信 Polly ライブラリ**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[次へ](modernize-your-apps-with-monitoring-and-telemetry.md)

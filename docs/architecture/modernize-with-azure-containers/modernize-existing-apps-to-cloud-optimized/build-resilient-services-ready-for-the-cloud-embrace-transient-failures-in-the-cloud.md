---
title: クラウドのための回復力のあるサービスを構築できます。 クラウド内の一時的な障害を受け入れる
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |クラウドのための回復力のあるサービスを構築できます。 クラウド内の一時的な障害を受け入れる
ms.date: 04/30/2018
ms.openlocfilehash: 5f44029a214cf1f366fc787e27a9ac34599c4dca
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373970"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>クラウドの準備が整っている回復力のあるサービスの構築:クラウド内の一時的な障害を受け入れる

回復性は、障害から回復し、引き続き機能する能力です。 回復性は、障害を回避することではなく、障害が発生したという事実を受け入れ、ダウンタイムやデータ損失を回避する方法でそれらに応答します。 回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。

アプリケーションは、ハードウェアベースのモデルではなく、回復性のソフトウェアベースのモデルを実装する必要がある場合に、クラウドの準備ができています。 クラウドアプリケーションは、確実に発生する部分的な障害を受け入れる必要があります。 アプリケーションを設計または部分的にリファクタリングして、予想される部分的な障害による回復性を実現します。 これは、一時的なネットワークの停止やノード、クラウドでクラッシュした Vm など、部分的な障害に対処するように設計されている必要があります。 コンテナーが orchestrator クラスター内の別のノードに移動されても、アプリケーション内で断続的にエラーが発生する可能性があります。

## <a name="handling-partial-failure"></a>部分的なエラーの処理

クラウドベースのアプリケーションでは、部分的な障害のリスクが発生しています。 たとえば、1つの web サイトインスタンスまたはコンテナーが失敗したり、短時間に利用できなくなったり、応答しなくなったりする可能性があります。 または、単一の VM またはサーバーがクラッシュする可能性があります。

クライアントとサービスは別のプロセスであるため、サービスはクライアントの要求に適時に応答できない可能性があります。 サービスが過負荷になり、要求に対して応答が遅くなったり、ネットワークの問題のために短時間アクセスできなくなったりする可能性があります。

たとえば、Azure SQL Database のデータベースにアクセスするモノリシック .NET アプリケーションについて考えてみます。 Azure SQL database またはその他のサードパーティのサービスが短時間応答しない場合 (Azure SQL データベースが別のノードまたはサーバーに移動され、数秒間応答しなくなる場合があります)、ユーザーが何らかの操作を実行しようとすると、アプリケーションがクラッシュし、表示 (される可能性があります。同時に例外が発生します。

同様のシナリオは、HTTP サービスを使用するアプリで発生する可能性があります。 短時間で一時的な障害が発生しても、ネットワークまたはサービス自体がクラウドで利用できない可能性があります。

図4-9 に示されているような弾力性のあるアプリケーションでは、リソースの一時的な障害をアプリケーションが処理できるようにするための "指数バックオフによる再試行" などの手法を実装する必要があります。 また、アプリケーションで "サーキットブレーカー" を使用する必要があります。 サーキットブレーカーは、アプリケーションが実際に長期間の障害である場合に、リソースにアクセスしようとするのを停止します。 サーキットブレーカーを使用することにより、アプリケーションはサービス拒否攻撃を provoking ことを回避します。

![指数バックオフによる再試行によって処理される部分的なエラー](./media/image9.png)

**図 4-9.** 指数バックオフによる再試行によって処理される部分的なエラー

これらの手法は、HTTP リソースとデータベースリソースの両方で使用できます。 図4-9 では、アプリケーションは3層アーキテクチャに基づいているため、サービスレベル (HTTP) およびデータ層レベル (TCP) でこれらの手法が必要になります。 データベースに加えて1つのアプリ層のみを使用するモノリシックアプリケーション (追加のサービスやマイクロサービスがない場合) では、データベース接続レベルでの一時的なエラーの処理が十分である可能性があります。 このシナリオでは、データベース接続の特定の構成のみが必要です。

データベースにアクセスする回復力のある通信を実装する場合、使用している .NET のバージョンによっては、(たとえば、 [Entity Framework 6](/ef/ef6/fundamentals/connection-resiliency/retry-logic)以降を含む) 簡単にすることができます。 これは、データベース接続を構成するだけの問題です)。 または、[一時的なエラー処理アプリケーションブロック](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50))(以前のバージョンの .net の場合) などの追加のライブラリを使用したり、独自のライブラリを実装したりする必要がある場合もあります。

HTTP 再試行とサーキットブレーカーを実装する場合は、.NET の推奨事項として、.NET Framework 4.0、.NET Framework 4.5、.NET Standard 1.1 (.NET Core サポートを含む) を対象と[する、このライブラリを](https://github.com/App-vNext/Polly)使用することをお勧めします。

クラウドで部分的なエラーを処理するための戦略を実装する方法については、次の参照情報を参照してください。

### <a name="additional-resources"></a>その他の技術情報

- **部分的なエラーを処理するための回復力のある通信の実装**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **接続の回復性と再試行ロジックの Entity Framework (バージョン6以降)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **一時的エラー処理アプリケーションブロック**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **回復性の高い HTTP 通信のためのライブラリ**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[次へ](modernize-your-apps-with-monitoring-and-telemetry.md)

---
title: WS-* プロトコル-WCF 開発者向け gRPC
description: WCF でサポートされている WS-* プロトコルと gRPC で使用可能な代替方法の確認
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4e7b80df182fb69cc51e14738e59ad87efaf5dd2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "73841313"
---
# <a name="ws--protocols"></a>WS-MANAGEMENT プロトコル\*

Windows Communication Foundation (WCF) を使用する利点の1つは、既存の_WS\*_ 標準プロトコルの多くをサポートすることでした。 このセクションでは、gRPC で同じ\* WS-MANAGEMENT プロトコルを管理する方法と、代替手段がない場合に使用できるオプションについて説明します。

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a>メタデータの交換-WS-POLICY、WS-POLICY など

SOAP サービスでは、Web サービス記述言語 (WSDL) スキーマドキュメントが、データ形式、操作、通信オプションなどの情報と共に公開されます。 このスキーマを使用して、クライアントコードを生成できます。

gRPC は、サーバーとクライアントが同じ `.proto` ファイルから生成された場合に最適に機能しますが、サーバーリフレクションのオプションの拡張機能を使用すると、実行中のサーバーから動的な情報を公開することができます。 詳細については、「 [grpc. リフレクション](https://nuget.org/packages/Grpc.Reflection)NuGet パッケージ」と「 [grpc C#サーバーリフレクション](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md)」を参照してください。

WS-MANAGEMENT プロトコルは、ローカルネットワーク上のサービスを検索するために使用されます。 gRPC サービスは、通常、DNS または Consul や飼育係などのサービスレジストリを使用して配置されます。

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a>セキュリティ-WS-SECURITY、WS-FEDERATION、XML 暗号化などの機能

セキュリティ、認証、および承認の詳細については、[第6章](security.md)を参照してください。 ただし、WCF とは異なり、gRPC は WS-SECURITY、WS フェデレーション、または XML 暗号化をサポートしていません。 それでも、gRPC は優れたセキュリティを提供しています。すべての gRPC ネットワークトラフィックは、HTTP/2 over TLS を使用するときに自動的に暗号化され、X509 証明書は相互クライアント/サーバー認証に使用される場合があります。

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC では、ws-reliablemessaging に相当するものは提供されません。 再試行のセマンティクスは、コードで処理する必要があります[。たとえば](https://github.com/App-vNext/Polly)、通常のようなライブラリを使用します。 Kubernetes または同様のオーケストレーション環境で実行されている場合、[サービスメッシュ](service-mesh.md)はサービス間の信頼性の高いメッセージングを提供するのにも役立ちます。

## <a name="ws-transaction-ws-coordination"></a>WS-ATOMICTRANSACTION、WS-ATOMICTRANSACTION

WCF による分散トランザクションの実装では、Windows の Microsoft 分散トランザクションコーディネーターまたは MSDTC を使用します。 これは、SQL Server、MSMQ、Windows ファイルシステムなど、特にサポートされているリソースマネージャーと連携します。 最新のマイクロサービスの世界では、使用されているテクノロジの範囲が広いため、それと同等の機能はありません。 トランザクションの詳細については、「[付録 a](appendix.md)」を参照してください。

>[!div class="step-by-step"]
>[前へ](error-handling.md)
>[次へ](migrate-wcf-to-grpc.md)

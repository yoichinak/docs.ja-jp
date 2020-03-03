---
title: GRPC アプリケーションのセキュリティ-WCF 開発者向け gRPC
description: GRPC での呼び出しとチャネルの認証および承認の概要。
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503408"
---
# <a name="security-in-grpc-applications"></a>gRPC アプリケーションのセキュリティ

実際のシナリオでは、アプリケーションとサービスのセキュリティ保護が不可欠です。 セキュリティには3つの主要領域があります。 

* ネットワークトラフィックを暗号化して、悪意のあるハッカーによって傍受されるのを防ぎます。
* クライアントとサーバーを認証して、id と信頼を確立します。
* クライアントがシステムへのアクセスを制御し、id に基づいてアクセス許可を適用することを承認します。

> [!NOTE]
> *認証*は、クライアントまたはサーバーの id を確立することに関係します。 *承認*は、クライアントがリソースにアクセスするためのアクセス許可を持っているか、コマンドを発行するかを判断することに関係します。

この章では、ASP.NET Core 用の gRPC での認証と承認の機能について説明します。 また、TLS で暗号化された接続を使用したネットワークセキュリティについても説明します。

## <a name="wcf-authentication-and-authorization"></a>WCF の認証と承認

Windows Communication Foundation (WCF) では、認証と承認は、使用されているトランスポートとバインドに応じて、さまざまな方法で処理されていました。 WCF では、さまざまな WS\* セキュリティ標準がサポートされています。 また、windows システム間で IIS または NetTCP サービスで実行されている HTTP サービスの Windows 認証もサポートされています。

## <a name="grpc-authentication-and-authorization"></a>gRPC の認証と承認

gRPC の認証と承認は、次の2つのレベルで機能します。

* 呼び出しレベルの認証/承認は、通常、呼び出しが行われたときにメタデータに適用されるトークンを使用して処理されます。 
* チャネルレベルの認証では、接続レベルで適用されるクライアント証明書を使用します。 また、チャネルのすべての呼び出しに自動的に適用される、呼び出しレベルの認証/承認の資格情報を含めることもできます。 

これらのメカニズムのいずれかまたは両方を使用して、サービスをセキュリティで保護することができます。

GRPC の ASP.NET Core 実装では、ほとんどの標準的な ASP.NET Core メカニズムによる認証と承認をサポートしています。

- 認証の呼び出し
  - Azure Active Directory
  - IdentityServer
  - JWT ベアラートークン
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- チャネル認証
  - クライアント認証

呼び出しの認証方法はすべて、*トークン*に基づいています。 実際の違いは、トークンが生成される方法と、ASP.NET Core サービスでトークンを検証するために使用されるライブラリです。

詳細については、[認証と承認](/aspnet/core/grpc/authn-and-authz)に関する記事を参照してください。

> [!NOTE]
> TLS で暗号化された HTTP/2 接続で gRPC を使用している場合は、チャネルレベルの認証を使用しない場合でも、クライアントとサーバー間のすべてのトラフィックが暗号化されます。

この章では、gRPC サービスに呼び出し資格情報とチャネル資格情報を適用する方法について説明します。 また、.NET Core gRPC クライアントの資格情報を使用してサービスで認証する方法についても説明します。

>[!div class="step-by-step"]
>[前へ](client-libraries.md)
>[次へ](call-credentials.md)

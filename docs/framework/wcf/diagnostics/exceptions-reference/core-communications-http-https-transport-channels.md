---
title: 'コア通信: HTTP、HTTPS トランスポート チャネル'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 4c4a2537ae615943ffac299a8c8cd00c67094360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998752"
---
# <a name="core-communications-httphttps-transport-channels"></a>コア通信: HTTP/HTTPS トランスポート チャネル
このトピックでは、Windows Communication Foundation (WCF) の HTTP または HTTPS トランスポート チャネルによって生成されるすべての例外を使用します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|指定された偽装レベルが指定されました。 明示的な資格情報を使用する場合に 'Impersonation' レベルをサポートできるのは、HTTP ダイジェスト認証のみです。|  
|FramingContentTypeMismatch|指定されたコンテンツの種類は、指定されたサービスでサポートされていませんでした。 クライアントとサービスのバインディングは一致しない場合もあります。|  
|Hosting_SslSettingsMisconfigured|指定されたサービスの SSL (Secure Sockets Layer) 設定が、インターネット インフォメーション サービスの SSL 設定と一致しません。|  
|HttpAuthSchemeAndClientCert|HTTPS リスナー ファクトリが、クライアント証明書と指定された認証方式を要求するように構成されています。 ただし、クライアント認証の方式は、一度に 1 種類しか要求できません。|  
|HttpReceiveFailure|指定された対象への HTTP 応答の受信中にエラーが発生しました。 サービス エンドポイント バインディングが HTTP プロトコルを使用していない可能性があります。 サービスがシャットダウンしたため、HTTP 要求コンテキストがサーバーによって中止された可能性もあります。 詳細については、サーバー ログを参照してください。|  
|HttpRegistrationAccessDenied|HTTP は指定された URL を登録できません。 プロセスには、この名前空間へのアクセス権はありません (を参照してください[Namespace の予約、登録、およびルーティング](/windows/desktop/http/namespace-reservations-registrations-and-routing)詳細については)。|  
|HttpRegistrationAlreadyExists|HTTP は指定された URL を登録できません。 別のアプリケーションが既にこの URL を HTTP.SYS に登録しています。|  
|HttpRegistrationPortInUse|HTTP が指定された URL を登録できませんでした。指定された TCP ポートは別のアプリケーションが使用しています。|  
|HttpSendFailure|指定された対象への HTTP 要求の発行中にエラーが発生しました。 この原因がセキュリティ バインディングの不一致ではないことを確認してください。 また、サービスが SSL (Secure Sockets Layer) 用に構成されていないことも確認してください。|  
|MessageXmlProtocolError|ネットワークから受信した XML に問題があります。 詳細については、内部例外を参照してください。|  
|MissingContentType|受信側は、指定された対象への要求でコンテンツの種類が指定されていないことを示すエラーを返しました。 詳細については、内部例外を参照してください。|  
|ProxyAuthenticationLevelMismatch|HTTP プロキシ認証の資格情報で、ターゲット サーバーの認証要件より厳しい要件である相互認証が指定されています。|  
|ProxyImpersonationLevelMismatch|HTTP プロキシ認証の資格情報で、ターゲット サーバーの認証制限より厳しい制限である偽装レベルの制限が指定されています。|  
|SecureChannelFailure|指定された証明機関との間で、SSL/TLS のセキュリティで保護されたチャネルを確立できませんでした。|  
|TrustFailure|指定された証明機関との間の SSL/TLS のセキュリティで保護されたチャネルで、信頼関係を確立できません。|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|HttpTransportBinding 要素では、明示的なプロキシ アドレスだけでなく、UseDefaultWebProxy=true も指定できません。|

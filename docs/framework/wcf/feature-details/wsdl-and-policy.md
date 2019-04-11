---
title: WSDL とポリシー
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: caaa54f04bbb10ed3b3dd65b53ace633b88f9126
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151906"
---
# <a name="wsdl-and-policy"></a>WSDL とポリシー
このトピックでは、Windows Communication Foundation (WCF) の WSDL 1.1、Ws-policy と Ws-policyattachment の実装の詳細だけでなく追加の Ws-policy アサーションおよび WCF で導入された WSDL 1.1 拡張について説明します。  
  
 WCF では、制約と明確にするこのドキュメントで説明されている W3C に提出された Ws-policy と Ws-policyattachment 仕様を実装します。  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|------------|---------------|  
|wsp (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|wsp (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WCF WSDL1.1 の拡張  
 WCF では、次の WSDL1.1 拡張機能を使用して、コントラクト セッションの要件について説明します。  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:boolean は、この操作が WCF セッションを開始することを示します既定値は`false`します。  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:boolean は、この操作には、WCF セッションが終了したことを示します既定値は`false`します。  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:boolean は、このコントラクトでセッションを確立する必要があるかどうかを示します。  
  
### <a name="soap-1x-http-binding-transport-uris"></a>SOAP 1.x HTTP バインディング トランスポートの URI  
 WCF では、次の Uri を使用して、WSDL 1.1、SOAP 1.1 および SOAP 1.2 のバインディング拡張機能の要素に使用するトランスポートを示します。  
  
|Transport|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|名前付きパイプ|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>WCF で実装されるポリシー アサーション  
 Web サービスの仕様で導入されたポリシー アサーションに加えて (ws-*) し、このドキュメントの他のセクションで説明したように、WCF は次のポリシー アサーションを実装します。  
  
|ポリシー アサーション|ポリシー サブジェクト|説明|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|エンドポイント|エンドポイントは、HTTP 基本認証を使用します。|  
|http:HttpDigestAuthentication|エンドポイント|エンドポイントは、HTTP ダイジェスト認証を使用します。|  
|http:HttpNegotiateAuthentication|エンドポイント|エンドポイントは、HTTP ネゴシエート認証を使用します。|  
|http:HttpNtlmAuthentication|エンドポイント|エンドポイントは、HTTP NTLM 認証を使用します。|  
|msf:Streamed|エンドポイント|エンドポイントは、ストリーミングされたメッセージ フレームを使用します。 このアサーションは、TCP、名前付きパイプのようなトランスポートに提供されるメッセージ フレーム プロトコルと共に使用されます。|  
|msf:SslTransportSecurity|エンドポイント|エンドポイントは、トランスポート層セキュリティ (TLS) をメッセージ フレームと共に使用します。|  
|msf:WindowsTransportSecurity|エンドポイント|エンドポイントは、Security Provider Negotiation (SPNEGO) をメッセージ フレームと共に使用します。|  
|msmq:MsmqBestEffort|エンドポイント|MSMQ はベストエフォート保証を使用します。|  
|msmq:MsmqSession|エンドポイント|MSMQ はセッション保証を使用します。|  
|msmq:MsmqVolatile|エンドポイント|MSMQ は揮発性です。|  
|msmq:Authenticated|エンドポイント|認証が、MSMQ トランスポートと共に使用されます。|  
|msmq:WindowsDomain|エンドポイント|MSMQ は Windows ドメイン認証を使用します。|  
|cdp:CompositeDuplex|エンドポイント|エンドポイントは、メッセージの送受信に 2 つの個別の逆方向トランスポート接続を使用します。|  
|mssp:RsaToken|入れ子|RSA キー トークンのアサーションです。 通常、この要件を満たすのは、保証する署名内でキー情報の一部として直接シリアル化される RSA キーです。|  
|mssp:SslContextToken|入れ子|WS-Trust を使用するバイナリ TLS ハンドシェイクによって取得される SecurityContextToken の使用を要求します。 入れ子になったアサーションには、sp:RequireDerivedKeys、mssp:MustNotSendCancel、mssp:RequireClientCertificate があります。|  
|mssp:MustNotSendCancel|入れ子|Cancel バインディング [WS-Trust、WS-SC] を使用するセキュリティ トークン要求 (RST) の要求メッセージ [WS-Trust] を特定の SecurityContextToken の発行者に送信しないという要件を指定します。 このアサーションが存在する場合、このような要求メッセージを発行者に送信することはできません。 このアサーションが存在しない場合、このような要求メッセージを発行者に送信できます。|  
|mssp:RequireClientCertificate|入れ子|このオプション要素では、TLSNEGO プロトコルの一部としてクライアント証明書を提供するという要件を指定します。 このアサーションが存在する場合、クライアント証明書を提供する必要があります。 このアサーションが存在しない場合、クライアント証明書を提供しないでください。 このアサーションは、mssp:SslContextToken の外側で使用することはできません。|  
  
## <a name="see-also"></a>関連項目

- [カスタム WSDL パブリケーション](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
- [方法: カスタム WSDL をエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [方法: カスタム WSDL をインポートする](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)

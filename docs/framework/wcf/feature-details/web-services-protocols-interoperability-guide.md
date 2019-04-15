---
title: Web サービス プロトコルの相互運用性ガイド
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 647212558b6be38e9b30239f7fb71213e6eb7d86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228270"
---
# <a name="web-services-protocols-interoperability-guide"></a>Web サービス プロトコルの相互運用性ガイド
Windows Communication Foundation (WCF) は、さまざまな Web サービス プロトコルを実装します。 これらのプロトコルの多くには、さまざまなオプションと拡張ポイントが用意されており、それらの実装は実装者の裁量に任されています。 このトピックでは、WCF が実装する Web サービス プロトコルの一覧を示します。 サポートされる各プロトコルの実装の詳細については、このセクションの他のトピックで説明します。  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>WCF が実装する Web サービス プロトコル  
 WCF チャネルを通じて Web サービス (WS) のインフラストラクチャ プロトコルのサポートを提供して、Web サービス、コントラクト機能を通じてアプリケーション プロトコル。 アプリケーション プロトコルの相互運用性は、XML スキーマ記述言語 (XSD) 1.0 と Web サービス記述言語 (WSDL) 1.1 を通じて実現されます。  
  
 インフラストラクチャ プロトコルの相互運用性は、WS-* 仕様によって提供されます。 WCF チャネル ws-数のサポートを提供する\*インフラストラクチャ プロトコル。 WCF チャネルは、バインド要素を使用して構成されます。 次の表には、ws-の完全な一覧が含まれて\*さまざまな WCF バインド要素によって実装されるインフラストラクチャ プロトコル。  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 次の表に、仕様をサポートしています。  
  
|仕様/ドキュメント|リンク|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](https://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 HTTP バインディング|[簡易オブジェクト アクセス プロトコル (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)セクション 7|  
|SOAP 1.2 HTTP バインディング|[SOAP Version 1.2 Part 2:Adjuncts (Second Edition)](https://go.microsoft.com/fwlink/?LinkId=95329)セクション 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>次の表に、仕様をサポートします。  
  
|仕様/ドキュメント|リンク|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (Fourth Edition)](https://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 コア|[SOAP Version 1.2 Part 1:Messaging Framework (第 2 版)](https://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS-Addressing 2004/08|[Web Services Addressing (WS-Addressing)](https://go.microsoft.com/fwlink/?LinkId=81239)|  
|W3C Web Services Addressing 1.0 - コア|[Web Services Addressing 1.0 - Core](https://go.microsoft.com/fwlink/?LinkId=96688)|  
|W3C Web Services Addressing 1.0 - SOAP バインディング|[Web Services Addressing 1.0 - SOAP Binding](https://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C Web Services Addressing 1.0 - WSDL バインディング*|[Web Services Addressing 1.0 - WSDL Binding](https://go.microsoft.com/fwlink/?LinkId=96690)|  
|W3C Web Services Addressing 1.0 - メタデータ|[Web Services Addressing 1.0 - Metadata](https://www.w3.org/TR/ws-addr-metadata/)|  
|WSDL SOAP1.1 バインディング|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)|  
|WSDL SOAP1.2 バインディング|[WSDL 1.1 Binding Extension for SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 次の表に、仕様をサポートしています。  
  
|仕様/ドキュメント|リンク|  
|-----------------------------|----------|  
|XOP|[XML-binary Optimized Packaging](https://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 バインディング|[SOAP Message Transmission Optimization Mechanism](https://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 バインディング|[SOAP 1.1 Binding for MTOM 1.0](https://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-Policy アサーション|未公開|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> 次の表に、仕様をサポートしています。  
  
|仕様/ドキュメント|リンク|  
|-----------------------------|----------|  
|WSS:SOAP Message Security 1.0|[Web Services Security:SOAP Message Security 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS:ユーザー名 Token Profile 1.0|[Web Services Security UsernameToken Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> 必要なPassword/@Type= PasswordText (既定値)|  
|WSS:X.509 Token Profile 1.0|[Web Services Security X.509 Certificate Token Profile](https://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS:SAML 1.1 トークン Profile 1.0|[Web Services Security:SAML トークン プロファイル](https://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS:SOAP Message Security 1.1|[Web Services Security:SOAP Message Security 1.1](https://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS Username Token Profile 1.1|[Web Services Security UsernameToken Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> パスワード ベースのキー派生は実装していません。<br /><br /> 必要なPassword/@Type= PasswordText (既定値)|  
|WSS:X509 token Profile 1.1|[Web Services Security X.509 Certificate Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS:Kerberos トークン プロファイル 1.1|[Web Services Security Kerberos Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS:SAML 1.1 トークン プロファイル 1.1|[Web Services Security SAML Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS-SecureConversation|[Web Services Secure Conversation Language](https://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Web Services Trust Language](https://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Web Services Secure Conversation Language](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> OASIS WS-SX 技術委員会に提出された正誤表で修正されています。<br /><br /> [ws-sx message](https://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[信頼できるメッセージング プロトコル バージョン 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 次の表に、仕様をサポートしています。  
  
|仕様/ドキュメント|Link|  
|-----------------------------|----------|  
|WS-Coordination|[Web Services Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Web Services Atomic Transaction](https://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>、<xref:System.ServiceModel.Description.MetadataImporter>、<xref:System.ServiceModel.Description.WsdlExporter>、<xref:System.ServiceModel.Description.WsdlImporter>、および <xref:System.ServiceModel.Description.MetadataResolver> の各クラスは、次のメタデータ仕様をサポートします。  
  
-   [XML Schema Part 1:Structures Second Edition](https://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML Schema Part 2:データ型の第 2 版](https://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [Ws-policy 1.2](https://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](https://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS-MetadataExchange 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [メタデータ取得のための WS-Transfer Get ](https://go.microsoft.com/fwlink/?LinkId=96708)  
  
 さらに、次のような相互運用性プロファイルは、WCF で実装されます。  
  
-   [Basic Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Simple SOAP Binding 1.0](https://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Basic Security Profile 1.0 ワーキング ドラフト](https://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>関連項目

- [システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [メッセージング プロトコル](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)
- [データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [WSDL とポリシー](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
- [セキュリティ プロトコル](../../../../docs/framework/wcf/feature-details/security-protocols.md)
- [信頼できるメッセージング プロトコル バージョン 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)
- [信頼できるメッセージング プロトコル バージョン 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)
- [トランザクション プロトコル](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)
- [コンテキスト交換プロトコル](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)

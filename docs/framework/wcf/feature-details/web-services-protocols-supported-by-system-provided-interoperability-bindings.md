---
title: システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 25efda74d205a36332a801e91ddc508796f7df5d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463986"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
Wcf (WCF) は、Web サービス仕様と呼ばれる一連の仕様をサポートする Web サービスと相互運用できるように構築されています。 相互運用性のベスト プラクティスを実現するためにサービス構成を簡略化するために、WCF では、相互運用可能な<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>システム<xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>指定の<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>バインディング 、 、および の 3 つのバインディングが導入されています。 構造化情報標準 (OASIS) の高度化のための組織との相互運用性のために、 WCF には、相互運用可能なシステム<xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>提供のバインディングが 1 つ含まれています。 メタデータのパブリケーションの場合、WCF には、2 つの相互運用可能なシステム指定のバインディングが含まれています: [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)と[\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)。 このトピックでは、システム指定の相互運用可能なバインディングがサポートする仕様を示します。  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>basicHttpBinding、wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding の各バインディングでサポートされる Web サービス プロトコル  
  
### <a name="all-bindings"></a>すべてのバインディング  
 [\<基本 HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<、wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、および[\<ws2007HttpBinding>バインディング](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)は、次のプロトコルをサポートします。  
  
> [!NOTE]
> メタデータの公開に使用するバインディングについては、このトピックで後述する「システム指定のメタデータ バインディング」を参照してください。  
  
|カテゴリ|Protocol|仕様と用途|  
|--------------|--------------|-----------------------------|  
|トランスポート|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`、`WSHttpBinding`、および `WS2007HttpBinding` は、HTTP トランスポートおよび HTTPS トランスポートを使用します。|  
|メッセージング|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`、`wsHttpBinding`、および `ws2007HttpBinding` は、MTOM (Message Transmission Optimization Mechanism) をサポートしています。 既定では使用されません。 MTOM を使用するには、`messageEncoding` 属性を `"Mtom"` に設定します。<br /><br /> 例:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadata|WSDL 1.1|[WSDL 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF では、Web サービス記述言語 (WSDL) を使用してサービスを記述します。|  
|Metadata|WS-Policy|[WS-Policy](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF では、WS-Policy 仕様とドメイン固有のアサーションを使用して、サービスの要件と機能を記述します。|  
|Metadata|WS-Policy 1.5|[WS-Policy 1.5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF では、WS-Policy 仕様とドメイン固有のアサーションを使用して、サービスの要件と機能を記述します。|  
|Metadata|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF は、Web サービス記述言語 (WSDL) のさまざまなスコープでポリシー式をアタッチする WS-PolicyAttachment を実装します。|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF は、XML スキーマ、WSDL、および WS ポリシーを取得する WS メタデータの交換を実装します。|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|カテゴリ|Protocol|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.1|[SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Basic Profile 1.1 に従って、`basicHttpBinding` 要素は SOAP 1.1 メッセージ プロトコルを実装しています。|  
|Security|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Basic Security Profile に従って、`basicHttpBinding` 要素は、ユーザー名/パスワードおよび X.509 ベースのセキュリティを実現するために、WSS (Web Services Security) SOAP Message Security 1.0 仕様を実装しています。<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Security|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP Message Security UsernameToken Profile 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Security|WSS SOAP メッセージ セキュリティ X.509 証明書トークン プロファイル 1.0|[WSS SOAP メッセージ セキュリティ X.509 証明書トークン プロファイル 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding  
  
|カテゴリ|Protocol|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.2|[基本](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Messaging Framework](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP バインディングを含む)](https://www.w3.org/TR/soap12-part2/)|  
|メッセージング|WS-アドレッシング 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Services Addressing 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`、`ws2007HttpBinding`、および `wsDualHttpBinding` は、非同期メッセージング、メッセージ相関、およびトランスポート中立のアドレス指定機構を有効にするために、W3C (World Wide Web Consortium) WS-Addressing 勧告を実装しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|メッセージング|WS-Addressing 1.0 - メタデータ|[WS-アドレス指定 1.0 メタデータ](https://www.w3.org/2007/05/addressing/metadata/)このプロトコルのサポートは、ServiceMetadata 動作でポリシーバージョンを設定することで有効になります - policyversion が 1.2 (デフォルト) に設定され、wsdl 記述は WS-Addressing wsdl に準拠しており、policyversion は 1.5 に設定され、wsdl 記述は ws-addressing メタデータに準拠しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|Security|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> `securityMode` 属性が "wsSecurityOverHttp" (既定) に設定され、`wsSecurity` 子要素を使用してパラメーターが構成されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Security|WSS SOAP メッセージ セキュリティ ユーザー名 トークン プロファイル 1.1|[WSS SOAP Message Security UsernameToken Profile 1.0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username" に設定されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Security|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP Message Security X.509 Certificate Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username"、"Certificate"、または "None" に設定されている場合に、メッセージを保護するために使用します。 また、`wsSecurity` 要素の `authenticationMode` 属性が "Certificate" に設定されている場合は、クライアント認証に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Security|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP メッセージ セキュリティ Kerberos トークン プロファイル 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Windows" に設定されている場合に、認証とメッセージの保護に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Security|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> `security/@mode` 属性が "Message" に設定され、`message/@establishSecurityContext` 属性が "true" (既定値) に設定されている場合に、セッションをセキュリティで保護するために使用します。|  
|Security|WS-Trust|[WS-トラスト](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> WS-SecureConversation で使用されます (上記を参照)。|  
|信頼できるメッセージ機能|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> バインディングが `reliableSession` を使用するように構成されている場合に使用します。<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|トランザクション|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> トランザクション マネージャー間の通信に使用します。 WCF クライアントとサービスは、常にローカル のトランザクション マネージャーを使用します。|  
|トランザクション|WS-Coordination|[WS-Coordination](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> `flowTransactions` 属性が "Allowed" または "Required" に設定されている場合に、トランザクション コンテキストをフローするために使用します。<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding および ws2007FederationHttpBinding  
 [\<サード](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)パーティがクライアントの認証に使用されるトークンを発行するフェデレーション シナリオをサポートするために、wsFederationHttpBinding>および[\<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)要素が導入されています。 `wsHttpBinding` で使用されるプロトコルに加えて、`wsFederationHttpBinding` では次のものを使用します。  
  
- トークンを発行するための `WS-Trust`  
  
- 最も一般的に発行されるトークンの形式のための WSS SAML (Security Assertions Markup Language) Token Profile 1.0 および 1.1  
  
 例:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'/>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 詳細については、「[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)」を参照してください。  
  
## <a name="system-provided-metadata-bindings"></a>システム指定のメタデータ バインディング  
 次の表に、<xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> クラスによって公開される、システム指定の相互運用可能なメタデータ バインディングによってサポートされるプロトコルを示します。  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [\<バインディングは>、](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)次のプロトコルをサポートしています。 このバインディングの使用の詳細については、「[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)」を参照してください。  
  
|カテゴリ|Protocol|仕様と用途|  
|--------------|--------------|-----------------------------|  
|トランスポート|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|メッセージング|SOAP 1.2|[基本](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Messaging Framework](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP バインディングを含む)](https://www.w3.org/TR/soap12-part2/)|  
|メッセージング|WS-アドレッシング 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Services Addressing 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF は、XML スキーマ、WSDL、および WS ポリシーを取得する WS メタデータの交換を実装します。|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 >は、次のプロトコルをサポートしています。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) このバインディングの使用の詳細については、「[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)」を参照してください。  
  
|カテゴリ|Protocol|仕様と用途|  
|--------------|--------------|-----------------------------|  
|トランスポート|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> トランスポート セキュリティは有効です。|  
|メッセージング|SOAP 1.2|[基本](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Messaging Framework](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP バインディングを含む)](https://www.w3.org/TR/soap12-part2/)|  
|メッセージング|WS-アドレッシング 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Services Addressing 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF は、XML スキーマ、WSDL、および WS ポリシーを取得する WS メタデータの交換を実装します。|  
  
## <a name="see-also"></a>関連項目

- [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)

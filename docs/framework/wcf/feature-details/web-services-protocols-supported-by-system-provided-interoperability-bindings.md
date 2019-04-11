---
title: システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: caf9a66e8c42fb80955539aa9d3eb32179309004
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157457"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
Windows Communication Foundation (WCF) は、一連の Web サービスの仕様と呼ばれる仕様をサポートする Web サービスと相互に構築されています。 WCF の相互運用性のベスト プラクティスのサービス構成を簡素化するには次の 3 つの相互運用可能なシステム指定のバインディングが導入されています: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>、 <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>、および<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>します。 WCF には Advancement of Structured Information Standards (OASIS) 標準の組織と相互運用性には 1 つの相互運用可能なシステム指定のバインディングが含まれています:<xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>します。 WCF にはメタデータの公開には 2 つの相互運用可能なシステム指定のバインディングが含まれています: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)と[ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)します。 このトピックでは、システム指定の相互運用可能なバインディングがサポートする仕様を示します。  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>basicHttpBinding、wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding の各バインディングでサポートされる Web サービス プロトコル  
  
### <a name="all-bindings"></a>すべてのバインディング  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、および[ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)バインディングのサポート、次のプロトコル。  
  
> [!NOTE]
>  メタデータの公開に使用するバインディングについては、このトピックで後述する「システム指定のメタデータ バインディング」を参照してください。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`、 `WSHttpBinding`、および`WS2007HttpBinding`、HTTP および HTTPS トランスポートを使用します。|  
|メッセージング|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`、 `wsHttpBinding`、および`ws2007HttpBinding`Message Transmission Optimization Mechanism (MTOM) をサポートします。 既定では使用されません。 MTOM を使用するには、`messageEncoding` 属性を `"Mtom"` に設定します。<br /><br /> 例:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|メタデータ|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF では、Web サービス記述言語 (WSDL) を使用して、サービスについて説明します。|  
|メタデータ|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF では、ドメイン固有のアサーションと共に Ws-policy 仕様を使用して、サービスの要件と機能について説明します。|  
|メタデータ|WS-Policy 1.5|[WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF では、ドメイン固有のアサーションと共に Ws-policy 仕様を使用して、サービスの要件と機能について説明します。|  
|メタデータ|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF では、Web サービス記述言語 (WSDL) でのさまざまなスコープでポリシー式をアタッチするには、Ws-policyattachment を実装します。|  
|メタデータ|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF には、XML スキーマ、WSDL、Ws-policy を取得するには、Ws-metadataexchange が実装されています。|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.1|[SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Basic Profile 1.1 に従って、`basicHttpBinding` 要素は SOAP 1.1 メッセージ プロトコルを実装しています。|  
|セキュリティ|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Basic Security Profile に従って、`basicHttpBinding` 要素は、ユーザー名/パスワードおよび X.509 ベースのセキュリティを実現するために、WSS (Web Services Security) SOAP Message Security 1.0 仕様を実装しています。<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP Message Security UsernameToken Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|セキュリティ|WSS SOAP メッセージ セキュリティ X.509 証明書 Token Profile 1.0|[WSS SOAP メッセージ セキュリティ X.509 証明書 Token Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Messaging Framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP バインディングを含む)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`、`ws2007HttpBinding`、および `wsDualHttpBinding` は、非同期メッセージング、メッセージ相関、およびトランスポート中立のアドレス指定機構を有効にするために、W3C (World Wide Web Consortium) WS-Addressing 勧告を実装しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|メッセージング|WS-Addressing 1.0 - メタデータ|[Ws-addressing 1.0 メタデータ](https://www.w3.org/2007/05/addressing/metadata)1.2 (既定値) に設定されています ServiceMetadata 動作のポリシーのバージョンを設定してこのプロトコルのサポートが有効になっている、wsdl 記述は Ws-addressing の wsdl に準拠しての1.5 に設定されています、wsdl 記述は ws-addressing メタデータに準拠しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|セキュリティ|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> `securityMode` 属性が "wsSecurityOverHttp" (既定) に設定され、`wsSecurity` 子要素を使用してパラメーターが構成されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP メッセージ セキュリティ UsernameToken Profile 1.1|[WSS SOAP Message Security UsernameToken Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username" に設定されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP Message Security X.509 Certificate Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username"、"Certificate"、または "None" に設定されている場合に、メッセージを保護するために使用します。 また、`wsSecurity` 要素の `authenticationMode` 属性が "Certificate" に設定されている場合は、クライアント認証に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP メッセージ Security Kerberos Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Windows" に設定されている場合に、認証とメッセージの保護に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|セキュリティ|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> `security/@mode` 属性が "Message" に設定され、`message/@establishSecurityContext` 属性が "true" (既定値) に設定されている場合に、セッションをセキュリティで保護するために使用します。|  
|セキュリティ|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation で使用されます (上記を参照)。|  
|信頼できるメッセージ機能|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> バインディングが `reliableSession` を使用するように構成されている場合に使用します。<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|トランザクション|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> トランザクション マネージャー間の通信に使用します。 WCF クライアントおよびサービスでは、常にローカル トランザクション マネージャーを使用するようにします。|  
|トランザクション|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> `flowTransactions` 属性が "Allowed" または "Required" に設定されている場合に、トランザクション コンテキストをフローするために使用します。<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding および ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)と[ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)が 3 つ目のフェデレーション シナリオでは、サポートを提供する要素が導入されていますパーティは、クライアントの認証に使用するトークンを発行します。 `wsHttpBinding` で使用されるプロトコルに加えて、`wsFederationHttpBinding` では次のものを使用します。  
  
-   `WS-Trust` トークンの発行。  
  
-   最も一般的に発行されるトークンの形式のための WSS SAML (Security Assertions Markup Language) Token Profile 1.0 および 1.1  
  
 例:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 詳細については、次を参照してください。[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)します。  
  
## <a name="system-provided-metadata-bindings"></a>システム指定のメタデータ バインディング  
 次の表に、<xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> クラスによって公開される、システム指定の相互運用可能なメタデータ バインディングによってサポートされるプロトコルを示します。  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)バインディングは、次のプロトコルをサポートしています。 このバインディングの使用に関する詳細については、次を参照してください。[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)します。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|メッセージング|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Messaging Framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP バインディングを含む)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|メタデータ|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF には、XML スキーマ、WSDL、Ws-policy を取得するには、Ws-metadataexchange が実装されています。|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)は次のプロトコルをサポートします。 このバインディングの使用に関する詳細については、次を参照してください。[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)します。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> トランスポート セキュリティは有効です。|  
|メッセージング|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Messaging Framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP バインディングを含む)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|メタデータ|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF には、XML スキーマ、WSDL、Ws-policy を取得するには、Ws-metadataexchange が実装されています。|  
  
## <a name="see-also"></a>関連項目

- [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)

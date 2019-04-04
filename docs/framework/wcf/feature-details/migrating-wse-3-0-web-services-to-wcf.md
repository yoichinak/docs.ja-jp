---
title: WSE 3.0 Web サービスの WCF への移行
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 30b9d1fa3c8b2123b3a71465f9ccebf722740d0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668251"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web サービスの WCF への移行
WSE 3.0 Web サービスの Windows Communication Foundation (WCF) への移行の利点は、パフォーマンスが向上し、サポートの追加のトランスポート、追加のセキュリティ シナリオ、および ws-* 仕様。 WSE 3.0 から WCF に移行する Web サービスは、最大 200% ~ 400% のパフォーマンス向上に発生します。 WCF でサポートされているトランスポートの詳細については、[トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)を参照してください。 WCF でサポートされるシナリオの一覧は、[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)を参照してください。 WCF でサポートされている仕様の一覧は、[Web サービス プロトコルの相互運用性ガイド](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)を参照してください。  
  
 次のセクションでは、WSE 3.0 Web サービスの特定の機能を WCF に移行する方法のガイダンスを提供します。  
  
## <a name="general"></a>全般  
 WSE 3.0 と WCF アプリケーションには、ネットワーク レベルの相互運用性と共通の用語セットが含まれます。 WSE 3.0 と WCF アプリケーションは、ワイヤレベルの相互運用可能な ws のセットに基づいて * 両方がサポートする仕様。 WSE 3.0 または WCF アプリケーションの開発時に WSE と認証モードの設定不要のセキュリティ アサーションの名前などの用語の一般的なセットがあります。  
  
 WSE 3.0 のプログラミング モデルを WCF と ASP.NET 間で類似した多くの側面もはまたはそれらが異なるです。 詳細については、WCF プログラミング モデルは、[基本的なプログラミング ライフ サイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)を参照してください。  
  
> [!NOTE]
>  WSE Web サービスを WCF に移行する、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールは、クライアントを生成するために使用できます。 ただし、このクライアントには、WCF サービスの開始点として使用できるインターフェイスとクラスも含まれます。 生成されるインターフェイスの <xref:System.ServiceModel.OperationContractAttribute> 属性は、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> プロパティが `*` に設定されたコントラクトのメンバーに適用されます。 WSE クライアントがこの設定を Web サービスを呼び出すと、次の例外がスローされます。**Web.services3.responseprocessingexception::WSE910:応答メッセージの処理中にエラーが発生したし、は、内部例外で、エラーを見つけることができます**します。 このエラーを軽減するには、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 属性の <xref:System.ServiceModel.OperationContractAttribute> プロパティを `null` 以外の値 (`http://Microsoft.WCF.Documentation/ResponseToOCAMethod` など) に設定します。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>ポリシー ファイルを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WCF サービスは、構成ファイルを使用して、サービスをセキュリティで保護して、このメカニズムは、WSE 3.0 ポリシー ファイルに似ています。 WSE 3.0 でポリシー ファイルを使用して Web サービスをセキュリティ保護するときは、設定不要のセキュリティ アサーションまたはカスタム ポリシー アサーションを使用します。 設定不要のセキュリティ アサーションは、WCF のセキュリティ バインド要素の認証モードに対応しています。 だけでなく、WCF 認証モードと WSE 3.0 の設定不要のセキュリティ アサーションの名前は、同じまたは、同様に、同じ資格情報の種類を使用してメッセージを保護します。 たとえば、 `usernameForCertificate` WSE 3.0 の設定不要のセキュリティ アサーションにマップ、 `UsernameForCertificate` WCF での認証モード。 次のコード例は、最小限のポリシーを使用する方法を示します、 `usernameForCertificate` WSE 3.0 の設定不要のセキュリティ アサーションにマップする`UsernameForCertificate`で WCF カスタム バインドでの認証モード。  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 WCF へのポリシー ファイルで指定されている WSE 3.0 Web サービスのセキュリティ設定を移行するには、構成ファイルで、カスタム バインディングを作成し、設定不要のセキュリティ アサーションを同等の認証モードに設定する必要があります。 さらに、WSE 3.0 クライアントがサービスと通信するときに 2004 年 8 月版の WS-Addressing 仕様を使用するように、カスタム バインドを構成する必要もあります。 移行した WCF サービスが WSE 3.0 クライアントとの通信は必要ありませんし、セキュリティのパリティを維持する必要がありますのみ、カスタム バインドを作成する代わりに適切なセキュリティ設定で WCF のシステム定義バインディングの使用を検討します。  
  
 次の表では、WSE 3.0 ポリシー ファイルと WCF で同等のカスタム バインドの間のマッピングを示します。  
  
|WSE 3.0 の設定不要のセキュリティ アサーション|WCF のカスタム バインド構成|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF でカスタム バインディングの作成の詳細については、[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)を参照してください。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>アプリケーション コードを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WSE 3.0 または WCF を使用するかどうかは、構成ではなく、アプリケーション コードでセキュリティ要件を指定できます。 WSE 3.0 でこれを行うには、`Policy` クラスの派生クラスを作成してから、`Add` メソッドを呼び出して要件を追加します。 セキュリティ要件を指定するコードの詳細については、次を参照してください。[方法。ポリシー ファイルを使用せず、Web サービスをセキュリティで保護された](https://go.microsoft.com/fwlink/?LinkId=73747)します。 WCF では、コードでセキュリティ要件を指定するのインスタンスを作成、<xref:System.ServiceModel.Channels.BindingElementCollection>クラスし、インスタンスの追加、<xref:System.ServiceModel.Channels.SecurityBindingElement>を<xref:System.ServiceModel.Channels.BindingElementCollection>します。 セキュリティ アサーション要件は、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的認証モード ヘルパー メソッドを使用して設定します。 WCF を使用してコードでセキュリティ要件を指定する方法の詳細については、次を参照してください。[方法。SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)と[方法。指定した認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)です。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 カスタム ポリシー アサーション  
 WSE 3.0 には、2 種類のカスタム ポリシー アサーションがあります。一方は SOAP メッセージをセキュリティで保護し、もう一方は SOAP メッセージをセキュリティで保護しません。 SOAP メッセージ セキュリティで保護するポリシー アサーションは WSE 3.0 から派生`SecurityPolicyAssertion`クラスと WCF の概念と同等では、<xref:System.ServiceModel.Channels.SecurityBindingElement>クラス。  
  
 重要な注意点は、WSE 3.0 の設定不要のセキュリティ アサーション WCF 認証モードのサブセットであることです。 WSE 3.0 カスタム ポリシー アサーションを作成した場合と同じ WCF 認証モードである可能性があります。 たとえば、WSE 3.0 は、設定不要の `UsernameOverTransport` セキュリティ アサーションと等価な CertificateOverTransport セキュリティ アサーションを提供しませんが、クライアントを認証するために X.509 証明書を使用します。 このシナリオでは、独自のカスタム ポリシー アサーションを定義する場合は、WCF では簡単に移行します。 WCF を利用する、静的な認証モードのヘルパー メソッドを WCF を構成するためにこのシナリオでは、認証モードを定義します<xref:System.ServiceModel.Channels.SecurityBindingElement>します。  
  
 SOAP メッセージをセキュリティで保護するカスタム ポリシー アサーションに相当する WCF 認証モードがない場合、派生クラスを<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>または<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF クラスし、等価なバインド要素を指定します。 詳細については、次を参照してください。[方法。SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)します。  
  
 SOAP メッセージ セキュリティで保護するカスタム ポリシー アサーションを変換するには、[フィルター](../../../../docs/framework/wcf/feature-details/filtering.md)サンプルとサンプル[カスタム メッセージ インターセプター](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)を参照してください。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 カスタム セキュリティ トークン  
 カスタム トークンを作成するためには、WCF プログラミング モデルは、WSE 3.0 と異なります。 WSE でカスタム トークンを作成する方法については、[カスタム セキュリティ トークンの作成](https://go.microsoft.com/fwlink/?LinkID=73750)を参照してください。 WCF でカスタム トークンを作成する方法については、次を参照してください。[方法。カスタム トークンを作成](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 カスタム トークン マネージャー  
 カスタム トークン マネージャーを作成するためのプログラミング モデルは、WCF で WSE 3.0 と異なります。 カスタム トークン マネージャーとカスタム セキュリティ トークンを必要とされる他のコンポーネントを作成する方法の詳細については、次を参照してください。[方法。カスタム トークンを作成](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
> [!NOTE]
>  カスタムを作成した場合`UsernameToken`セキュリティ トークン マネージャーは、WCF にはカスタム セキュリティ トークン マネージャーを作成するよりも、認証ロジックを指定する簡単なメカニズムが用意されています。 詳細については、次を参照してください。[方法。カスタム ユーザー名およびパスワード検証を使用して、](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)します。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM エンコードされた SOAP メッセージを使用する WSE 3.0 Web サービス  
 WSE 3 アプリケーションのように、WCF アプリケーションは、エンコードを構成で MTOM メッセージを指定できます。 この設定を移行するには追加、 [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)サービスのバインドにします。 次のコード例では、MTOM エンコーディングを指定する方法 WSE 3.0 の WCF で同等であるサービスを示します。  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE メッセージング API を使用する WSE 3.0 アプリケーション  
 クライアントと Web サービス間でやり取りされる XML に直接アクセスするために WSE メッセージング API が使用されている場合は、"Plain Old XML" (POX) を使用するようにアプリケーションを変換できます。 POX の詳細については、[POX アプリケーションとの相互運用](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)を参照してください。 WSE メッセージング API の詳細については、[送信および受信 SOAP メッセージを使用して WSE メッセージング API](https://go.microsoft.com/fwlink/?LinkID=73755)を参照してください。  
  
## <a name="transports"></a>トランスポート  
  
### <a name="tcp"></a>TCP  
 既定では、WSE 3.0 クライアントおよび TCP トランスポートを使用して SOAP メッセージを送信する Web サービス相互運用不可能 WCF クライアントおよび Web サービスとします。 このような非互換性は、TCP プロトコルで使用されるフレームの違いとパフォーマンス上の理由に起因します。 ただし、WCF サンプルでは、WSE 3.0 と相互運用するカスタム TCP セッションを実装する方法について説明します。 詳細については、このサンプルは、次を参照してください。[トランスポート。WSE 3.0 TCP 相互運用性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)します。  
  
 WCF アプリケーションが TCP トランスポートを使用することを指定するには、使用、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)します。  
  
### <a name="custom-transport"></a>カスタム トランスポート  
 WCF では、WSE 3.0 カスタム トランスポートの等価は、チャネル拡張です。 チャネル拡張機能の作成方法の詳細については、[チャネル レイヤーの拡張](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [基本的なプログラミング ライフサイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [方法: 指定した認証モード用の SecurityBindingElement を作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)

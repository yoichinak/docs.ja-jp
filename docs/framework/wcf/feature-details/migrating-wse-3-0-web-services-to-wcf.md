---
title: WSE 3.0 Web サービスの WCF への移行
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184577"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web サービスの WCF への移行
WSE 3.0 Web サービスを Wcf (WCF) に移行する利点としては、パフォーマンスの向上と追加のトランスポートのサポート、追加のセキュリティ シナリオ、および WS-* 仕様が含まれます。 WSE 3.0 から WCF に移行される Web サービスでは、最大で 200 % から 400% のパフォーマンスが向上します。 WCF でサポートされるトランスポートの詳細については、「[トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)」を参照してください。 WCF でサポートされるシナリオの一覧については、「[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)」を参照してください。 WCF でサポートされる仕様の一覧については、「 [Web サービス プロトコルの相互運用性ガイド](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)」を参照してください。  
  
 次のセクションでは、WSE 3.0 Web サービスの特定の機能を WCF に移行する方法について説明します。  
  
## <a name="general"></a>全般  
 WSE 3.0 および WCF アプリケーションには、ワイヤ レベルの相互運用性と一般的な用語セットが含まれます。 WSE 3.0 と WCF アプリケーションは、両方がサポートする WS-* 仕様のセットに基づいて、ワイヤ レベルの相互運用可能です。 WSE 3.0 または WCF アプリケーションを開発するときには、WSE のターンキー セキュリティ アサーションの名前や認証モードなどの用語の共通セットがあります。  
  
 WCF と ASP.NET または WSE 3.0 プログラミング モデルの間には多くの類似した側面がありますが、これらは異なります。 WCF プログラミング モデルの詳細については、「[プログラミングの基本ライフサイクル」を](../../../../docs/framework/wcf/basic-programming-lifecycle.md)参照してください。  
  
> [!NOTE]
> WSE Web サービスを WCF に移行するには、[サービス モデル メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを使用してクライアントを生成できます。 ただし、このクライアントには、WCF サービスの開始点として使用できるインターフェイスとクラスも含まれます。 生成されるインターフェイスの <xref:System.ServiceModel.OperationContractAttribute> 属性は、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> プロパティが `*` に設定されたコントラクトのメンバーに適用されます。 WSE クライアントがこの設定で Web サービスを呼び出すと、**次の**例外がスローされます。 このエラーを軽減するには、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 属性の <xref:System.ServiceModel.OperationContractAttribute> プロパティを `null` 以外の値 (`http://Microsoft.WCF.Documentation/ResponseToOCAMethod` など) に設定します。  
  
## <a name="security"></a>Security  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>ポリシー ファイルを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WCF サービスは、構成ファイルを使用してサービスをセキュリティで保護することができ、そのメカニズムは WSE 3.0 ポリシー ファイルに似ています。 WSE 3.0 でポリシー ファイルを使用して Web サービスをセキュリティ保護するときは、設定不要のセキュリティ アサーションまたはカスタム ポリシー アサーションを使用します。 ターンキー セキュリティ アサーションは、WCF セキュリティ バインディング要素の認証モードに密接にマップされます。 WCF 認証モードと WSE 3.0 ターンキー セキュリティ アサーションは同じまたは同様に命名されているだけでなく、同じ資格情報の種類を使用してメッセージをセキュリティで保護します。 たとえば、WSE `usernameForCertificate` 3.0 のターンキー セキュリティ アサーションは`UsernameForCertificate`、WCF の認証モードにマップされます。 次のコード例は、WSE 3.0`usernameForCertificate`のターンキー セキュリティ アサーションを使用する最小限の`UsernameForCertificate`ポリシーが、カスタム バインドの WCF の認証モードにマップする方法を示しています。  
  
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
  
 ポリシー ファイルで指定されている WSE 3.0 Web サービスのセキュリティ設定を WCF に移行するには、カスタム バインドを構成ファイルに作成し、ターンキー セキュリティ アサーションを同等の認証モードに設定する必要があります。 さらに、WSE 3.0 クライアントがサービスと通信するときに 2004 年 8 月版の WS-Addressing 仕様を使用するように、カスタム バインディングを構成する必要もあります。 移行された WCF サービスが WSE 3.0 クライアントとの通信を必要とせず、セキュリティ パリティのみを維持する必要がある場合は、カスタム バインドを作成する代わりに、適切なセキュリティ設定で WCF システム定義のバインドを使用することを検討してください。  
  
 次の表は、WSE 3.0 ポリシー ファイルと、WCF の対応するカスタム バインドのマッピングを示しています。  
  
|WSE 3.0 の設定不要のセキュリティ アサーション|WCF のカスタム バインド構成|  
|----------------------------------------|--------------------------------------|  
|\<ユーザー名オーバートランスポートセキュリティ />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<相互証明書10セキュリティ />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<証明書セキュリティ />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<証明書セキュリティ />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<セキュリティ />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<相互証明書11セキュリティ />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF でのカスタム バインドの作成の詳細については、「[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>アプリケーション コードを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WSE 3.0 または WCF のどちらを使用するか、構成ではなくアプリケーション コードでセキュリティ要件を指定できます。 WSE 3.0 でこれを行うには、`Policy` クラスの派生クラスを作成してから、`Add` メソッドを呼び出して要件を追加します。 コードでのセキュリティ要件の指定の詳細については、「[方法 : ポリシー ファイルを使用せずに Web サービスをセキュリティで保護する](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10))」を参照してください。 WCF で、コードでセキュリティ要件を指定するには、クラスのインスタンス<xref:System.ServiceModel.Channels.BindingElementCollection>を作成し、 に<xref:System.ServiceModel.Channels.SecurityBindingElement>のインスタンスを<xref:System.ServiceModel.Channels.BindingElementCollection>追加します。 セキュリティ アサーション要件は、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的認証モード ヘルパー メソッドを使用して設定します。 WCF を使用してコードでセキュリティ要件を指定する方法の詳細については、「[方法 : SecurityBindingElement を使用してカスタム バインドを作成](how-to-create-a-custom-binding-using-the-securitybindingelement.md)[する」および「方法 : 指定された認証モードの SecurityBindingElement を作成する](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)」を参照してください。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 カスタム ポリシー アサーション  
 WSE 3.0 には、2 種類のカスタム ポリシー アサーションがあります。一方は SOAP メッセージをセキュリティで保護し、もう一方は SOAP メッセージをセキュリティで保護しません。 セキュリティ保護された SOAP メッセージが WSE 3.0`SecurityPolicyAssertion`クラスから派生し、WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>の概念的な同等のクラスをセキュリティで保護するポリシー アサーションはクラスです。  
  
 注意すべき重要な点は、WSE 3.0 のターンキー セキュリティ アサーションは WCF 認証モードのサブセットです。 WSE 3.0 でカスタム ポリシー アサーションを作成した場合は、同等の WCF 認証モードがある可能性があります。 たとえば、WSE 3.0 は、設定不要の `UsernameOverTransport` セキュリティ アサーションと等価な CertificateOverTransport セキュリティ アサーションを提供しませんが、クライアントを認証するために X.509 証明書を使用します。 このシナリオに独自のカスタム ポリシー アサーションを定義した場合、WCF は移行を簡単にします。 WCF では、このシナリオの認証モードを定義するため、静的な認証モードヘルパー メソッドを利用して WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>を構成できます。  
  
 SOAP メッセージをセキュリティで保護するカスタム ポリシー アサーションと同等の WCF 認証モードがない場合は、<xref:System.ServiceModel.Channels.TransportSecurityBindingElement><xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>または<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF クラスからクラスを派生し、同等のバインド要素を指定します。 詳細については、「[方法 : SecurityBindingElement を使用してカスタム バインドを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)」を参照してください。  
  
 SOAP メッセージを保護しないカスタム ポリシー アサーションを変換するには、[フィルタリング](../../../../docs/framework/wcf/feature-details/filtering.md)および[サンプルのカスタム メッセージ インターセプター](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)を参照してください。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 カスタム セキュリティ トークン  
 カスタム トークンを作成するための WCF プログラミング モデルは、WSE 3.0 とは異なります。 WSE でのカスタム トークンの作成の詳細については、「[カスタム セキュリティ トークンの作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10))」を参照してください。 WCF でのカスタム トークンの作成の詳細については、「[方法 : カスタム トークンを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)」を参照してください。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 カスタム トークン マネージャー  
 カスタム トークン マネージャーを作成するためのプログラミング モデルは、WSE 3.0 と WCF では異なります。 カスタム トークン マネージャーとカスタム セキュリティ トークンに必要なその他のコンポーネントを作成する方法の詳細については、「[方法 : カスタム トークンを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)」を参照してください。  
  
> [!NOTE]
> カスタム`UsernameToken`セキュリティ トークン マネージャーを作成した場合、WCF では、カスタム セキュリティ トークン マネージャーを作成するよりも簡単に認証ロジックを指定するメカニズムが提供されます。 詳細については、「[方法 : カスタム ユーザー名とパスワード検証ツールを使用](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)する 」を参照してください。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM エンコードされた SOAP メッセージを使用する WSE 3.0 Web サービス  
 WSE 3 アプリケーションと同様に、WCF アプリケーションは、構成で MTOM メッセージ エンコーディングを指定できます。 この設定を移行するには、サービスのバインドに[\<mtomMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)を追加します。 WCF で同等のサービスに対して、WSE 3.0 で MTOM エンコードを指定する方法を次のコード例に示します。  
  
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

 クライアントと Web サービス間でやり取りされる XML に直接アクセスするために WSE メッセージング API が使用されている場合は、"Plain Old XML" (POX) を使用するようにアプリケーションを変換できます。 POX の詳細については、 [POX アプリケーションとの相互運用性](interoperability-with-pox-applications.md)を参照してください。 WSE メッセージング API の詳細については、「 [WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10))メッセージング API を使用した SOAP メッセージの送受信 」を参照してください。  
  
## <a name="transports"></a>トランスポート  
  
### <a name="tcp"></a>TCP  
 既定では、TCP トランスポートを使用して SOAP メッセージを送信する WSE 3.0 クライアントおよび Web サービスは、WCF クライアントおよび Web サービスと相互運用できません。 このような非互換性は、TCP プロトコルで使用されるフレームの違いとパフォーマンス上の理由に起因します。 ただし、WCF サンプルでは、WSE 3.0 と相互運用するカスタム TCP セッションを実装する方法について詳しく説明します。 このサンプルの詳細については、「[トランスポート: WSE 3.0 TCP 相互運用性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)」を参照してください。  
  
 WCF アプリケーションが TCP トランスポートを使用することを指定するには、 [ \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)を使用します。  
  
### <a name="custom-transport"></a>カスタム トランスポート  
 WCF の WSE 3.0 カスタム トランスポートと同等のチャネル拡張機能です。 チャネル拡張の作成の詳細については、[チャネル層の拡張を](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)参照してください。  
  
## <a name="see-also"></a>関連項目

- [基本的なプログラミング ライフサイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [方法 : SecurityBindingElement を使用してカスタム バインドを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [方法 : 指定した認証モード用の SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)

---
title: トランスポート セキュリティの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 04526e8aea09b412de4d3a94f17938b02ad6527b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105275"
---
# <a name="transport-security-overview"></a>トランスポート セキュリティの概要
トランスポート セキュリティ機構では、Windows Communication Foundation (WCF) は、バインドと使用されているトランスポートによって異なります。 たとえば、<xref:System.ServiceModel.WSHttpBinding> クラスを使用する場合、トランスポートは HTTP であり、トランスポートをセキュリティで保護するための主要機構は SSL (Secure Sockets Layer) over HTTP (一般に HTTPS と呼ばれます) です。 このトピックでは、WCF のシステム指定のバインディングで使用される主要なトランスポート セキュリティ機構について説明します。  
  
> [!NOTE]
>  .NET Framework 3.5 以降のバージョンと SSL セキュリティを使用する場合、WCF クライアントは両方、中間証明書を使用してその証明書ストアに、サービスの証明書チェーンの検証を実行する SSL ネゴシエーション中に受信した中間証明書証明書。 .NET Framework 3.0 では、ローカルの証明書ストアにインストールされている中間証明書のみが使用されます。  
  
> [!WARNING]
>  トランスポート セキュリティを使用した場合、<xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティが上書きされることがあります。 この設定に防ぐため、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType>に<xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>します。 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> は、サービスの説明で設定できる、サービスの動作です。  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 既定では、<xref:System.ServiceModel.BasicHttpBinding> クラスはセキュリティを提供しません。 このバインディングは、セキュリティを実装していない Web サービス プロバイダーとの相互運用性のためにデザインされています。 ただし、<xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.BasicHttpSecurityMode.None> 以外の値に設定することにより、セキュリティを有効にすることができます。 トランスポート セキュリティを有効にするには、このプロパティを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定します。  
  
### <a name="interoperation-with-iis"></a>IIS との相互運用性  
 <xref:System.ServiceModel.BasicHttpBinding> クラスは、主に既存の Web サービスと相互運用するために使用されます。これらのサービスの多くは、インターネット インフォメーション サービス (IIS) によってホストされます。 そのため、このバインディングのトランスポート セキュリティは、IIS サイトとシームレスに相互運用できるようにデザインされています。 IIS サイトと相互運用するには、セキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定した後、クライアント資格情報の種類を設定します。 資格情報の種類の値は、IIS ディレクトリのセキュリティ機構に対応しています。 モードを設定し、資格情報の種類を Windows に設定するコードを次に示します。 この構成は、クライアントとサーバーが同じ Windows ドメインに存在する場合に使用できます。  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 または、次のように構成します。  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 以下のセクションでは、その他のクライアント資格情報の種類について説明します。  
  
#### <a name="basic"></a>基本  
 これは、IIS の基本認証方法に対応しています。 このモードを使用する場合は、Windows ユーザー アカウントと、適切な NTFS ファイル システムのアクセス許可を使用して IIS サーバーを構成する必要があります。 詳細については[!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[Enabling Basic Authentication and Configuring the Realm Name](https://go.microsoft.com/fwlink/?LinkId=88592)します。 詳細については[!INCLUDE[iisver](../../../../includes/iisver-md.md)]を参照してください[IIS 7.0 Beta:基本認証を構成](https://go.microsoft.com/fwlink/?LinkId=88593)します。  
  
#### <a name="certificate"></a>証明書  
 IIS には、クライアントに証明書を使用してログオンすることを要求するオプションがあります。 この機能により、IIS はクライアント証明書を Windows アカウントにマップすることもできます。 詳細については[!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[Enabling Client Certificates in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88594)します。 詳細については[!INCLUDE[iisver](../../../../includes/iisver-md.md)]を参照してください[IIS 7.0 Beta:Configuring Server Certificates in IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595)します。  
  
#### <a name="digest"></a>Digest  
 ダイジェスト認証は基本認証と似ていますが、資格情報をクリア テキストではなくハッシュとして送信できるという利点があります。 詳細については[!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkID=88443)します。 詳細については[!INCLUDE[iisver](../../../../includes/iisver-md.md)]を参照してください[IIS 7.0 Beta:ダイジェスト認証を構成する](https://go.microsoft.com/fwlink/?LinkId=88596)します。  
  
#### <a name="windows"></a>Windows  
 これは、IIS の統合 Windows 認証に対応しています。 この値に設定する場合、サーバーは、Kerberos プロトコルを使用する Windows ドメインにドメイン コントローラーとして存在することにもなっています。 サーバーが Kerberos ベースのドメインに存在しない場合、または Kerberos システムに障害が発生した場合は、次のセクションで説明する NTLM (NT LAN Manager) 値を使用できます。 詳細については[!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[Integrated Windows Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88597)します。 詳細については[!INCLUDE[iisver](../../../../includes/iisver-md.md)]を参照してください[IIS 7.0 Beta:Configuring Server Certificates in IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595)します。  
  
#### <a name="ntlm"></a>NTLM  
 この値を使用すると、Kerberos プロトコルが失敗した場合に、サーバーは、NTLM を使用して認証を実行できます。 IIS の構成の詳細については[!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[強制的に NTLM 認証](https://go.microsoft.com/fwlink/?LinkId=88598)します。 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] では、Windows 認証に NTLM 認証が含まれます。 詳細については、次を参照してください[IIS 7.0 Beta:。Configuring Server Certificates in IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=88595)します。  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> クラスは、WS-* 仕様を実装するサービスと共に相互運用するようにデザインされています。 このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。 SSL を使用する WCF アプリケーションを作成するのにには、アプリケーションをホストするのに IIS を使用します。 自己ホスト型アプリケーションを作成する場合は、HttpCfg.exe ツールを使用して、X.509 証明書をコンピューターの特定のポートにバインドします。 ポート番号は、エンドポイント アドレスとして、WCF アプリケーションの一部として指定されます。 トランスポート モードを使用する場合は、エンドポイント アドレスに HTTPS プロトコルを含める必要があります。そうしないと、実行時に例外が発生します。 詳細については、次を参照してください。 [HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)します。  
  
 クライアント認証の場合、<xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> クラスの <xref:System.ServiceModel.HttpTransportSecurity> プロパティを <xref:System.ServiceModel.HttpClientCredentialType> 列挙値のいずれかに設定します。 この列挙値は、<xref:System.ServiceModel.BasicHttpBinding> のクライアント資格情報の種類と同一であり、IIS サービスを使用してホストされるようにデザインされています。  
  
 クライアント資格情報の種類が Windows の場合に使用するバインディングの例を次に示します。  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 このバインディングが提供するのは、トランスポート レベルのセキュリティではなく、メッセージ レベルのセキュリティだけです。  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> クラスは、メッセージ トランスポートに TCP を使用します。 トランスポート モードのセキュリティは、TLS (Transport Layer Security) over TCP を実装することによって実現されます。 TLS 実装は、オペレーティング システムによって提供されます。  
  
 次のコードに示すように、<xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> クラスの <xref:System.ServiceModel.TcpTransportSecurity> プロパティを <xref:System.ServiceModel.TcpClientCredentialType> 値のいずれかに設定することで、クライアントの資格情報の種類を指定することもできます。  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>クライアント  
 クライアントでは、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> メソッドを使用して証明書を指定する必要があります。  
  
> [!NOTE]
>  Windows セキュリティを使用している場合には、証明書は不要です。  
  
 証明書の拇印を使用するコードを次に示します。拇印により、証明書が一意に識別されます。 証明書の詳細については、「[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 または、証明書をクライアントの構成で指定を使用して、 [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) behaviors セクション内の要素。  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 同じネットワーク上の 2 台のコンピューター間に名前付きパイプ チャネルを作成できますが、<xref:System.ServiceModel.NetNamedPipeBinding> クラスは、コンピューター内通信 (つまり、同じコンピューター上で実行されるプロセス) を効率的に行うことができるようにデザインされています。 このバインディングが提供するのは、トランスポート レベルのセキュリティだけです。 このバインディングを使用してアプリケーションを作成する場合は、エンドポイント アドレスにプロトコルとして "net.pipe" を含める必要があります。  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 トランスポート セキュリティを使用する場合、このバインディングでは SSL over HTTP を使用します。SSL over HTTP は HTTPS とも呼ばれ、発行済みトークン (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>) を含みます。 フェデレーション アプリケーションの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> クラスは、ピアツーピア ネットワーク機能を使用して効率的に通信できるようにデザインされた、セキュリティ保護されたトランスポートです。 クラスとバインディングの名前が示すように、プロトコルは TCP です。 セキュリティ モードが Transport に設定されている場合、このバインディングは TLS over TCP を実装します。 ピア ツー ピア機能の詳細については、次を参照してください。[ピア ツー ピア ネットワー キング](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)します。  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding と NetMsmqBinding  
 トランスポートの詳細についてはセキュリティとメッセージ キュー (MSMQ と呼ばれる以前) を参照してください[トランスポート セキュリティを使用してメッセージをセキュリティで保護する](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)します。  
  
## <a name="see-also"></a>関連項目

- [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)

---
title: 資格情報の種類の選択
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 20c070e9351219a649735ac404231cf6f265d814
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586123"
---
# <a name="selecting-a-credential-type"></a>資格情報の種類の選択
*資格情報* とはWindows Communication Foundation (WCF) が要求された身分証明または資格を確立するために使用するデータです。 たとえば、パスポートは、政府によって発行される、国籍または地域籍を証明するための資格情報です。 WCF では、資格情報は、ユーザー名トークンと X.509 証明書などのさまざまな形式を実行できます。 このトピックでは、資格情報、WCF では、使用する方法と、アプリケーションの適切な資格情報を選択する方法について説明します。  
  
 多くの国や地域において、運転免許証は資格情報の一例です。 運転免許証には、個人を識別する情報や能力を表すデータが記載されます。 この免許証には、所有者の写真という形式で所有の証明が含まれています。 免許証は、政府機関など、信頼された証明機関によって発行されます。 免許証には発行機関印が押され (国や地域によってはホログラムが使用され) ており、これによって、改ざんあるいは偽造されたものではないことが示されています。  
  
 資格情報の提示には、データ自体の提示とデータの所有証明の提示が関与します。 WCF では、さまざまなトランスポートとメッセージの両方のセキュリティ レベルで資格情報の種類をサポートしています。 たとえば、2 つの種類の WCF ではサポートされている資格情報: ユーザー名と (X.509) 証明書します。  
  
 ユーザー名資格情報で、ユーザー名はクレームされた ID を表しており、パスワードは所有の証明に使用されます。 この場合の信頼された証明機関とは、ユーザー名とパスワードを検証するシステムです。  
  
 X.509 証明書資格情報でサブジェクト名、サブジェクト代替名、または証明書内の特定のフィールドとして使用できます、他のフィールドの id のクレームなど、`Valid From`と`Valid To`フィールドで、指定の有効性、証明書。  
  
## <a name="transport-credential-types"></a>トランスポート資格情報の種類  
 転送セキュリティ モードのバインディングによって使用できるクライアント資格情報の種類を次の表に示します。 サービスを作成する際には、`ClientCredentialType` プロパティを次のいずれかの値に設定し、クライアントがサービスと通信するときに提供する必要がある資格情報の種類を指定します。 この種類は、コードまたは構成ファイルで設定できます。  
  
|設定|説明|  
|-------------|-----------------|  
|なし|クライアントが資格情報を提示する必要がないことを指定します。 匿名クライアントであると解釈されます。|  
|Basic|クライアントに基本認証を指定します。 詳細については、RFC2617 を参照してください。-[HTTP 認証。基本認証とダイジェスト認証](https://go.microsoft.com/fwlink/?LinkID=88313)」を参照してください。|  
|Digest|クライアントにダイジェスト認証を指定します。 詳細については、RFC2617 を参照してください。-[HTTP 認証。基本認証とダイジェスト認証](https://go.microsoft.com/fwlink/?LinkID=88313)」を参照してください。|  
|Ntlm|NT LAN Manager (NTLM) 認証を指定します。 これは、何らかの理由で Kerberos 認証を使用できないときに使用されます。 設定して、フォールバックとしての使用を無効にすることもできます、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>プロパティを`false`、これにより、WCF に NTLM を使用する場合に例外をスローするベスト エフォートです。 ただし、このプロパティを `false` に設定しても、ネットワーク経由で NTLM 資格情報が送信されなくなるとは限りません。|  
|Windows|Windows 認証を指定します。 Windows ドメインで Kerberos プロトコルだけを指定するには、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> プロパティを `false` (既定値は `true`) に設定する必要があります。|  
|証明書|X.509 証明書を使用したクライアント認証を実行します。|  
|[Password]|ユーザーは、ユーザー名とパスワードを提供する必要があります。 Windows 認証または他のカスタム ソリューションを使用して、ユーザー名とパスワードの組み合わせを検証します。|  
  
### <a name="message-client-credential-types"></a>メッセージ クライアント資格情報の種類  
 メッセージ セキュリティを使用するアプリケーションを作成するときに使用できる資格情報の種類を次の表に示します。 これらの値は、コードまたは構成ファイルで使用できます。  
  
|設定|説明|  
|-------------|-----------------|  
|なし|クライアントが資格情報を提示する必要がないことを指定します。 匿名クライアントであると解釈されます。|  
|Windows|Windows 資格情報によって確立されたセキュリティ コンテキストで、SOAP メッセージ交換を実行できます。|  
|[ユーザー名]|ユーザー名資格情報を使用したクライアントの認証をサービスで要求できるようにします。 WCF での署名の生成やデータの暗号化などのユーザー名と暗号化操作を許可しないことに注意してください。 WCF によりユーザー名資格情報を使用する場合に、トランスポートがセキュリティで保護されるようになります。|  
|証明書|X.509 証明書を使用したクライアントの認証をサービスで要求できるようにします。|  
|IssuedToken|セキュリティ ポリシーに従って構成されるカスタム トークンです。 既定のトークンの種類は、SAML (Security Assertion Markup Language) です。 トークンは、セキュリティ トークン サービスによって発行されます。 詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。|  
  
### <a name="negotiation-model-of-service-credentials"></a>サービス資格情報のネゴシエーション モデル  
 *ネゴシエーション*は資格情報を交換することで、クライアントとサービス間の信頼を確立するプロセスです。 このプロセスは、ネゴシエーション プロセスの次の手順に必要な情報だけを公開するために、クライアントとサービスとの間で反復して実行されます。 実際には、最後に、後続の操作で使用されるサービスの資格情報がクライアントに配信されます。  
  
 1 つの例外を除き、既定では WCF では、システム指定のバインディング、サービス資格情報自動的にネゴシエート メッセージ レベルのセキュリティを使用する場合。 (例外とは、<xref:System.ServiceModel.BasicHttpBinding> の場合です。このバインディングでは、既定ではセキュリティが有効化されません)。この動作を無効にするには、<xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティと <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティを参照してください。  
  
> [!NOTE]
>  WCF クライアントがその証明書ストア内の中間証明書と SSL ネゴシエーション中に受信した中間証明書の両方を使用して、サービスの証明書チェーンの検証を実行する .NET Framework 3.5 以降のバージョンと SSL セキュリティを使用する場合証明書。 .NET Framework 3.0 では、ローカルの証明書ストアにインストールされている中間証明書のみが使用されます。  
  
#### <a name="out-of-band-negotiation"></a>帯域外ネゴシエーション  
 自動ネゴシエーションを無効にした場合、サービスにメッセージを送信する前にクライアント側にサービス資格情報が準備されている必要があります。 これとも呼ばれる、*帯域外の*プロビジョニングします。 たとえば、指定された資格情報の種類が証明書で、自動ネゴシエーションが無効の場合、クライアントはサービス所有者に連絡し、証明書を受け取って、クライアント アプリケーションを実行しているコンピューターにインストールする必要があります。 この方法は、たとえば B2B シナリオで、サービスにアクセスできるクライアントを厳密に制御することが必要な場合に使用される可能性があります。 電子メールで、このアウト-の-域外ネゴシエーションを実行でき、X.509 証明書は、Microsoft 管理コンソール (MMC) の証明書スナップインなどのツールを使用して Windows 証明書ストアに格納します。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティを使用して、帯域外ネゴシエーションによって取得した証明書をサービスに提供します。 バインディングでは自動ネゴシエーションが許可されないので、<xref:System.ServiceModel.BasicHttpBinding> クラスを使用するときはこの操作が必要になります。 このプロパティは、相関関係のない双方向シナリオでも使用します。 このシナリオでは、クライアントが先にサーバーへの要求を送信する必要がなく、サーバーからクライアントにメッセージが送信されます。 サーバーにはクライアントからの要求がないので、サーバーはクライアントの証明書を使用して、クライアントへのメッセージを暗号化する必要があります。  
  
## <a name="setting-credential-values"></a>資格情報の値の設定  
 セキュリティ モードを選択したら、実際の資格情報を指定する必要があります。 たとえば、資格情報の種類を "Certificate" に設定した場合、特定の資格情報 (特定の X.509 証明書など) をサービスまたはクライアントに関連付ける必要があります。  
  
 サービスをプログラミングしている場合とクライアントをプログラミングしている場合で、資格情報の値を設定する方法が少し異なります。  
  
### <a name="setting-service-credentials"></a>サービス資格情報の設定  
 トランスポート モードを使用し、HTTP をトランスポートとして使用する場合は、インターネット インフォメーション サービス (IIS) を使用するか、証明書でポートを構成する必要があります。 詳細については、次を参照してください。[トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)と[HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)します。  
  
 コードで資格情報をサービスに提供するには、<xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成し、<xref:System.ServiceModel.Description.ServiceCredentials> プロパティからアクセスできる <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> クラスを使用して適切な資格情報を指定します。  
  
#### <a name="setting-a-certificate"></a>証明書の設定  
 クライアントに対するサービスの認証に使用される X.509 証明書をサービスに提供するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> メソッドを使用します。  
  
 クライアント証明書をサービスに提供するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> メソッドを使用します。  
  
#### <a name="setting-windows-credentials"></a>Windows 資格情報の設定  
 クライアントが有効なユーザー名とパスワードを指定した場合、その資格情報がクライアントの認証に使用されます。 それ以外の場合は、現在ログオンしているユーザーの資格情報が使用されます。  
  
### <a name="setting-client-credentials"></a>クライアント資格情報の設定  
 WCF では、クライアント アプリケーションは、サービスに接続する WCF クライアントを使用します。 各クライアントは、<xref:System.ServiceModel.ClientBase%601> クラスから派生しています。各クライアントでは <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティを使用して、クライアント資格情報のさまざまな値を指定できます。  
  
#### <a name="setting-a-certificate"></a>証明書の設定  
 サービスに対するクライアントの認証に使用される X.509 証明書をサービスに提供するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> メソッドを使用します。  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>サービスに対するクライアントの認証でのクライアント資格情報の使用  
 サービスとの通信に必要なクライアント資格情報は、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティまたは <xref:System.ServiceModel.ChannelFactory.Credentials%2A> プロパティを使用して提供されます。 この情報は、サービスに対してクライアントを認証するためにセキュリティ チャネルで使用されます。 認証は、次のいずれかの方法で実行されます。  
  
- クライアントの資格情報は、最初のメッセージを送信すると、WCF クライアントのインスタンスを使用してセキュリティ コンテキストを確立する前に 1 回使用されます。 アプリケーション メッセージはすべて、そのセキュリティ コンテキストで保護されます。  
  
- サービスに送信されたアプリケーション メッセージごとの認証に、クライアント資格情報を使用します。 この場合、クライアントとサービスとの間にコンテキストは確立されません。  
  
### <a name="established-identities-cannot-be-changed"></a>変更できない確立された ID  
 1 つ目の方法を使用した場合、確立されたコンテキストは、クライアント ID に永続的に関連付けられます。 つまり、セキュリティ コンテキストが確立されると、クライアントに関連付けられた ID を変更できません。  
  
> [!IMPORTANT]
>  ID の切り替えができないこと (つまり、セキュリティ コンテキストを確立する場合の既定の動作) について、注意が必要な状況があります。 別のサービスと通信するサービスを作成する場合、2 番目のサービスの WCF クライアントを開くために使用する id を変更できません。 これは、複数のクライアントが最初のサービスを使用できる状況で、2 番目のサービスにアクセスするときに最初のサービスがクライアントを偽装する場合、問題になります。 サービスがすべての呼び出し元に対して同じクライアントを再利用する場合、2 番目のサービスへの呼び出しはすべて、2 番目のサービスに対してクライアントを開くために使用した最初の呼び出し元の ID によって実行されます。 つまり、このサービスでは、すべてのクライアントが 2 番目のサービスと通信できるように、最初のクライアントの ID が使用されます。 これによって、権限の昇格が発生する可能性があります。 これがサービスの目的の動作でない場合、各呼び出し元を追跡し、その呼び出し元ごとに 2 番目のサービスに対する新しいクライアントを作成する必要があります。これによって、適切な呼び出し元が 2 番目のサービスと通信するために、サービスは適切なクライアントだけを使用できます。  
  
 資格情報とセキュリティで保護されたセッションの詳細については、次を参照してください。[セキュリティで保護されたセッションに関するセキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [セキュリティの概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)

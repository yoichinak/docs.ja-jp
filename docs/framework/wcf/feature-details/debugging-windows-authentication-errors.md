---
title: Windows 認証エラーのデバッグ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: a68a291b1974e86c9a4f16f9d90a879649076533
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595137"
---
# <a name="debugging-windows-authentication-errors"></a>Windows 認証エラーのデバッグ
セキュリティ機構として Windows 認証を使用する場合、セキュリティ サポート プロバイダー インターフェイス (SSPI: Security Support Provider Interface) がセキュリティ プロセスを処理します。 SSPI 層でセキュリティ エラーが発生すると、Windows Communication Foundation (WCF) によってが表示されます。 このトピックでは、エラーの診断に役立つフレームワークと一連の質問を示します。  
  
 Kerberos プロトコルの概要については、[Kerberos](https://go.microsoft.com/fwlink/?LinkID=86946)、SSPI の概要を参照してください。 [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941)を参照してください。  
  
 WCF の通常の使用、Windows 認証のため、*ネゴシエート*クライアントとサービス間の Kerberos 相互認証を実行するセキュリティ サポート プロバイダー (SSP)、します。 場合は、Kerberos プロトコルは、WCF はフォールバック NT LAN Manager (NTLM) を既定で、ご利用いただけません。 ただし、WCF、Kerberos プロトコルのみを使用する (および Kerberos が使用できない場合に例外をスローする) を構成できます。 Kerberos プロトコルの制限付きの形式を使用する WCF を構成することもできます。  
  
## <a name="debugging-methodology"></a>デバッグ方法  
 基本的な方法は次のとおりです。  
  
1.  Windows 認証を使用しているかどうかを確認します。 他の方式を使用している場合には、このトピックは該当しません。  
  
2.  Windows 認証を使用している場合は、WCF 構成で Kerberos ダイレクトまたはネゴシエートを使用するかどうかを決定します。  
  
3.  構成で Kerberos プロトコルと NTLM のどちらを使用しているかを確認した後は、現在のコンテキストでのエラー メッセージを理解できます。  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Kerberos プロトコルと NTLM の可用性  
 Kerberos SSP は、Kerberos キー配布センター (KDC: Key Distribution Center) として機能するドメイン コントローラーを必要とします。 Kerberos プロトコルを使用できるのは、クライアントとサービスの両方がドメイン ID を使用している場合だけです。 次の表に示すように、アカウントの他の組み合わせでは NTLM が使用されます。  
  
 この表の列見出しは、サーバーが使用すると考えられるアカウントの種類を示します。 左の列は、クライアントが使用すると考えられるアカウントの種類を示します。  
  
||Local User|ローカル システム|Domain User|Domain Machine|  
|-|----------------|------------------|-----------------|--------------------|  
|Local User|NTLM|NTLM|NTLM|NTLM|  
|ローカル システム|匿名 NTLM|匿名 NTLM|匿名 NTLM|匿名 NTLM|  
|Domain User|NTLM|NTLM|Kerberos|Kerberos|  
|Domain Machine|NTLM|NTLM|Kerberos|Kerberos|  
  
 具体的には、次の 4 種類のアカウントがあります。  
  
-   ローカル ユーザー:コンピューター専用のユーザー プロファイル。 例 : `MachineName\Administrator` または `MachineName\ProfileName`。  
  
-   ローカル システム:ドメインに参加していないコンピューターのビルトイン アカウント システム。  
  
-   ドメイン ユーザー:Windows ドメイン ユーザー アカウント。 たとえば、`DomainName\ProfileName` のように指定します。  
  
-   Domain Machine:マシン id の Windows ドメインに参加しているコンピューターで実行されているプロセスです。 たとえば、`MachineName\Network Service` のように指定します。  
  
> [!NOTE]
>  サービス資格情報は、<xref:System.ServiceModel.ICommunicationObject.Open%2A> クラスの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されたときにキャプチャされます。 クライアント資格情報は、クライアントがメッセージを送信するたびに読み取られます。  
  
## <a name="common-windows-authentication-problems"></a>Windows 認証の一般的な問題  
 ここでは、Windows 認証に関するいくつかの一般的な問題と、考えられる解決策について説明します。  
  
### <a name="kerberos-protocol"></a>Kerberos プロトコル  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Kerberos プロトコルでの SPN と UPN の問題  
 Windows 認証を使用し、SSPI が Kerberos プロトコルを使用またはネゴシエートする場合、クライアント エンドポイントが使用する URL には、サービス URL 内のサービスのホストの完全修飾ドメイン名が含まれている必要があります。 これは、サービスが実行されているアカウントが Active Directory ドメインでサービスを実行してこれは最も一般的に、コンピューターが追加されたときに作成されるコンピューター (既定値) のサービス プリンシパル名 (SPN) キーにアクセスを前提としています、ネットワーク サービス アカウント。 サービスがコンピューターの SPN キーにアクセスできない場合は、クライアントのエンドポイント ID でサービスを実行しているアカウントの正しい SPN またはユーザー プリンシパル名 (UPN: User Principal Name) を指定する必要があります。 SPN と UPN と WCF のしくみについての詳細については、[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)を参照してください。  
  
 Web ファームや Web ガーデンなどの負荷分散シナリオでは、各アプリケーションに一意のアカウントを定義し、そのアカウントに SPN を割り当て、アプリケーションのサービスすべてがそのアカウントで実行されるようにするのが一般的です。  
  
 サービスのアカウント用の SPN を取得するには、Active Directory ドメイン管理者である必要があります。 詳細については、[Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkID=88330)を参照してください。  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Kerberos プロトコル ダイレクトでは Domain Machine アカウントでサービスを実行する必要がある  
 この状況は、次のコードに示すように、`ClientCredentialType` プロパティが `Windows` に設定され、<xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティが `false` に設定されている場合に発生します。  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 これを解決するには、ドメインに参加しているコンピューターで、Domain Machine アカウント (Network Service など) を使用してサービスを実行します。  
  
### <a name="delegation-requires-credential-negotiation"></a>委任には資格情報ネゴシエーションが必要  
 委任で Kerberos 認証プロトコルを使用するには、資格情報ネゴシエーションを使用する Kerberos プロトコル ("マルチレッグ" Kerberos または "マルチステップ" Kerberos とも呼ばれます) を実装する必要があります。 資格情報ネゴシエーションを使用しない Kerberos 認証 ("ワンショット" Kerberos または "シングルレッグ" Kerberos とも呼ばれます) を実装した場合は、例外がスローされます。  
  
 資格情報ネゴシエーションを使用する Kerberos を実装するには、次の手順を実行します。  
  
1.  <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> を <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> に設定して委任を実装します。  
  
2.  次のような SSPI ネゴシエーションが必要です。  
  
    1.  標準バインディングを使用する場合は、`NegotiateServiceCredential` プロパティを `true` に設定します。  
  
    2.  カスタム バインドを使用する場合は、`AuthenticationMode` 要素の `Security` 属性を `SspiNegotiated` に設定します。  
  
3.  次のように、NTLM を使用できないようにすることで、SSPI ネゴシエーションで Kerberos を使用する必要があります。  
  
    1.  NTLM を使用できないようにするには、コードで `ChannelFactory.Credentials.Windows.AllowNtlm = false` ステートメントを使用します。  
  
    2.  構成ファイルで `allowNtlm` 属性を `false` に設定することもできます。 この属性に含まれている、 [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)します。  
  
### <a name="ntlm-protocol"></a>NTLM プロトコル  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>ネゴシエート SSP は NTLM にフォールバックするが、NTLM が無効になっている  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>プロパティに設定されて`false`、それが原因で NTLM が使用されている場合に例外をスローする最善の努力をするように、Windows Communication Foundation (WCF)。 ただし、このプロパティを `false` に設定しても、ネットワーク経由で NTLM 資格情報が送信されなくなるとは限りません。  
  
 NTLM へのフォールバックを無効にする方法を次に示します。  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>NTLM ログオンが失敗する  
 サービスで、クライアント資格情報が無効です。 ユーザー名とパスワードが正しく設定されており、サービスを実行しているコンピューターに認識されているアカウントに対応していることを確認します。 NTLM では、指定された資格情報を使用してサービスのコンピューターにログオンします。 資格情報がクライアントを実行しているコンピューターで有効であっても、サービスのコンピューターでは無効な場合、このログオンは失敗します。  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>匿名 NTLM ログオンが発生するが、既定では匿名ログオンが無効になっている  
 次の例に示すように、クライアントの作成時に、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> プロパティを <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> に設定します。ただし、既定では、サーバーは匿名ログオンを許可しません。 これは、<xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> クラスの <xref:System.ServiceModel.Security.WindowsServiceCredential> プロパティの既定値が `false` であるためです。  
  
 匿名ログオンを有効にすることを試みるクライアント コードを次に示します (既定のプロパティは `Identification` です)。  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 サーバーによって匿名ログオンを有効にするように既定値を変更するサービス コードを次に示します。  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 権限借用の詳細については、[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)を参照してください。  
  
 もう 1 つの方法として、SYSTEM ビルトイン アカウントを使用する Windows サービスとしてクライアントを実行します。  
  
### <a name="other-problems"></a>その他の問題  
  
#### <a name="client-credentials-are-not-set-correctly"></a>クライアント資格情報が正しく設定されていない  
 Windows 認証では、<xref:System.ServiceModel.Security.WindowsClientCredential> ではなく、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティによって返された <xref:System.ServiceModel.Security.UserNamePasswordClientCredential> インスタンスを使用します。 誤りのあるコード例を次に示します。  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 正しいコード例を次に示します。  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI を使用できない  
 次のオペレーティング システムでは、Windows 認証サーバーとして使用する場合はサポートされません。[!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition、 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition、および[!INCLUDE[wv](../../../../includes/wv-md.md)]Home edition。  
  
#### <a name="developing-and-deploying-with-different-identities"></a>異なる ID を使用した開発と展開  
 アプリケーションを 1 台のコンピューターで開発し、別のコンピューターに展開し、異なるアカウントの種類を使用して各コンピューターで認証を行う場合、動作の違いが発生する場合があります。 たとえば、`SSPI Negotiated` 認証モードを使用して Windows XP Professional コンピューターでアプリケーションを開発するとします。 ローカル ユーザー アカウントを使用して認証する場合は、NTLM プロトコルが使用されます。 アプリケーションを開発した後は、ドメイン アカウントで実行されるサービスを Windows Server 2003 コンピューターに展開します。 この時点で、クライアントは Kerberos とドメイン コントローラーを使用するため、このサービスを認証できなくなります。  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [サポートされていないシナリオ:](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)

---
title: サービスのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: 65d4f2858c2be4c2a6872f96ef3739bb16253d74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157678"
---
# <a name="securing-services"></a>サービスのセキュリティ保護
Windows Communication Foundation (WCF) サービスのセキュリティは、2 つの主要要件で構成されます。 転送セキュリティと承認します。 (3 番目の要件は、「セキュリティのイベントの監査[監査](../../../docs/framework/wcf/feature-details/auditing-security-events.md))。簡単に説明すると、転送セキュリティは、認証 (サーバーとクライアント両方の ID の検証)、機密性 (メッセージの暗号化)、および整合性 (改ざんを検出するためのデジタル署名) で構成されます。 承認は、たとえば、特権のあるユーザーだけがファイルを読み取ることができるなど、リソースへのアクセスを制御することです。 WCF の機能を使用して、2 つの主な要件を簡単に実装します。  
  
 例外として、<xref:System.ServiceModel.BasicHttpBinding>クラス (または[ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)構成内の要素)、転送セキュリティは、すべての定義済みバインディングの既定で有効です。 このセクションのトピックでは、2 つの基本的なシナリオ、インターネット インフォメーション サービス (IIS) でホストされるイントラネット サービス上で転送セキュリティと承認を実装するシナリオと、IIS でホストされるサービス上で転送セキュリティと承認を実装するシナリオについて説明します。  
  
> [!NOTE]
>  Windows XP Home では、Windows 認証をサポートしていません。 このため、このシステムではサービスを実行しないでください。  
  
## <a name="security-basics"></a>セキュリティの基礎  
 セキュリティは、 *資格情報*に依存します。 資格情報は、エンティティが本物であることを証明します (、*エンティティ*人、ソフトウェア プロセス、会社、または承認できるものにすることができます)。たとえば、サービスのクライアントと、*要求*の*identity*、資格情報によってなんらかの方法では、そのクレームを証明し、。 通常のシナリオでは、資格情報の交換が行われます。 最初に、サービスがその ID のクレームを作成し、資格情報を使用してクライアントにそのクレームを証明します。 次に、クライアントが ID のクレームを作成し、サービスに資格情報を提示します。 両方がお互いの資格情報を信頼した場合、 *セキュリティで保護されたコンテキスト* を確立できます。このコンテキストでは、すべてのメッセージは機密性が保護された状態で交換され、すべてのメッセージはその整合性を保護するために署名されます。 サービスはクライアントの ID を確立した後で、クライアントの資格情報のクレームをグループの *ロール* または *メンバーシップ* に適合できます。 いずれの場合も、クライアントが属するロールまたはグループを使用して、サービスは、そのクライアントがロール特権またはグループ特権に基づいて限られた操作を実行することを *承認* します。  
  
## <a name="windows-security-mechanisms"></a>Windows セキュリティ機構  
 クライアントとサービスのコンピューターが、両方がネットワークにログオンする必要がある Windows ドメインに存在する場合、資格情報は Windows インフラストラクチャによって提供されます。 この場合、コンピューターのユーザーがネットワークにログオンすると資格情報が確立されます。 ネットワーク上の各ユーザーおよび各コンピューターは、信頼されたユーザーおよびコンピューターの集合に属することを検証される必要があります。 Windows システムでは、このようなユーザーとコンピューターは、 *セキュリティ プリンシパル*とも呼ばれます。  
  
 *Kerberos* コントローラーによるサポートがある Windows ドメインでは、Kerberos コントローラーは、チケットを各セキュリティ プリンシパルに付与することをベースにしたスキームを使用します。 コントローラーによって付与されたチケットは、システムの他のチケット付与システムによって信頼されます。 エンティティが何らかの操作を実行しようとしたり、コンピューター上のファイルやディレクトリなどの *リソース* にアクセスしようとしたりすると、その都度チケットの有効性が検査され、検査に合格した場合、プリンシパルに操作用の別のチケットが付与されます。 このチケットの付与方法は、操作ごとにプリンシパルを検証する方法よりも効率的です。  
  
 Windows ドメインで従来より使用されている安全性が低い機構に、NT LAN Manager (NTLM) があります。 Kerberos を使用できない場合 (通常、ワークグループなどの Windows ドメインの外部)、代わりに NTLM を使用できます。 NTLM は、IIS のセキュリティ オプションとしても使用できます。  
  
 Windows システムでは、各コンピューターとユーザーにロールとグループのセットを割り当てることによって承認が機能します。 たとえば、各 Windows コンピューターは、 *管理者*のロールに属するユーザー (またはユーザー グループ) がセットアップし、管理する必要があります。 もう 1 つのロールは、 *ユーザー*のロールです。このロールのアクセス許可は、管理者ロールより制限されます。 ロール以外に、ユーザーはグループにも割り当てられます。 グループによって、複数のユーザーが同じロールで動作できます。 このため、実際 Windows コンピューターは、ユーザーをグループに割り当てることによって管理されます。 たとえば、複数のユーザーをコンピューターのユーザー グループに割り当て、限られた人数のユーザーを管理者グループに割り当てることができます。 ローカル コンピューターでは、管理者は新しいグループを作成して、他のユーザー (または他のグループ) をそのグループに割り当てることもできます。  
  
 Windows を実行しているコンピューターでは、ディレクトリの各フォルダーを保護できます。 つまり、フォルダーを選択して、そのフォルダーのファイルにアクセスできるユーザー、およびそのユーザーがファイルのコピー、ファイルの変更 (最大限の特権が与えられている場合)、ファイルの削除、またはフォルダーへのファイルの追加を実行できるかどうかを制御できます。 これは、アクセス制御と呼ばれ、その機構はアクセス制御リスト (ACL) と呼ばれます。 ACL を作成するとき、アクセス権を 1 つまたは複数のグループおよびドメインの個別のメンバーに割り当てることができます。  
  
 WCF インフラストラクチャは、これらの Windows セキュリティ メカニズムを使用して設計されています。 したがって、イントラネットに展開するサービスを作成していて、そのクライアントを Windows ドメインのメンバーに限定する場合、セキュリティを簡単に実装できます。 有効なユーザーだけがドメインにログオンできます。 ログオン後、Kerberos コントローラーによって、各ユーザーは他のコンピューターまたはアプリケーションとの間にセキュリティで保護されたコンテキストを確立できます。 ローカル コンピューターでは、グループを簡単に作成でき、特定のフォルダーを保護する場合、そのグループを使用してローカル コンピューター上でアクセス権を割り当てることができます。  
  
## <a name="implementing-windows-security-on-intranet-services"></a>イントラネット サービスでの Windows セキュリティの実装  
 Windows ドメインでのみ実行するアプリケーションをセキュリティで保護するには、 <xref:System.ServiceModel.WSHttpBinding> または <xref:System.ServiceModel.NetTcpBinding> バインディングの既定のセキュリティ設定を使用できます。 既定では、だれでも、同じ Windows ドメイン WCF サービスにアクセスできます。 ドメイン内にいるユーザーは、ネットワークにログオン済みなので信頼できます。 サービスとクライアントの間で交換されるメッセージは、機密性を保護するために暗号化され、整合性を保護するために署名されます。 Windows セキュリティを使用するサービスを作成する方法の詳細については、次を参照してください。[方法。Windows 資格情報でサービスをセキュリティで保護された](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)します。  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>PrincipalPermissionAttribute クラスを使用した承認  
 コンピューター上のリソースへのアクセスを制限する必要がある場合、最も簡単な方法は <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを使用することです。 この属性を使用すると、ユーザーが指定の Windows グループまたはロールに属しているか、特定のユーザーであることを要求して、サービス操作の呼び出しを制限できます。 詳細については、「[方法 :PrincipalPermissionAttribute クラスでアクセスを制限する](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)します。  
  
### <a name="impersonation"></a>偽装  
 偽装は、リソース アクセスの制御に使用できるもう 1 つの機構です。 既定では、IIS でホストされるサービスは、ASPNET アカウントの ID で実行されます。 ASPNET アカウントは、アクセス許可のあるリソースにだけアクセスできます。 ただし、ASPNET サービス アカウントを除外し、他の特定の ID によるフォルダーへのアクセスを許可するように ACL を設定できます。 ここで問題となるのが、ASPNET アカウントがフォルダーにアクセスできない場合に、他のユーザーがフォルダーにアクセスできるようにする方法です。 これは、偽装を使用することで解決できます。偽装によって、サービスは特定のリソースにアクセスするためにクライアントの資格情報を使用できます。 もう 1 つの例は、特定のユーザーだけがアクセス許可を持つ SQL Server データベースにアクセスする場合です。 権限借用の使用に関する詳細については、次を参照してください。[方法。サービスのクライアントを偽装](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)と[委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)します。  
  
## <a name="security-on-the-internet"></a>インターネット上のセキュリティ  
 インターネット上のセキュリティは、イントラネット上のセキュリティと同じ要件で構成されます。 サービスは、信頼性を証明するために資格情報を提示する必要があり、クライアントは、サービスに対して ID を証明する必要があります。 クライアントの ID が証明されると、サービスは、クライアントによるリソースへのアクセスを制御できます。 ただし、インターネットではさまざまな種類が混在しているので、提示される資格情報は、Windows ドメインで使用される資格情報とは異なります。 Kerberos コントローラーが資格情報のチケットを使用して、ドメインでユーザーの認証を処理するのに対し、インターネットでは、サービスとクライアントは、資格情報を提示するための複数の異なる方法のいずれかに依存します。 このトピックの目的は、インターネットでアクセス可能な WCF サービスを作成することができる一般的なアプローチを提示するただしです。  
  
### <a name="using-iis-and-aspnet"></a>IIS と ASP.NET の使用  
 インターネット セキュリティの要件、およびその問題を解決するための機構は、新しいものではありません。 IIS はこの問題に対応する多くのセキュリティ機能があり、インターネット用の Microsoft の Web サーバーさらに、 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] WCF サービスを使用できるセキュリティ機能が含まれています。 これらのセキュリティ機能を利用するには、IIS で、WCF サービスをホストします。  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>ASP.NET メンバーシップとロール プロバイダーの使用  
 ASP.NET には、メンバーシップとロール プロバイダーが用意されています。 プロバイダーは、呼び出し元を認証するためのユーザー名とパスワードの組み合わせのデータベースであり、これによって、各呼び出し元のアクセス特権を指定することもできます。 Wcf では、既存のメンバーシップとロール プロバイダーの構成を簡単に使用できます。 この機能を示すサンプル アプリケーションについては、「 [Membership and Role Provider](../../../docs/framework/wcf/samples/membership-and-role-provider.md) 」のサンプルを参照してください。  
  
### <a name="credentials-used-by-iis"></a>IIS で使用する資格情報  
 Kerberos コントローラーによるサポートがある Windows ドメインとは異なり、インターネットには、随時ログオンしている多数のユーザーを管理するための共通のコントローラーがありません。 代わりに、インターネットの資格情報は、ほとんどの場合、X.509 証明書 (SSL (Secure Sockets Layer) 証明書とも呼ばれる) の形で提示されます。 この証明書は、通常、 *証明機関*によって発行されます。この証明機関は、証明書の信頼性を保証するサードパーティの企業および証明書が発行された個人です。 インターネット上にサービスを公開するには、このような信頼された証明書を提供して、サービスを認証する必要があります。  
  
 それでは、どのように信頼された証明書を取得するのでしょうか。 その方法の 1 つは、サービスを展開する準備とそのサービスの証明書を購入する準備ができたら、Authenticode、VeriSign などのサードパーティ証明機関に連絡する方法です。 ただし、WCF を使用した開発フェーズでは、まだ準備ができていません証明書を購入する、ツールと手法の存在する X.509 証明書を作成する場合は、運用環境のデプロイをシミュレートするために使用できます。 詳細については、次を参照してください。 [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md)します。  
  
## <a name="security-modes"></a>セキュリティ モード  
 WCF セキュリティのプログラミングには、いくつかの重要な意思決定ポイントする必要があります。 最も基本的な決定の 1 つは、 *セキュリティ モード*を選択することです。 2 つの主要なセキュリティ モードとして、 *トランスポート モード* と *メッセージ モード*があります。  
  
 3 番目のモードは、2 つの主要モードのセマンティクスを組み合わせたもので、 *メッセージ資格情報付きトランスポート モード*です。  
  
 セキュリティ モードによって、メッセージをセキュリティで保護する方法が決まります。それぞれのモードには、次に示す利点と欠点があります。 セキュリティ モードを設定する方法についての詳細については、次を参照してください。[方法。セキュリティ モードを設定](../../../docs/framework/wcf/how-to-set-the-security-mode.md)します。  
  
#### <a name="transport-mode"></a>トランスポート モード  
 ネットワークとアプリケーションの間には複数の層があります。 この層の 1 つが *トランスポート* 層で *、* エンドポイント間のメッセージ転送を管理します。 存在するために、これは WCF がそれぞれのメッセージの転送をセキュリティで保護できる、いくつかのトランスポート プロトコルを使用することを理解することが必要です。 (トランスポートの詳細については、次を参照してください[トランスポート](../../../docs/framework/wcf/feature-details/transports.md)。)。  
  
 一般的に使用されるプロトコルは HTTP ですが、その他にも TCP があります。 この各プロトコルは、プロトコルに固有の機構によってメッセージ転送をセキュリティで保護できます。 たとえば、HTTP プロトコルは SSL over HTTP (一般的に "HTTPS" と省略される) を使用してセキュリティで保護されます。 そのため、セキュリティのトランスポート モードを選択するときは、同時に、プロトコルによって指定された機構の使用を選択することになります。 たとえば、 <xref:System.ServiceModel.WSHttpBinding> クラスを選択し、そのセキュリティ モードをトランスポートに設定した場合、セキュリティ機構として SSL over HTTP (HTTPS) を選択することになります。 トランスポート モードの利点は、セキュリティが比較的低いレベルで統合されるので、メッセージ モードよりも効率的であるという点です。 トランスポート モードを使用するとき、トランスポートの仕様に基づいてセキュリティ機構を実装する必要があります。これによって、トランスポートを経由した Point-to-Point からのみメッセージを安全にフローできます。  
  
#### <a name="message-mode"></a>メッセージ モード  
 一方、メッセージ モードでは、セキュリティ データを各メッセージの一部として追加することによってセキュリティを提供します。 XML および SOAP のセキュリティ ヘッダーを使用して、メッセージの整合性と機密性を確保するために必要な資格情報とその他のデータを各メッセージに追加します。 各メッセージにはセキュリティ データが追加され、各メッセージを個別に処理する必要があるので、パフォーマンスが犠牲になります  (トランスポート モードでは、トランスポート層がセキュリティで保護されると、すべてのメッセージが自由にフローします)。ただし、メッセージ セキュリティには、トランスポート セキュリティに勝る利点が 1 つあります。それは、より柔軟であるという点です。 つまり、セキュリティ要件はトランスポートによって決定されません。 メッセージをセキュリティで保護するために、任意の種類のクライアント資格情報を使用できます (トランスポート モードでは、トランスポート プロトコルによって、使用できるクライアント資格情報の種類が決まります)。  
  
#### <a name="transport-with-message-credentials"></a>メッセージ資格情報付きトランスポート  
 3 番目のモードは、トランスポート セキュリティとメッセージ セキュリティの利点を組み合わせています。 このモードでは、トランスポート セキュリティを使用して、各メッセージの機密性と整合性を効率的に確保できます。 同時に、各メッセージには、その資格情報データが追加されるので、メッセージを認証できます。 認証と共に、承認も実装できます。 送信者を認証することによって、送信者の ID に応じてリソースへのアクセスが許可または拒否されます。  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>クライアント資格情報の種類と資格情報の値の指定  
 セキュリティ モードを選択した後で、必要に応じて、クライアント資格情報の種類を指定することもできます。 クライアント資格情報の種類では、サービスでの認証時にクライアントが使用する必要がある種類を指定します。  
  
 ただし、すべてのシナリオにクライアント資格情報の種類が必要とは限りません。 SSL over HTTP (HTTPS) を使用して、サービスはクライアントに対して認証を行います。 この認証の一部として、 *ネゴシエーション*と呼ばれるプロセスで、サービスの証明書がクライアントに送信されます。 SSL によってセキュリティで保護されたトランスポートによって、すべてのメッセージの機密性が確保されます。  
  
 クライアントの認証が必要なサービスを作成している場合、クライアント資格情報の種類の選択肢は、選択したトランスポートとモードによって異なります。 たとえば、HTTP トランスポートを使用して、トランスポート モードを選択する場合、基本、ダイジェストなどのいくつかの選択肢があります (これらの詳細については、資格情報の種類を参照してください[Understanding HTTP Authentication](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md))。  
  
 Windows ドメインで、そのネットワークの他のユーザーだけが利用できるサービスを作成している場合、最も使いやすいのは、Windows クライアント資格情報の種類です。 ただし、場合によっては、サービスにも証明書を提供する必要があります。 これに示した[方法。クライアント資格情報の値を指定](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)します。  
  
#### <a name="credential-values"></a>資格情報の値  
 *資格情報の値* とは、サービスが使用する実際の資格情報です。 資格情報の種類を指定したら、サービスを実際の資格情報で構成する必要があります。 Windows を選択し、サービスを Windows ドメインで実行する場合は、実際の資格情報の値を指定しません。  
  
## <a name="identity"></a>同一。  
 WCF では、用語*identity*サーバーとクライアントに異なる意味を持ちます。 つまり、サービスを実行しているとき、ID は認証後にセキュリティ コンテキストに割り当てられます。 実際の ID を表示するには、 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> クラスの <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティと <xref:System.ServiceModel.ServiceSecurityContext> プロパティを確認します。 詳細については、「[方法 :セキュリティ コンテキストを調べる](../../../docs/framework/wcf/how-to-examine-the-security-context.md)します。  
  
 反対に、クライアントでは、ID はサービスを検証するために使用されます。 デザイン時に、クライアント開発者を設定できます、 [ \<identity >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素をサービスから取得した値にします。 実行時に、クライアントは、要素の値をサービスの実際の ID と照合してチェックします。 チェックが失敗した場合、クライアントは通信を終了します。 特定のユーザー ID でサービスを実行している場合の値はユーザー プリンシパル名 (UPN) で、コンピューター アカウントでサービスを実行している場合の値はサービス プリンシパル名 (SPN) です。 詳細については、次を参照してください。[サービス Id と認証](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)します。 資格情報には、証明書、つまり証明書を識別する証明書内のフィールドも使用できます。  
  
## <a name="protection-levels"></a>保護レベル  
 `ProtectionLevel` プロパティは、 <xref:System.ServiceModel.ServiceContractAttribute> クラス、 <xref:System.ServiceModel.OperationContractAttribute> クラスなどのいくつかの属性クラスで使用します。 保護レベルは、サービスをサポートするメッセージ (またはメッセージ部分) が署名されるのか、署名および暗号化されるのか、または署名と暗号化なしで送信されるのかを指定する値です。 プロパティの詳細については、次を参照してください。[について保護レベル](../../../docs/framework/wcf/understanding-protection-level.md)、およびプログラミング例については、次を参照してください。[方法。ProtectionLevel プロパティを設定](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)します。 サービス コントラクトの設計の詳細については、`ProtectionLevel`コンテキストでは、次を参照してください。 [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [サービス ID と認証](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [保護レベルの理解](../../../docs/framework/wcf/understanding-protection-level.md)
- [委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)
- [セキュリティ](../../../docs/framework/wcf/feature-details/security.md)
- [セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)
- [方法: ProtectionLevel プロパティを設定します。](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [方法: Windows 資格情報でサービスをセキュリティで保護します。](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [方法: セキュリティ モードを設定します。](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [方法: クライアント資格情報の種類を指定します。](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
- [方法: PrincipalPermissionAttribute クラスでアクセスを制限します。](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [方法: サービスでのクライアントを偽装します。](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [方法: セキュリティ コンテキストを調べる](../../../docs/framework/wcf/how-to-examine-the-security-context.md)

---
title: WSFederation 認証モジュールの概要
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: 9ade6b0d9e4aadb353ca148f868d548fbaacfbc3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987698"
---
# <a name="wsfederation-authentication-module-overview"></a>WSFederation 認証モジュールの概要
Windows Identity Foundation (WIF) は、WS-Federated Authentication Module (WS-FAM) を通じて ASP.NET アプリケーションでのフェデレーション認証をサポートします。 このトピックは、フェデレーション認証の動作とその使用方法の理解に役立ちます。  
  
### <a name="overview-of-federated-authentication"></a>フェデレーション認証の概要  
 2 つのドメイン間に信頼関係がある場合、フェデレーション認証により、一方の信頼するドメイン内のセキュリティ トークン サービス (STS) から、他方の信頼するドメイン内の STS へ認証情報を提供できます。 この例を次の図に示します。  
  
 ![フェデレーション認証シナリオを示す図](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Fabrikam 信頼ドメインのクライアントが、Contoso 信頼ドメインの証明書利用者 (RP) アプリケーションに要求を送信します。  
  
2. RP は Contoso 信頼ドメインの STS にクライアントをリダイレクトします。 この STS はクライアントについては関知しません。  
  
3. Contoso STS は Contoso 信頼ドメインと信頼関係がある Fabrikam 信頼ドメインの STS にクライアントをリダイレクトします。  
  
4. Fabrikam STS がクライアント ID を確認し、Contoso STS にセキュリティ トークンを発行します。  
  
5. Contoso STS は、Fabrikam トークンを使用して RP が使用できる独自のトークンを作成したり、作成されたトークンを RP へ送信します。  
  
6. RP はセキュリティ トークンからクライアントのクレームを抽出し、承認決定を実行します。  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>ASP.NET を使用したフェデレーション認証モジュールの使用  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WS-ATOMICTRANSACTION) は、ASP.NET アプリケーションにフェデレーション認証を追加できる HTTP モジュールです。 フェデレーション認証により、認証ロジックが STS によって処理されるので、ビジネス ロジックの作成に集中できます。  
  
 WS-FAM を構成して、未認証の要求のリダイレクト先に対して STS を指定します。 WIF では次の 2 つの方法でユーザーを認証できます。  
  
1. パッシブリダイレクト:認証されていないユーザーが保護されたリソースにアクセスしようとしたときに、ログインページを必要とせずに単純に STS にリダイレクトする場合は、これが適切な方法です。 STS はユーザーの ID を検証し、そのユーザーの適切なクレームを含むセキュリティ トークンを発行します。 このオプションでは WS-FAM を HTTP モジュールのパイプラインに追加する必要があります。 Identity and Access Tool for Visual Studio 2012 を使用することで、WS-FAM を使用して STS でフェデレーションを実行するようアプリケーションの構成ファイルを変更できます。 詳細については、「[Visual Studio 2012 の ID およびアクセス ツール](../../../docs/framework/security/identity-and-access-tool-for-vs.md)」を参照してください。  
  
2. RP アプリケーションのサインイン ページ用の分離コードから <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> メソッドまたは <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> メソッドを呼び出すことができます。  
  
 受動リダイレクトでは、すべての通信は、クライアント (通常はブラウザー) からの応答/リダイレクトによって実行されます。 アプリケーションの HTTP パイプラインに WS-FAM を追加できます。ここで WS-FAM は未認証のユーザー要求を監視し、指定した STS にユーザーをリダイレクトします。  
  
 また、ASP.NET アプリケーションで機能をカスタマイズできるようにするいくつかのイベントも発生します。  
  
### <a name="how-the-ws-fam-works"></a>WS-FAM の動作  
 WS-FAM は <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> クラスに実装されます。 通常は、ASP.NET RP アプリケーションの HTTP パイプラインに WS-RELIABLEMESSAGING を追加します。 未認証のユーザーが保護されたリソースにアクセスしようとすると、RP は "401 authorization denied" (401 承認が拒否されました) という HTTP 応答を返します。 WS-FAM は、クライアントがこれを受け取ることを許可する代わりにこの応答を先に取得し、指定されている STS にユーザーをリダイレクトします。 STS はセキュリティ トークンを発行し、WS-FAM がそれを再び受け取ります。 Ws-management は、トークンを使用して、認証され<xref:System.Security.Claims.ClaimsPrincipal>たユーザーのインスタンスを作成します。これにより、通常の .NET Framework 承認メカニズムが機能するようになります。  
  
 HTTP はステートレスであるため、保護されている別のリソースにユーザーがアクセスしようとするたびに、このプロセス全体が繰り返し行われないようにする必要があります。 このような場合に <xref:System.IdentityModel.Services.SessionAuthenticationModule> が役に立ちます。 STS がユーザーにセキュリティ トークンを発行すると、<xref:System.IdentityModel.Services.SessionAuthenticationModule> もユーザーにセッションのセキュリティ トークンを作成して、クッキーにします。 以降の要求では、<xref:System.IdentityModel.Services.SessionAuthenticationModule> はこのクッキーを受け取り、これを使用してユーザーの <xref:System.Security.Claims.ClaimsPrincipal> を構築します。  
  
 次の図に、受動リダイレクトのケースの全体的な情報のフローを示します。 要求は STS を通じて自動的にリダイレクトされ、ログイン ページなしで資格情報が作成されます。  
  
 ![パッシブリダイレクトを使用したサインインを示す図。](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 次の図は、ユーザーが STS に認証されており、セキュリティ トークンが <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> によって処理されるときに発生する状況を詳細に示します。  
  
 ![パッシブ リダイレクトを使用するトークン処理のタイミング](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 次の図は、ユーザーのセキュリティ トークンがクッキーにシリアル化されていて <xref:System.IdentityModel.Services.SessionAuthenticationModule> 先に取得されている場合に発生する状況を詳細に示します。  
  
 ![コントロールを使用するサインインを示す SAM タイミング図](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>イベント  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>、<xref:System.IdentityModel.Services.SessionAuthenticationModule>、および親クラス <xref:System.IdentityModel.Services.HttpModuleBase> は、HTTP 要求処理のさまざまな段階でイベントを発生させます。 これらのイベントは、ASP.NET アプリケーション`global.asax`のファイルで処理できます。  
  
- ASP.NET のインフラストラクチャは、モジュールを初期化するためにモジュールの <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> メソッドを呼び出します。  
  
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> イベントは、<xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> から派生するアプリケーションのモジュールのいずれか 1 つで ASP.NET インフラストラクチャが <xref:System.IdentityModel.Services.HttpModuleBase> メソッドを初めて呼び出す場合に発生します。 このメソッドは静的な <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> のプロパティにアクセスし、これにより構成が Web.config ファイルから読み込まれます。 このイベントが発生するのは、このプロパティに初めてアクセスした場合だけです。 構成から初期化される <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> オブジェクトは、イベント ハンドラーの <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> のプロパティを通じてアクセスできます。 構成がモジュールに適用される前に、このイベントを使用して構成を変更できます。 Application_Start イベントでこのイベントのハンドラーを追加できます。  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     各モジュールが <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> と <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> 抽象メソッドをオーバーライドします。 これらのメソッドの 1 番目は、モジュールにとって重要な ASP.NET パイプライン イベントのハンドラーを追加します。 ほとんどの場合、モジュールの既定の実装で十分です。 これらのメソッドの 2 番目は、<xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> プロパティからモジュールのプロパティを初期化します (これは、以前に読み込まれた構成のコピーです)。<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> または <xref:System.IdentityModel.Services.SessionAuthenticationModule> から派生するクラスの構成から新しいプロパティの初期化をサポートするには、2 番目のメソッドをオーバーライドすることが必要になる場合があります。 このような場合、追加された構成プロパティをサポートするために、<xref:System.IdentityModel.Configuration.IdentityConfiguration>、<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>、または <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> などの適切な構成オブジェクトから派生することが必要になる場合があります。  
  
- WS-FAM は STS によって発行されたセキュリティ トークンを受け取る場合、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> イベントを発生させます。  
  
- WS-FAM はトークンを検証した後 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> イベントを発生させます。  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> はユーザーのセッションのセキュリティ トークンを作成するとき <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> イベントを発生させます。  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> は、セッションのセキュリティ トークンを含むクッキーを使用してそれ以降の要求を受け取る場合、<xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> イベントを発生させます。  
  
- WS-FAM はユーザーを発行者にリダイレクトする前に、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> イベントを発生させます。 WS-Federation のサインイン要求は、イベントに渡される <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> の <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> のプロパティを通じて利用できます。 この要求は、発行者に送信する前に変更できます。  
  
- WS-FAM は、クッキーが正常に作成され、ユーザーがサインインしている場合に、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> イベントを発生させます。  
  
- WS-FAM は、各ユーザーのセッションが閉じられる際に各セッションにつき 1 回 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> イベントを発生させます。 セッションがクライアント側で閉じられた場合、このイベントは発生しません (たとえば、セッション クッキーを削除するなど)。 SSO 環境では、IP-STS は各 RP にサインアウトするよう要求することもできます。 また、これによりこのイベントが発生し、<xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> は `true` に設定されます。  
  
> [!NOTE]
> <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> または <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> により発生したイベント中は、<xref:System.IdentityModel.Services.SessionAuthenticationModule> プロパティを使用しないでください。 これは、イベントは認証プロセス中に発生するが、<xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> は認証プロセスの後に設定されるためです。  
  
### <a name="configuration-of-federated-authentication"></a>フェデレーション認証の構成  
 WS-FAM と SAM は [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 要素で構成されます。 [\<wsFederation>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) の子要素は、WS-FAM プロパティの既定値 (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> プロパティや <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> プロパティなど) を構成します (これらの値は、一部の WS-FAM イベントのハンドラーを用意することにより要求ごとに変更できます (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> など))。SAM で使用される cookie ハンドラーは [\<cookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) 子要素によって構成されます。 WIF には <xref:System.IdentityModel.Services.ChunkedCookieHandler> クラスに実装されている既定の cookie ハンドラーが用意されており、チャンク サイズは [\<chunkedCookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) 要素で設定できます。 `<federationConfiguration>` 要素は <xref:System.IdentityModel.Configuration.IdentityConfiguration> を参照し、この要素にはアプリケーションで使用される他の WIF コンポーネント (<xref:System.Security.Claims.ClaimsAuthenticationManager>、<xref:System.Security.Claims.ClaimsAuthorizationManager> など) の構成が用意されています。 ID の構成は、`<federationConfiguration>` 要素の `identityConfigurationName` 属性で [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 名前付き要素を指定することで明示的に参照できます。 ID 構成を明示的に参照しない場合、既定の ID 構成が使用されます。  
  
 次の XML は、ASP.NET の証明書利用者 (RP) アプリケーションの構成を示します。 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> および <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 構成セクションは `<configSections>` 要素の下に追加されます。 SAM および WS-FAM は、`<system.webServer>`/`<modules>` 要素の下にある HTTP モジュールに追加されます。 最後に、WIF コンポーネントは `<system.identityModel>`/`<identityConfiguration>` および `<system.identityModel.services>`/`<federationConfiguration>` 要素の下に構成されます。 この構成では、既定のクッキー ハンドラーであり、`<cookieHandler>` 要素で指定されたクッキー ハンドラー型ではない、チャンクされたクッキー ハンドラーを指定します。  
  
> [!WARNING]
> 次の例では、`requireHttps` 要素の `<wsFederation>` 属性と `requireSsl` 要素の `<cookieHandler>` 属性は `false` です。 これは、セキュリティ上の脅威になる可能性があります。 稼働環境では、これらの値は両方とも `true` に設定する必要があります。  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)

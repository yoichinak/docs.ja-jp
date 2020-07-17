---
title: カスタム トークン
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: b073375325d2989a23624303f2c40b8f61a29d02
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928651"
---
# <a name="custom-token"></a>カスタム トークン

このサンプルでは、カスタムトークンの実装を Windows Communication Foundation (WCF) アプリケーションに追加する方法を示します。 この例では、`CreditCardToken` を使用して、クライアントのクレジット カードに関する情報をサーバーに安全に渡します。 このトークンは、WS-Security メッセージ ヘッダー内で渡され、対称セキュリティ バインド要素を使用してメッセージ本文と他のメッセージ ヘッダーと共に署名および暗号化されます。 これは、組み込みのトークンでは不十分な場合に役立ちます。 このサンプルでは、組み込みのトークンのいずれかを使用する代わりに、カスタム セキュリティ トークンをサービスに提供する方法を示します。 サービスは、要求/応答通信パターンを定義するコントラクトを実装します。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

 このサンプルに示されている手順の概要は次のとおりです。

- クライアントがカスタム セキュリティ トークンをサービスに渡す方法。

- サービスがカスタム セキュリティ トークンを使用および検証する方法。

- WCF サービスコードが、カスタムセキュリティトークンを含む、受信したセキュリティトークンに関する情報を取得する方法。

- サーバーの X.509 証明書を使用して、メッセージの暗号化や署名に使用する対称キーを保護する方法。

## <a name="client-authentication-using-a-custom-security-token"></a>カスタム セキュリティ トークンを使用したクライアント認証

 サービスは単一エンドポイントを公開します。エンドポイントは、`BindingHelper` クラスと `EchoServiceHost` クラスを使用してプログラムによって作成されます。 エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。 バインディングは、`SymmetricSecurityBindingElement` と `HttpTransportBindingElement` を使用して、カスタム バインディングとして構成されます。 このサンプルでは、`SymmetricSecurityBindingElement` を設定してサービスの X.509 証明書を使用し、送信中の対称キーを保護して、WS-Security メッセージ ヘッダー内でカスタム `CreditCardToken` を署名および暗号化されたセキュリティ トークンとして渡します。 この動作により、クライアント認証に使用されるサービス資格情報と、サービス X.509 証明書に関する情報が指定されます。

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 メッセージ内のクレジット カード トークンを使用するため、このサンプルではカスタム サービス資格情報を使用してこの機能を実現します。 サービス資格情報クラスは `CreditCardServiceCredentials` クラス内にあり、`EchoServiceHost.InitializeRuntime` メソッド内のサービス ホストの動作コレクションに追加されます。

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 クライアント エンドポイントは、サービス エンドポイントと同様の方法で構成されます。 クライアントは、同じ `BindingHelper` クラスを使用してバインディングを作成します。 セットアップの残りの部分は、`Client` クラスにあります。 クライアントはさらに、`CreditCardToken` インスタンスを適切なデータと共にクライアント エンドポイントの動作コレクションに追加することによって、`CreditCardClientCredentials` に含まれる情報とサービス X.509 証明書に関する情報をセットアップ コード内に設定します。 サンプルでは、サービス証明書として、サブジェクト名が `CN=localhost` に設定された X.509 証明書を使用しています。

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a>カスタム セキュリティ トークンの実装

 WCF でカスタムセキュリティトークンを有効にするには、カスタムセキュリティトークンのオブジェクト表現を作成します。 サンプルのこの表現は、`CreditCardToken` クラスにあります。 このオブジェクト表現は、セキュリティ トークンのすべての関連情報を保持し、セキュリティ トークンに含まれるセキュリティ キーのリストを提供します。 この場合、クレジット カード セキュリティ トークンにはセキュリティ キーが含まれません。

 次のセクションでは、カスタムトークンをネットワーク経由で送信し、WCF エンドポイントで使用できるようにするために行う必要がある操作について説明します。

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>カスタム クレジット カード トークンのメッセージへの提供とメッセージからの取得

 WCF のセキュリティトークンシリアライザーは、メッセージの XML からセキュリティトークンのオブジェクト表現を作成し、セキュリティトークンの XML 形式を作成する役割を担います。 また、セキュリティ トークンを指すキー識別子の読み取りと書き込みなど、他の機能も備えていますが、この例ではセキュリティ トークン関連の機能だけを使用します。 カスタム トークンを有効にするには、独自のセキュリティ トークン シリアライザーを実装する必要があります。 このサンプルでは、この目的のために `CreditCardSecurityTokenSerializer` クラスを使用します。

 サービス側では、カスタム シリアライザーは XML 形式のカスタム トークンを読み取り、そこからカスタム トークンのオブジェクト表現を作成します。

 クライアント側では、`CreditCardSecurityTokenSerializer` クラスが、セキュリティ トークンのオブジェクト表現に含まれる情報を XML ライターに書き込みます。

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>トークン プロバイダー クラスとトークン認証システム クラスの作成方法

 クライアントとサービスの資格情報は、セキュリティ トークン マネージャーのインスタンスを提供します。 セキュリティ トークン マネージャーのインスタンスを使用すると、トークン プロバイダー、トークン認証システム、およびトークン シリアライザーを取得できます。

 トークン プロバイダーは、クライアントまたはサービスの資格情報に含まれる情報に基づいて、トークンのオブジェクト表現を作成します。 次に、トークンのオブジェクト表現は、(前のセクションで説明したとおり) トークン シリアライザーを使用してメッセージに書き込まれます。

 トークン認証システムは、到着したメッセージ内のトークンを検証します。 受信トークンのオブジェクト表現は、トークン シリアライザーによって作成されます。 このオブジェクト表現は、次に、検証のためトークン認証システムに渡されます。 トークンが正常に検証されたら、トークン認証システムは `IAuthorizationPolicy` オブジェクトのコレクションを返します。このオブジェクトはトークンに含まれる情報を表します。 この情報は、承認に関する決定を行ったり、アプリケーションに対するクレームを提供したりするために、後でメッセージ処理中に使用されます。 この例では、クレジット カード トークンの認証システムはこの目的のために `CreditCardTokenAuthorizationPolicy` を使用します。

 トークン シリアライザーは、トークンのオブジェクト表現を通信回線に送り、通信回線からトークンのオブジェクト表現を受け取ります。 これについては、前のセクションで説明したとおりです。

 このサンプルでは、トークン プロバイダーはクライアントでのみ使用し、トークン認証システムはサービスでのみ使用します。これは、クレジット カード トークンの送信はクライアントからサービスへの方向でのみ行うためです。

 クライアント側の機能は `CreditCardClientCredentials`、`CreditCardClientCredentialsSecurityTokenManager`、および `CreditCardTokenProvider` クラスにあります。

 サービス側の機能は `CreditCardServiceCredentials`、`CreditCardServiceCredentialsSecurityTokenManager`、`CreditCardTokenAuthenticator`、および `CreditCardTokenAuthorizationPolicy` クラスにあります。

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException(nameof(creditCardFile));

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException(nameof(issuedClaims));
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a>呼び出し元の情報の表示

 呼び出し元の情報を表示するには、次のサンプル コードに示すように `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` を使用します。 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` には、現在の呼び出し元に関連付けられている承認クレームが含まれています。 クレームは、`CreditCardToken` コレクションの `AuthorizationPolicies` クラスによって提供されます。

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。

## <a name="setup-batch-file"></a>セットアップ バッチ ファイル

 このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする、IIS でホストされるアプリケーションを実行できるようになります。 このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。

 次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。

- サーバー証明書の作成 :

     `Setup.bat` バッチ ファイルの次の行は、使用するサーバー証明書を作成します。 `%SERVER_NAME%` 変数はサーバー名です。 この変数を変更して、使用するサーバー名を指定します。 このバッチ ファイルでの既定は localhost です。 `%SERVER_NAME%` 変数を変更する場合は、Client.cs ファイルと Service.cs ファイル全体を参照して、localhost のすべてのインスタンスを Setup.bat スクリプトで使用するサーバー名に置き換える必要があります。

     証明書は、`LocalMachine` ストアの場所の My (Personal) ストアに保存されます。 証明書は、IIS でホストされるサービスの LocalMachine ストアに保存されます。 自己ホスト型サービスの場合、バッチ ファイルで文字列 LocalMachine を CurrentUser に置き換えて、クライアント証明書を CurrentUser ストアの場所に保存します。

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- サーバー証明書のクライアントの信頼された証明書ストアへのインストール。

     Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。 この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。 マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。

    ```bat
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- IIS でホストされるサービスから証明書の秘密キーへのアクセスを有効にするには、IIS でホストされる処理が実行されているユーザー アカウントに、秘密キーへの適切なアクセス許可を付与する必要があります。 これは、Setup.bat スクリプトの最後の手順によって実現されます。

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> セットアップの .bat バッチファイルは、Visual Studio 2012 のコマンドプロンプトから実行するように設計されています。 Visual Studio 2012 のコマンドプロンプト内で設定された PATH 環境変数は、セットアップの .bat スクリプトで必要な実行可能ファイルが格納されているディレクトリを指します。

#### <a name="to-set-up-and-build-the-sample"></a>サンプルをセットアップしてビルドするには

1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。

2. ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。

#### <a name="to-run-the-sample-on-the-same-computer"></a>サンプルを同じコンピューターで実行するには

1. 管理者特権で Visual Studio 2012 のコマンドプロンプトウィンドウを開き、サンプルのインストールフォルダーから Setup.exe を実行します。 これにより、サンプルの実行に必要なすべての証明書がインストールされます。Makecert.exe が存在するフォルダーがパスに含まれていることを確認します。

> [!NOTE]
> サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。 他のセキュリティ サンプルでも同じ証明書を使用します。  
  
1. Client.exe を client\bin ディレクトリで起動します。 クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
2. クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。  
  
#### <a name="to-run-the-sample-across-computer"></a>サンプルを複数のコンピューターで実行するには  
  
1. サービス コンピューターにサービス バイナリ用のディレクトリを作成します。  
  
2. サービス プログラム ファイルを、サービス コンピューターのサービス ディレクトリにコピーします。 必ず CreditCardFile.txt をコピーしてください。これを行わない場合、クレジット カードの認証システムはクライアントから送信されたクレジット カード情報を検証できません。 Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。  
  
3. コンピューターの完全修飾ドメイン名を含むサブジェクト名を持つサーバー証明書が必要です。 `%SERVER_NAME%` 変数を、サービスがホストされるコンピューターの完全修飾名に変更すると、Setup.bat を使用してこの証明書を作成できます。 セットアップの .bat ファイルは、管理者特権で開かれた Visual Studio の開発者コマンドプロンプトで実行する必要があることに注意してください。  
  
4. サーバー証明書をクライアントの CurrentUser-TrustedPeople ストアにコピーします。 このようにする必要があるのは、サーバー証明書が信頼できる発行元から発行されていない場合のみです。  
  
5. EchoServiceHost.cs ファイルで、証明書のサブジェクト名の値を localhost から完全修飾コンピューター名に変更します。  
  
6. クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。  
  
7. Client.cs ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。  
  
8. Client.cs ファイルで、サービス X.509 証明書のサブジェクト名を localhost からリモート ホストの完全修飾コンピューター名に変更します。  
  
9. クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。  
  
10. クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。  
  
#### <a name="to-clean-up-after-the-sample"></a>サンプルの実行後にクリーンアップするには  
  
1. サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。  

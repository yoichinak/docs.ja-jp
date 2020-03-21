---
title: '方法 : フェデレーション クライアントを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: a9213d8cbbafaaa1fffa3a1db0d6936c2fc6544f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185037"
---
# <a name="how-to-create-a-federated-client"></a>方法 : フェデレーション クライアントを作成する
Windows 通信基盤 (WCF) では、*フェデレーション サービス*のクライアントを作成するには、主に次の 3 つの手順を実行します。  
  
1. [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)または同様のカスタム バインディングを構成します。 適切なバインディングの作成の詳細については、「[方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)」を参照してください。 または、フェデレーション サービスのメタデータ エンドポイントに対して[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe) を](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)実行して、フェデレーション サービスおよび 1 つ以上のセキュリティ トークン サービスと通信するための構成ファイルを生成します。  
  
2. クライアントがセキュリティ トークン サービスと対話する際のさまざまな側面を制御する <xref:System.ServiceModel.Security.IssuedTokenClientCredential> のプロパティを設定します。  
  
3. セキュリティ トークン サービスなど、特定のエンドポイントとのセキュリティ保護された通信に必要な証明書を許可する <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> のプロパティを設定します。  
  
> [!NOTE]
> クライアントが、偽装された資格情報、<xref:System.Security.Cryptography.CryptographicException> バインディングやカスタムの発行済みトークン、および非対称キーを使用すると、<xref:System.ServiceModel.WSFederationHttpBinding> がスローされる可能性があります。 <xref:System.ServiceModel.WSFederationHttpBinding> プロパティと <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> プロパティをそれぞれ <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> に設定すると、<xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey> バインディングとカスタムの発行済みトークンで非対称キーが使用されます。 クライアントがメッセージを送信しようとするときに、クライアントが偽装している ID のユーザー プロファイルが存在しないと、<xref:System.Security.Cryptography.CryptographicException> がスローされます。 この問題を回避するには、クライアント コンピューターにログオンした後、または `LoadUserProfile` を呼び出した後に、メッセージを送信します。  
  
 ここでは、これらの手順について詳しく説明します。 適切なバインディングの作成の詳細については、「[方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)」を参照してください。 フェデレーション サービスの動作の詳細については、「[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)」を参照してください。  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>フェデレーション サービスの構成を生成し、確認するには  
  
1. サービスのメタデータ URL のアドレスをコマンド ライン パラメーターとして使用して、サービス モデル メタデータ[ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を実行します。  
  
2. 生成された構成ファイルを適切なエディターで開きます。  
  
3. 生成された[\<発行者の>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)の属性と内容を調べ、[\<要素>メタデータを確認](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)します。 これらは[\<、wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)またはカスタム バインディング要素の[\<セキュリティ>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)要素内にあります。 予期されたドメイン名やその他のアドレス情報がアドレスに含まれていることを確認します。 この情報をチェックすることは重要です。それは、クライアントがこれらのアドレスに対して認証を行い、ユーザー名とパスワードの組み合わせなどの情報を公開する可能性があるためです。 アドレスが予期されたアドレスではない場合、意図しない受信者に情報が公開されるおそれがあります。  
  
4. コメントアウトされた要素内の要素>、追加`alternativeIssuedTokenParameters`[\<の発行済み<TokenParameters>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)確認します。 Svcutil.exe ツールを使用してフェデレーション サービスの構成を生成するときに、フェデレーション サービスまたは任意の中間セキュリティ トークン サービスが、発行者アドレスを指定せずに、複数のエンドポイントを公開するセキュリティ トークン サービスのメタデータ アドレスを指定している場合、生成された構成ファイルは最初のエンドポイントを参照します。 追加のエンドポイントは、コメントアウトされた<>`alternativeIssuedTokenParameters`要素として構成ファイルに含まれます。  
  
     これらの<>`issuedTokenParameters`の1つが、構成に既に存在する方が好ましいかどうかを判断します。 たとえば、クライアントは、ユーザー名とパスワードのペアではなく、Windows CardSpace トークンを使用してセキュリティ トークン サービスに対して認証を行うことを好む場合があります。  
  
    > [!NOTE]
    > サービスと通信するまでに複数のセキュリティ トークン サービスをたどる必要がある場合は、中間セキュリティ トークン サービスがクライアントを不適切なセキュリティ トークン サービスにダイレクトする可能性があります。 したがって、[\<発行されたトークン パラメーター>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)のセキュリティ トークン サービスのエンドポイントが、予期されるセキュリティ トークン サービスであり、不明なセキュリティ トークン サービスではないことを確認します。  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>コードで IssuedTokenClientCredential を構成するには  
  
1. 次のコード例に示すように、<xref:System.ServiceModel.Security.IssuedTokenClientCredential> クラスの <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> プロパティまたは <xref:System.ServiceModel.Description.ClientCredentials> クラスから返された、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティから <xref:System.ServiceModel.ChannelFactory> にアクセスします。  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. トークン キャッシュが不要な場合は、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> プロパティを `false` に設定します。 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> プロパティにより、セキュリティ トークン サービスからのこれらのトークンをキャッシュするかどうかが制御されます。 このプロパティを `false` に設定すると、クライアントは、以前のトークンがいまだに有効な場合でも、フェデレーション サービスに対してクライアント自体を再認証する必要があるときに、新しいトークンをセキュリティ トークン サービスに要求します。 このプロパティを `true` に設定すると、クライアントは、トークンの有効期限が切れていない限り、フェデレーション サービスに対してクライアント自体を再認証する必要があるときに既存のトークンを再利用します。 既定では、 `true`です。  
  
3. キャッシュされたトークンの制限時間を設ける必要がある場合は、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> プロパティを <xref:System.TimeSpan> 値に設定します。 このプロパティは、トークンがキャッシュされる時間を指定します。 指定の時間が経過すると、トークンはクライアントのキャッシュから削除されます。 既定では、トークンは無期限でキャッシュされます。 制限時間を 10 分に設定する例を次に示します。  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. 省略可能。 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> をパーセンテージに設定します。 既定値は 60 (パーセント) です。 このプロパティは、トークンの有効期間をパーセンテージで指定します。 たとえば、発行されたトークンが 10 時間有効で、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> が 80 に設定されている場合、このトークンは 8 時間後に更新されます。 この値を 80% に設定する例を次に示します。  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     トークンの有効期間と `IssuedTokenRenewalThresholdPercentage` 値によって決まる更新間隔は、キャッシュ時間が更新しきい時間よりも短い場合には、`MaxIssuedTokenCachingTime` 値によってオーバーライドされます。 たとえば、`IssuedTokenRenewalThresholdPercentage` とトークンの有効期間を掛けた積が 8 時間であり、`MaxIssuedTokenCachingTime` 値が 10 分の場合、クライアントは、トークンの更新のために 10 分ごとにセキュリティ トークン サービスに連絡します。  
  
5. <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> 以外のキー エントロピ モードが、メッセージ セキュリティやメッセージ資格情報付きトランスポート セキュリティを使用しないバインディング (たとえば、 バインディングに <xref:System.ServiceModel.Channels.SecurityBindingElement> が存在しない場合) で必要な場合は、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> プロパティに適切な値を設定します。 *エントロピー*モードは、プロパティを使用して対称キーを<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A>制御できるかどうかを決定します。 この既定値は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> であり、この場合、クライアントとトークン発行者の両方から、実際のキーを生成する際に組み合わせるデータが提供されます。 これ以外の値は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> と <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy> であり、それぞれクライアントまたはサーバーによってキー全体が指定されます。 サーバーのデータのみを使用してキーを指定するよう、このプロパティを設定する例を次に示します。  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > セキュリティ トークン サービスまたはサービス バインディングに <xref:System.ServiceModel.Channels.SecurityBindingElement> が存在する場合、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> で設定された <xref:System.ServiceModel.Security.IssuedTokenClientCredential> は、<xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> の `SecurityBindingElement` プロパティによってオーバーライドされます。  
  
6. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> プロパティによって返されるコレクションに発行者固有のエンドポイント動作を追加して、これらの動作を構成します。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>構成で IssuedTokenClientCredential を構成するには  
  
1. エンドポイント動作で[\<発行済みトークン](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)>要素の子として[\<、発行済みトークン>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)要素を作成します。  
  
2. トークンキャッシュが必要ない場合は、<>`cacheIssuedTokens``issuedToken`要素の属性を に`false`設定します。  
  
3. キャッシュされたトークンに時間制限が必要な場合は、<>`maxIssuedTokenCachingTime``issuedToken`要素の属性を適切な値に設定します。 次に例を示します。  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. デフォルト以外の値が優先される場合は、<>`issuedTokenRenewalThresholdPercentage``issuedToken`要素の属性を適切な値に設定します。  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. メッセージ セキュリティやメッセージ資格情報付きトランスポート セキュリティを使用しないバインディングで `CombinedEntropy` 以外のキー エントロピ モードが必要な場合 (たとえば、バインディングに `SecurityBindingElement` が存在しない場合) は、必要に応じて次のように `defaultKeyEntropyMode` 要素の `<issuedToken>` 属性を `ServerEntropy` または `ClientEntropy` に設定します。  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. 省略可能。 `issuerChannelBehaviors` <>要素を<>`issuedToken`要素の子として作成して、発行者固有のカスタム エンドポイント動作を構成します。 動作ごとに、<>`issuerChannelBehaviors`要素の`add`子として<>要素を作成します。 <`add`の>要素に属性を設定して、動作`issuerAddress`の発行者アドレスを指定します。 <`add`の>要素に属性を`behaviorConfiguration`設定して、動作自体を指定します。  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>コードで X509CertificateRecipientClientCredential を構成するには  
  
1. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> クラスまたは <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> プロパティの <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティが持つ <xref:System.ServiceModel.ClientBase%601> プロパティを介して、次のように <xref:System.ServiceModel.ChannelFactory> にアクセスします。  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. 特定のエンドポイントの証明書として <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> インスタンスを使用できる場合は、<xref:System.Collections.Generic.ICollection%601.Add%2A> プロパティによって返されるコレクションの <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> メソッドを使用します。  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> インスタンスが使用できない場合は、次の例に示すように、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> メソッドを使用します。  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>構成で X509CertificateRecipientClientCredential を構成するには  
  
1. スコープ付[\<き証明書>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)要素を[\<作成するエンドポイント](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)動作の[\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素の子である serviceCertificate>要素を作成します。  
  
2. `<add>` 要素の子要素として `<scopedCertificates>` 要素を作成します。 適切な証明書を参照するように `storeLocation`、`storeName`、`x509FindType`、`findValue` の各属性の値を指定します。 次の例に示すように、`targetUri` 属性を、証明書が使用されるエンドポイントのアドレスを指定する値に設定します。  
  
    ```xml  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## <a name="example"></a>例  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> クラスのインスタンスをコードで構成する例を、次のコード サンプルに示します。  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  
 情報の漏えいを防ぐために、Svcutil.exe ツールを使用してフェデレーション エンドポイントからのメタデータを処理するクライアントでは、生成されたセキュリティ トークン サービス アドレスが予期されたものであることを確認する必要があります。 これが特に重要なのは、セキュリティ トークン サービスが複数のエンドポイントを公開する場合です。この場合、Svcutil.exe ツールは、複数のエンドポイントうちの最初のエンドポイントを使用する構成ファイルを生成しますが、このエンドポイントは、クライアントが使用する必要のあるエンドポイントと異なる場合があるためです。  
  
## <a name="localissuer-required"></a>LocalIssuer が必要な場合  
 チェーン内の 2 番目から最後までのセキュリティ トークン サービスによって発行者アドレスまたは発行者メタデータ アドレスが指定されている場合、Svcutil.exe の既定の出力では、ローカル発行者が使用されません。クライアントで常にローカル発行者を使用する場合は、この点に注意が必要です。  
  
 クラスの<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>プロパティ 、、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>および<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>プロパティの設定の<xref:System.ServiceModel.Security.IssuedTokenClientCredential>詳細については、「[方法 : ローカル発行者を構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)」を参照してください。  
  
## <a name="scoped-certificates"></a>範囲指定された証明書  
 証明書ネゴシエーションを使用しないという一般的な理由により、任意のセキュリティ トークン サービスとの通信用のサービス証明書を指定する必要がある場合は、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> プロパティを使用して指定できます。 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> メソッドは、パラメーターとして <xref:System.Uri> と <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> を受け取ります。 指定した証明書は、指定した URI のエンドポイントと通信するときに使用されます。 または、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> メソッドを使用して、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> プロパティによって返されるコレクションに証明書を追加することもできます。  
  
> [!NOTE]
> 特定の URI に範囲指定された証明書というクライアントの概念は、該当する URI でエンドポイントを公開するサービスへの送信呼び出しを行うアプリケーションにだけ適用されます。 発行されたトークンの署名に使用される証明書 (<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A><xref:System.ServiceModel.Security.IssuedTokenServiceCredential>クラスによって返されるコレクション内のサーバー上で構成されているものなど) には適用されません。 詳細については、「[方法 : フェデレーション サービスで資格情報を構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)
- [方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [方法 : ローカル発行者を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [メタデータを使用する場合のセキュリティ上の考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [方法 : セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)

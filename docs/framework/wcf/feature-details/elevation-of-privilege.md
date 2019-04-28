---
title: 権限の昇格
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: fd5829d2dbb1853bf65f1f6e402b918137bd59e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856405"
---
# <a name="elevation-of-privilege"></a>権限の昇格
*特権が昇格される*本来付与されたもの以外のアクセス許可を承認を攻撃者に与えた結果します。 たとえば、"読み取り専用" アクセス許可の権限セットを持つ攻撃者が、何らかの方法で権限セットを "読み取り/書き込み" アクセス許可を含むものに昇格させます。  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>SAML トークンのクレームには信頼された STS による署名が必要  
 SAML (Security Assertions Markup Language) トークンは、発行済みトークンの既定の型である汎用 XML トークンです。 SAML トークンは、通常の交換においてエンド Web サービスから信頼されたセキュリティ トークン サービス (STS) によって作成できます。 SAML トークンには、ステートメント内にクレームが格納されます。 攻撃者は、有効なトークンからクレームをコピーして新しい SAML トークンを作成し、別の発行者による署名を行うことがあります。 この目的は、サーバーが発行者を検証するかどうかを確認し、検証しない場合に、この脆弱性を利用して信頼された STS が意図したものよりも高い権限を与える SAML トークンを作成することです。  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> クラスは、SAML トークンに含まれるデジタル署名を検証します。<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> クラスの <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> が <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> に設定されている場合、既定の <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust> は、SAML トークンが有効な X.509 証明書によって署名されていることを要求します。 SAML トークンの発行者を信頼できるかどうか判断するには、`ChainTrust` モードだけでは不十分です。 より詳細な信頼モデルを必要とするサービスは、承認ポリシーと強制ポリシーを使用して、発行済みトークン認証によって生成されたクレーム セットの発行者をチェックするか、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential> の X.509 検証設定を使用して、許可する署名証明書のセットを制限できます。 詳細については、次を参照してください。[管理クレームと Id モデルでの承認](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)と[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。  
  
## <a name="switching-identity-without-a-security-context"></a>セキュリティ コンテキストを使用しない ID の切り替え  
 次の内容は、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] にのみ適用されます。  
  
 クライアントとサーバー、クライアントの id の間の接続が確立されたときに変化しない状況の 1 つを除く: すべての次の条件に該当する場合、WCF クライアントが開かれた後に。  
  
- (トランスポート セキュリティ セッションまたはメッセージ セキュリティ セッションを使用) のセキュリティ コンテキストを確立するプロシージャがオフになっている (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A>プロパティに設定されて`false`メッセージ セキュリティまたはトランスポート セキュリティを確立できない場合トランスポート セキュリティの場合は、セッションが使用されます。 トランスポート セキュリティの場合は、セキュリティ セッションを確立できないトランスポート (HTTPS など) が使用されている)。  
  
- Windows 認証を使用している。  
  
- 資格情報を明示的に設定していない。  
  
- 偽装されたセキュリティ コンテキストでサービスを呼び出している。  
  
 これらの条件に該当する場合、サービスに対するクライアントの認証に使用される id が変わる可能性があります (必要はありませんが、偽装された id、プロセス id 代わりに)、WCF クライアントが開かれた後にします。 この状況が発生するのは、サービスに対するクライアントの認証に使用する Windows 資格情報がすべてのメッセージと共に送信され、認証に使用する資格情報が現在のスレッドの Windows ID から取得されるためです。 (たとえば、別の呼び出し元を偽装することによって) 現在のスレッドの Windows ID が変更された場合、メッセージに添付され、サービスに対するクライアントの認証に使用する資格情報も変更される可能性があります。  
  
 偽装と共に Windows 認証を使用する場合に動作を確定する必要があるときは、Windows 資格情報を明示的に設定するか、サービスでセキュリティ コンテキストを確立する必要があります。 これを行うには、メッセージ セキュリティ セッションまたはトランスポート セキュリティ セッションを使用します。 たとえば、net.tcp トランスポートは、トランスポート セキュリティ セッションを提供します。 また、サービスの呼び出し時に、クライアント操作の同期バージョンだけを使用する必要があります。 メッセージ セキュリティ コンテキストを確立する場合は、構成済みセッションの更新時間よりも長い時間、サービスへの接続を開いたままにしないようにしてください。セッション更新プロセスの間にも ID が変更される可能性があるためです。  
  
### <a name="credentials-capture"></a>資格情報のキャプチャ  
 次の内容は、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降のバージョンに適用されます。  
  
 クライアントまたはサービスが使用する資格情報は、現在のコンテキストのスレッドに基づきます。 資格情報は、クライアントまたはサービスの `Open` メソッド (または、非同期呼び出しの場合は `BeginOpen`) が呼び出された場合に取得されます。 <xref:System.ServiceModel.ServiceHost> クラスおよび <xref:System.ServiceModel.ClientBase%601> クラスのいずれの場合も、`Open` メソッドおよび `BeginOpen` メソッドは、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> クラスの <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> メソッドおよび <xref:System.ServiceModel.Channels.CommunicationObject> メソッドから継承されます。  
  
> [!NOTE]
>  `BeginOpen` メソッドを使用する場合、キャプチャされた資格情報は、このメソッドを呼び出したプロセスの資格情報であることが保証されません。  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>トークン キャッシュによる以前のデータを使用した再生の許可  
 WCF でのローカル セキュリティ機関 (LSA)`LogonUser`ユーザー名とパスワードによってユーザーを認証する関数。 WCF を使用すると、ログオン関数は、コストの高い操作であるためを表すトークンをキャッシュすると、認証されたユーザーにパフォーマンスが向上します。 キャッシュ機構は、それ以降に使用できるように `LogonUser` の結果を保存します。 このメカニズムは既定では無効になります。有効にするには、設定、<xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A>プロパティを`true`を使用して、または、`cacheLogonTokens`の属性、 [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)します。  
  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> プロパティを <xref:System.TimeSpan> に設定するか、`cachedLogonTokenLifetime` 要素の `userNameAuthentication` 属性を使用することで、キャッシュされたトークンの有効期間 (TTL) を設定できます。既定値は 15 分です。 Windows からユーザー アカウントが削除された場合や、パスワードが変更されている場合でも、トークンがキャッシュされている間は、同じユーザー名とパスワードを指定すると、どのクライアントもこのトークンを使用できます。 TTL が期限切れトークンがキャッシュから削除するまで、WCF は、(場合によって悪意のある) のユーザーが認証を使用します。  
  
 この問題を緩和します。攻撃のウィンドウを小さくには、設定、`cachedLogonTokenLifetime`最短の時間の値にまたがる、ユーザーが必要です。  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>トークンの承認を発行するには。大きな値にリセットされた有効期限  
 一定の条件下で、<xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> の <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティが予期しない大きな値 (<xref:System.DateTime.MaxValue> フィールド値から 1 日引いた値 (December 20, 9999)) に設定される場合があります。  
  
 これは、<xref:System.ServiceModel.WSFederationHttpBinding>、およびクライアント資格情報の種類が発行済みトークンであるシステム提供のバインディングを使用している場合に発生します。  
  
 また、以下のメソッドのいずれかを使用して、カスタム バインドを作成した場合にも発生します。  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 これをできるだけ防ぐには、承認ポリシーによって各承認ポリシーのアクションと有効期限をチェックする必要があります。  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>クライアントで予定していたものと異なる証明書をサービスで使用する場合  
 一定の条件下で、クライアントが X.509 証明書を使用してメッセージにデジタル署名したときに、予定していたものと異なる証明書をサービスが取得する場合があります。  
  
 これは、次のような状況で発生する可能性があります。  
  
- クライアントが X.509 証明書を使用してメッセージにデジタル署名したときに、その X.509 証明書をメッセージに添付するのではなく、サブジェクト キー識別子を使用して証明書を参照しているだけの場合。  
  
- サービスのコンピューターに同じ公開キーを持つ複数の証明書が格納されており、それらの証明書に含まれる情報が異なる場合。  
  
- サービスがサブジェクト キー識別子と一致する証明書を取得したが、クライアントが使用する予定だったものではない場合。 WCF では、メッセージを受信し、署名を検証、WCF は、X.509 証明書の情報をから、クライアントが期待と異なる可能性がある管理者特権のあるクレームのセットにマップします。  
  
 これをできるだけ防ぐには、X.509 証明書を別の方法 (<xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial> の使用など) で参照します。  
  
## <a name="see-also"></a>関連項目

- [セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [情報の漏えい](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [サービス拒否](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [改変](../../../../docs/framework/wcf/feature-details/tampering.md)
- [サポートされていないシナリオ:](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)

---
title: WIF 要求プログラミング モデル
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
ms.openlocfilehash: 543db91eaa058a87cfe579a23abb710f21ec1b85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953596"
---
# <a name="wif-claims-programming-model"></a>WIF 要求プログラミング モデル
ASP.NET と Windows Communication Foundation (WCF) の開発者は、通常、IIdentity インターフェイスや IPrincipal インターフェイスを利用し、ユーザーの ID 情報を処理します。 .NET 4.5 では、Windows Identity Foundation (WIF) が統合され、あらゆるプリンシパルに対して常に要求が表示されるようになりました。次の図をご覧ください。

 ![WIF 要求プログラミング モデルを示す図。](./media/wif-claims-programming-model/wif-claims-programming-model.png)

 .NET 4.5 では、System.Security.Claims に新しい ClaimsPrincipal クラスと ClaimsIdentity クラスが含まれます (上の図をご覧ください)。 .NET のすべてのプリンシパルは ClaimsPrincipal から派生するようになりました。 ASP.NET の FormsIdentity や WindowsIdentity のような、組み込み ID クラスはすべて ClaimsIdentity から派生するようになりました。 同様に、GenericPrincipal や WindowsPrincipal など、組み込みのプリンシパル クラスはすべて ClaimsPrincipal から派生します。

 要求は <xref:System.Security.Claims.Claim> クラスにより表されます。 このクラスには、次の重要なプロパティがあります。

- <xref:System.Security.Claims.Claim.Type%2A> は要求の種類を表し、通常は URI です。 たとえば、電子メール アドレスの要求として表されます`http://schemas.microsoft.com/ws/2008/06/identity/claims/email`します。

- <xref:System.Security.Claims.Claim.Value%2A> には要求の値が含まれ、文字列として表されます。 たとえば、として電子メール アドレスを表すことができます"someone@contoso.com"。

- <xref:System.Security.Claims.Claim.ValueType%2A> は要求値の種類を表し、通常は URI です。 たとえば、文字列型は `http://www.w3.org/2001/XMLSchema#string` として表されます。 値の型は、XML スキーマに基づく QName になります。 WIF で有効な QName 値を出力するには、値の形式を `namespace#format` にする必要があります。 名前空間が適切に定義された名前空間ではない場合、生成された XML がスキーマ検証できない場合があります。その名前空間には XSD ファイルが発行されないためです。 既定の値の型は `http://www.w3.org/2001/XMLSchema#string` です。 安全に使用できる既知の値の型については、次を参照してください。、 [W3C XML スキーマ](https://www.w3.org/2001/XMLSchema)ページ。

- <xref:System.Security.Claims.Claim.Issuer%2A> は、要求を発行したセキュリティ トークン サービス (STS) の識別子です。 これは STS の URL か、STS を表す名前として表されます。たとえば、`https://sts1.contoso.com/sts` のようになります。

- <xref:System.Security.Claims.Claim.OriginalIssuer%2A> は、チェーン内の STS の数に関係なく、要求を最初に発行した STS の識別子です。 これは <xref:System.Security.Claims.Claim.Issuer%2A> のように表されます。

- <xref:System.Security.Claims.Claim.Subject%2A> はサブジェクトであり、その ID が調べられます。 これには、<xref:System.Security.Claims.ClaimsIdentity> が含まれます。

- <xref:System.Security.Claims.Claim.Properties%2A> はディクショナリであり、開発者はアプリケーション固有のデータを他のプロパティと共に送信できます。カスタム検証に利用できます。

## <a name="identity-delegation"></a>ID 委任
<xref:System.Security.Claims.ClaimsIdentity> の重要なプロパティは <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> です。 中間層がクライアントとして機能し、バックエンド サービスに要求を行う多層システムで、このプロパティは資格情報の委任を可能にします。

### <a name="accessing-claims-through-threadcurrentprincipal"></a>Thread.CurrentPrincipal 経由で要求にアクセスする
RP アプリケーションで現在のユーザーの要求セットにアクセスするには、`Thread.CurrentPrincipal` を使用します。

次のコード サンプルでは、このメソッドを利用し、System.Security.Claims.ClaimsIdentity を取得するしくみを確認できます。

```csharp
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;
```

詳細については、「 <xref:System.Security.Claims> 」を参照してください。

### <a name="role-claim-type"></a>役割という要求の種類
RP アプリケーションの構成の一環として、役割という要求の種類を決定します。 この種類の要求は、System.Security.Claims.ClaimsPrincipal.IsInRole(System.String) で利用されます。 既定の要求の種類は `http://schemas.microsoft.com/ws/2008/06/identity/claims/role` です。

### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>さまざまな種類のトークンから Windows Identity Foundation により抽出された要求
WIF は、すぐに使える、さまざまな認証メカニズムの組み合わせに対応しています。 次の表は、さまざまな種類のトークンから WIF が抽出する要求をまとめたものです。

|トークン型|生成された要求|Windows アクセス トークンにマッピング|
|-|-|-|
|SAML 1.1|1.System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope) からのすべての要求。<br />2.トークンに証明トークンが含まれる場合、XML でシリアル化した確認キーが含まれる `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` 要求。<br />3.Issuer 要素からの `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` 要求。<br />4.トークンに認証ステートメントが含まれる場合、AuthenticationMethod 要求と AuthenticationInstant 要求。|"SAML 1.1" の一覧に含まれる要求に加え、`http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` タイプの要求を除き、Windows 認証関連の要求が加わり、ID は WindowsClaimsIdentity で表されます。|
|SAML 2.0|"SAML 1.1" と同じ。|"Windows アカウントにマップされた SAML 1.1" と同じ。|
|X509|1.X500 の識別名、emailName、dnsName、SimpleName、UpnName、UrlName、拇印、RsaKey (これは X509Certificate2.PublicKey.Keyy プロパティから RSACryptoServiceProvider.ExportParameters メソッドを利用して抽出できます)、DsaKey (これは X509Certificate2.PublicKey.Key プロパティから DSACryptoServiceProvider.ExportParameters メソッドを利用して抽出できます)、X509 証明書の SerialNumber プロパティを持つ要求。<br />2.値 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509` を持つ AuthenticationMethod 要求。 証明書が XmlSchema DateTime 形式で検証されたときの値を持つ AuthenticationInstant 要求。|1.Windows アカウントの完全修飾ドメイン名が `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` 要求値として使用されます。 .<br />2.Windows にマッピングされていない X509 証明書からの要求と、Windows に証明書をマッピングして取得した Windows アカウントからの要求。|
|UPN|1.要求は、Windows 認証セクションの要求と似ています。<br />2.値 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password` を持つ AuthenticationMethod 要求。 パスワードが XmlSchema DateTime 形式で検証されたときの値を持つ AuthenticationInstant 要求。||
|Windows (Kerberos または NTLM)|1.など、アクセス トークンから生成された要求。PrimarySID、DenyOnlyPrimarySID、PrimaryGroupSID、DenyOnlyPrimaryGroupSID、GroupSID、DenyOnlySID、および名前<br />2.値 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows` を持つ AuthenticationMethod。 Windows アクセス トークンが XMLSchema DateTime 形式で作成されたときの値を持つ AuthenticationInstant。||
|RSA キー ペア|1.値 RSAKeyValue を持つ `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` 要求。<br />2.値 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature` を持つ AuthenticationMethod 要求。 RSA キーが XMLSchema DateTime 形式で認証された (つまり、署名が検証された) ときの値を持つ AuthenticationInstant 要求。||

|認証の種類|"AuthenticationMethod" 要求の URI|
|-|-|
|[Password]|`urn:oasis:names:tc:SAML:1.0:am:password`|
|Kerberos|`urn:ietf:rfc:1510`|
|SecureRemotePassword|`urn:ietf:rfc:2945`|
|TLSClient|`urn:ietf:rfc:2246`|
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|
|XmlDSig|`urn:ietf:rfc:3075`|
|指定されていません。|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|
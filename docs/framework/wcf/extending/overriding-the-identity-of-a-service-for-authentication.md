---
title: 認証のためのサービスの ID のオーバーライド
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 29529115847950dcaba255b0740bc5014557244f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635721"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>認証のためのサービスの ID のオーバーライド
クライアント資格情報の種類を選択すると、サービス メタデータで公開される ID の種類が指定されるため、通常、サービスで ID を設定する必要はありません。 たとえば、次の構成コードを使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素とセット、`clientCredentialType`属性を Windows にします。  

 次の Web サービス記述言語 (WSDL) コードは、定義済みのエンドポイントの ID を示しています。 特定のユーザー アカウントで自己ホスト型サービスとして、この例では、サービスが実行されている (username@contoso.com) でユーザー プリンシパル名 (UPN) id を含んでいる、アカウント名。 UPN は、Windows ドメインではユーザー ログオン名とも呼ばれます。  

 Id の設定を示すサンプル アプリケーションを参照してください。[サービス Id サンプル](../../../../docs/framework/wcf/samples/service-identity-sample.md)します。 サービス id の詳細については、次を参照してください。[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)します。  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos 認証と ID  
 既定では、Windows 資格情報を使用するサービスが構成されている場合、 [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素を含む、 [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md)または[ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md)要素が WSDL で生成されます。 サービスが実行されている場合、 `LocalSystem`、 `LocalService`、または`NetworkService`アカウント、サービス プリンシパル名 (SPN) が既定の形式で生成`host/` \< *hostname*> ためこれらのアカウントでは、コンピューターの SPN のデータにアクセスします。 Windows Communication Foundation (WCF) の形式で UPN が生成されます、サービスが別のアカウントで実行している場合\< *username*>@<*domainName* `>`. これらが生成されるのは、Kerberos 認証では、サービスを認証するために UPN または SPN をクライアントに提供する必要があるからです。  
  
 Setspn.exe ツールを使用して、他の SPN をドメイン内のサービスのアカウントに登録することもできます。 登録した SPN は、そのサービスの ID として使用できます。 このツールをダウンロードするには、次を参照してください。 [Windows 2000 リソース キット ツール。Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752)します。 ツールの詳細については、次を参照してください。 [Setspn の概要](https://go.microsoft.com/fwlink/?LinkId=61374)します。  
  
> [!NOTE]
>  ネゴシエーションを行わずに Windows 資格情報を使用するには、サービスのユーザー アカウントが Active Directory ドメインに登録された SPN にアクセスできる必要があります。 これは、次の方法で行うことができます。  
  
- サービスを実行するには、NetworkService アカウントまたは LocalSystem アカウントを使用します。 これらのアカウントは、コンピューターのコンピューター、Active Directory ドメインに参加したときに確立された SPN にアクセスのため、WCF は、サービスのメタデータ (WSDL) でサービスのエンドポイント内で適切な SPN 要素を自動的に生成します。  
  
- 任意の Active Directory ドメイン アカウントを使用してサービスを実行します。 この場合、そのドメイン アカウント用の SPN を確立します。これには、Setspn.exe ユーティリティ ツールを使用できます。 サービスのアカウントの SPN を作成した後にそのメタデータ (WSDL) を通じてサービスのクライアントに公開する WCF を構成します。 これを行うには、アプリケーション構成ファイルまたはコードを使用して、公開されるエンドポイントのエンドポイント ID を設定します。  
  
 Spn の詳細について、Kerberos プロトコル、および Active Directory を参照してください。 [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330)します。  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN または UPN が空の文字列の場合  
 空の文字列の SPN または UPN を設定した場合は、使用しているセキュリティ レベルと認証モードに応じて、次のようになります。  
  
- トランスポート レベルのセキュリティを使用している場合は、NTLM (NT LanMan) 認証が選択されます。  
  
- メッセージ レベルのセキュリティを使用している場合は、認証モードによっては認証に失敗する可能性があります。  
  
- `spnego` モードを使用し、`AllowNtlm` 属性を `false` に設定している場合は、認証に失敗します。  
  
- `spnego` モードを使用し、`AllowNtlm` 属性を `true` に設定している場合、UPN が空の場合は認証に失敗しますが、SPN が空の場合は認証に成功します。  
  
- Kerberos ダイレクト ("ワンショット" とも呼ばれます) を使用している場合は、認証に失敗します。  
  
### <a name="using-the-identity-element-in-configuration"></a>使用して、 \<identity > 構成要素  
 前の例で示したバインディングのクライアント資格情報の種類を Certificate に変更すると、生成される WSDL には、Base64 でシリアル化された ID 値用の X.509 証明書が含まれます。コードを次に示します`,`。 これは、Windows 以外のすべてのクライアント資格情報の種類の既定値です。  

 構成で <`identity`> 要素を使用したり、コードで ID を設定したりすることにより、既定のサービス ID の値を変更したり、ID の種類を変更したりすることが可能です。 値 `contoso.com` を使用してドメイン ネーム システム (DNS) ID を設定する構成コードを次に示します。  

### <a name="setting-identity-programmatically"></a>プログラムによる ID の設定  
 WCF が自動的に決定されるため、サービスは、id を明示的に指定がありません。 ただし、WCF は、必要な場合、エンドポイントで id を指定することです。 特定の DNS ID を持つ新しいサービス エンドポイントを追加するコードを次に示します。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [方法: カスタムのクライアント Id 検証機能を作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)

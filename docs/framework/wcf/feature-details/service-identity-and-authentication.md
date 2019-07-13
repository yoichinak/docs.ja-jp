---
title: サービス ID と認証
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: 695b6c24700fe42664944d6f9c1e03010248d86a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487747"
---
# <a name="service-identity-and-authentication"></a>サービス ID と認証
サービスの*エンドポイント id*は、サービスの Web サービス記述言語 (WSDL) から生成された値です。 この値は、すべてのクライアントに反映され、サービスの認証に使用されます。 クライアントがエンドポイントとの通信を開始し、サービスがクライアントに対して認証を行った後に、クライアントは、エンドポイント ID 値とエンドポイントの認証プロセスから返された実際の値を比較します。 この 2 つの値が一致した場合、クライアントは要求したサービス エンドポイントに接続していることを確認できます。 これは、関数に対する保護として*フィッシング*クライアントが悪意のあるサービスによってホストされるエンドポイントにリダイレクトされるようにすることで。  
  
 Id の設定を示すサンプル アプリケーションを参照してください。[サービス Id サンプル](../../../../docs/framework/wcf/samples/service-identity-sample.md)します。 エンドポイントとエンドポイント アドレスの詳細については、次を参照してください。[アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)します。  
  
> [!NOTE]
>  認証に NTLM (NT LanMan) を使用する場合、NTLM ではクライアントがサーバーを認証できないため、サービス ID はチェックされません。 NTLM はコンピューターが Windows ワークグループの一部である場合、または Kerberos 認証をサポートしていない古いバージョンの Windows が実行されている場合に使用されます。  
  
 Windows Communication Foundation (WCF) インフラストラクチャが、サービスを認証し、サービス id がエンドポイントで指定された id と一致する場合のみ、メッセージを送信するクライアントは、上にあるサービスにメッセージを送信するセキュリティで保護されたチャネルを開始するときにクライアントのアドレスを使用します。  
  
 ID の処理は、次の 2 段階から成ります。  
  
- デザイン時に、クライアント開発者は、(WSDL を通じて公開される) エンドポイントのメタデータでサービスの ID を確認します。  
  
- 実行時に、クライアント アプリケーションは、メッセージをサービスに送信する前に、サービスのセキュリティ資格情報のクレームを確認します。  
  
 クライアントでの ID の処理は、サービスでのクライアント認証と似ています。 セキュリティで保護されたサービスは、クライアントの資格情報が認証されるまでコードを実行しません。 同様に、クライアントは、サービスのメタデータによって事前に認識されている内容に基づいて、サービスの資格情報が認証されるまでメッセージを送信しません。  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> クラスの <xref:System.ServiceModel.EndpointAddress> プロパティは、クライアントによって呼び出されるサービスの ID を表します。 サービスはこの <xref:System.ServiceModel.EndpointAddress.Identity%2A> をサービスのメタデータ内に公開します。 クライアントの開発者を実行すると、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 、生成された構成が、サービスの値を格納する、サービス エンドポイントに対して<xref:System.ServiceModel.EndpointAddress.Identity%2A>プロパティ。 (セキュリティで構成されている) 場合は、WCF インフラストラクチャは、サービスが指定された id を所有しているかを確認します。  
  
> [!IMPORTANT]
>  メタデータには、サービスに要求される ID が含まれています。したがって、安全な方法 (サービスの HTTPS エンドポイントを作成するなど) でサービス メタデータを公開することをお勧めします。 詳細については、「[方法 :メタデータ エンドポイントをセキュリティで保護された](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)します。  
  
## <a name="identity-types"></a>ID の種類  
 サービスは、id の 6 つの種類を提供できます。 ID の各種類は、構成内の `<identity>` 要素に含めることのできる要素に対応します。 使用する ID の種類は、シナリオとサービスのセキュリティ要件によって異なります。 ID の各種類の説明を次の表に示します。  
  
|ID の種類|説明|一般的なシナリオ|  
|-------------------|-----------------|----------------------|  
|ドメイン ネーム システム (DNS)|この要素は X.509 証明書または Windows アカウントと一緒に使用します。 資格情報に指定されている DNS 名とこの要素で指定されている値とが比較されます。|DNS チェックを行うことにより、DNS 名またはサブジェクト名を含む証明書を使用できます。 同じ DNS 名またはサブジェクト名を使用して証明書が再発行された場合、ID 検査は引き続き有効になります。 証明書を再発行すると、新しい RSA キーが取得されますが、同じ DNS 名またはサブジェクト名が保持されます。 つまり、クライアントはサービスの ID 情報を更新する必要がありません。|  
|証明書。 `ClientCredentialType` が Certificate に設定されている場合の既定値です。|この要素は、クライアントと比較するための Base64 でエンコードされた X.509 証明書の値を指定します。<br /><br /> また、サービスを認証する資格情報として、CardSpace を使用する場合は、この要素を使用します。|この要素は、証明書の拇印の値に基づいて、認証を 1 つの証明書に制限します。 拇印の値は一意であるため、この制限によってより厳密な認証が可能になります。 これは、1 つ注意点があります。同じサブジェクト名を持つ証明書を再発行すると場合、新しい拇印もあります。 つまり、新しい拇印が認識されていない場合、クライアントはサービスを検証できなくなります。 証明書の拇印を見つける方法の詳細については、次を参照してください。[方法。証明書のサムプリントを取得](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)します。|  
|証明書参照|前述の証明書オプションと同じです。 ただし、この要素を使用すると、証明書の名前と証明書を取得するストアの場所を指定できます。|前述の証明書のシナリオと同じです。<br /><br /> 利点は、証明書ストアの場所を変更できることです。|  
|RSA|この要素は、クライアントと比較するための RSA キーの値を指定します。 これは証明書オプションに似ていますが、証明書の拇印を使用するのではなく、証明書の RSA キーを使用します。|RSA チェックを行うと、証明書の RSA キーに基づいて、単一の証明書に基づく認証に明確に制限できます。 これにより、RSA キーが変更された場合に既存のクライアントでサービスが使用できなくなるのと引き換えに、特定の RSA キーをより厳しく認証できます。|  
|ユーザー プリンシパル名 (UPN)。 `ClientCredentialType` が Windows に設定されており、サービス プロセスがシステム アカウントのいずれかで実行されていない場合の既定値です。|この要素は、サービスを実行中の UPN を指定します。 Kerberos プロトコルと Id のセクションを参照してください。 [Id 認証サービスのオーバーライド](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)します。|この設定では、サービスが特定の Windows ユーザー アカウントで実行されていることを確認します。 このユーザー アカウントは、現在ログオンしているユーザーである場合もあれば、特定のユーザー アカウントで実行されているサービスである場合もあります。<br /><br /> サービスが Active Directory 環境のドメイン アカウントで実行されている場合、この設定では Windows Kerberos セキュリティを利用します。|  
|サービス プリンシパル名 (SPN)。 `ClientCredentialType` が Windows に設定されており、サービス プロセスがシステム アカウント (LocalService、LocalSystem、または NetworkService) のいずれかで実行されている場合の既定値です。|この要素は、サービスのアカウントに関連付けられている SPN を指定します。 Kerberos プロトコルと Id のセクションを参照してください。 [Id 認証サービスのオーバーライド](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)します。|これにより、SPN と SPN に関連付けられた特定の Windows アカウントによってサービスが識別されます。<br /><br /> Setspn.exe ツールを使用すると、サービスのユーザー アカウントに対してコンピューター アカウントを関連付けることができます。<br /><br /> サービスがシステム アカウントのいずれか、または SPN 名に関連付けられたドメイン アカウントで実行されており、コンピューターが Active Directory 環境のドメインのメンバーである場合、この設定では Windows Kerberos セキュリティを利用します。|  
  
## <a name="specifying-identity-at-the-service"></a>サービスでの ID の指定  
 クライアント資格情報の種類を選択すると、サービス メタデータで公開される ID の種類が指定されるため、通常、サービスで ID を設定する必要はありません。 オーバーライドまたはサービス id を指定する方法の詳細については、次を参照してください。 [Id 認証サービスのオーバーライド](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)します。  
  
## <a name="using-the-identity-element-in-configuration"></a>使用して、 \<identity > 構成要素  
 上記の例で示したバインディングのクライアント資格情報の種類を `Certificate,` に変更すると、次のコードに示すように、生成される WSDL には、Base64 でシリアル化された、ID 値用の X.509 証明書が含まれます。 これは、Windows 以外のすべてのクライアント資格情報の種類の既定値です。  

 既定のサービス id の値を変更またはを使用して、id の種類を変更することができます、`<identity>`要素の構成またはコードで id を設定します。 値 `contoso.com` を使用してドメイン ネーム システム (DNS) ID を設定する構成コードを次に示します。  

## <a name="setting-identity-programmatically"></a>プログラムによる ID の設定  
 WCF が自動的に決定されるため、サービスは、id を明示的に指定がありません。 ただし、WCF は、必要な場合、エンドポイントで id を指定することです。 特定の DNS ID を持つ新しいサービス エンドポイントを追加するコードを次に示します。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>クライアントでの ID の指定  
 クライアント開発者の通常の使用、デザイン時に、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)クライアント構成を生成します。 生成された構成ファイル (クライアントが使用するもの) には、サービスの ID が含まれます。 たとえば、次のコードは、前の例で示した DNS ID を指定するサービスから生成されたものです。 クライアントのエンドポイント ID 値が、サービスのエンドポイント ID 値と一致していることに注意してください。 この場合、クライアントは、サービスの Windows (Kerberos) 資格情報を受け取るときに、この値が `contoso.com` であることを要求します。  

 サービスでクライアント資格情報の種類として Windows ではなく証明書を指定した場合は、証明書の DNS プロパティの値が `contoso.com` であることが要求されます (DNS プロパティが `null` の場合は、証明書のサブジェクト名が `contoso.com` である必要があります)。  
  
#### <a name="using-a-specific-value-for-identity"></a>ID の特定の値の使用  
 次のクライアント構成ファイルは、サービスの ID に特定の値を要求する方法を示しています。 次の例では、クライアントは 2 つのエンドポイントと通信できます。 1 つ目のエンドポイントは証明書の拇印で識別され、もう 1 つは証明書の RSA キーで識別されます。 つまり、公開キーと秘密キーのペアだけが含まれた証明書ですが、この証明書は信頼された証明機関によって発行されたものではありません。  

## <a name="identity-checking-at-run-time"></a>実行時の ID 検査  
 デザイン時には、クライアント開発者はサービスのメタデータで ID を確認します。 実行時には、サービスのエンドポイントを呼び出す前に ID 検査が実行されます。  
  
 ID 値は、メタデータで指定された認証の種類 (つまり、サービスで使用される資格情報の種類) に関連付けられています。  
  
 認証に X.509 証明書を使用するメッセージ レベルまたはトランスポート レベルの SSL (Secure Sockets Layer) を使用して認証を行うようにチャネルが構成されている場合、次の ID 値が有効になります。  
  
- DNS。 WCF により、SSL ハンドシェイク中に提供された証明書が、DNS が含まれているまたは`CommonName`DNS id をクライアントに指定された値と等しく (CN) 属性。 この検査は、サーバー証明書の有効性の確認とは別に行われます。 既定では、WCF は、サーバー証明書が信頼されたルート証明機関によって発行されたことを検証します。  
  
- 証明書。 SSL ハンドシェイク中に WCF により、リモート エンドポイントが id で指定された正確な証明書の値を提供します。  
  
- 証明書参照。 証明書と同じです。  
  
- RSA。 SSL ハンドシェイク中に WCF により、リモート エンドポイントが id で指定された正確な RSA キーを提供します。  
  
 サービスが認証に Windows 資格情報を使用するメッセージ レベルまたはトランスポート レベル SSL の認証を行い、資格情報をネゴシエートする場合、次の ID 値が有効になります。  
  
- DNS。 ネゴシエーションでは、DNS 名を確認できるように、サービスの SPN が渡されます。 SPN の形式は `host/<dns name>` です。  
  
- SPN。 サービスの明示的な SPN (例 : `host/myservice`) が返されます。  
  
- UPN。 サービス アカウントの UPN です。 UPN は、フォーム`username` @`domain`します。 たとえば、サービスがユーザー アカウントで実行されている場合、UPN は `username@contoso.com` のようになります。  
  
 (<xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティを使用して) ID をプログラムによって指定することは任意です。 ID が指定されておらず、クライアント資格情報の種類が Windows の場合、既定値は、先頭に "host/" リテラルが付加されたサービス エンドポイント アドレスのホスト名の部分に値が設定された SPN になります。 ID が指定されておらず、クライアント資格情報の種類が証明書の場合、既定値は `Certificate` です。 これは、メッセージ レベルとトランスポート レベルの両方のセキュリティに適用されます。  
  
## <a name="identity-and-custom-bindings"></a>ID とカスタム バインド  
 サービスの ID は使用するバインディングの種類によって異なるため、カスタム バインディングの作成時には、適切な ID が公開されていることを確認する必要があります。 たとえば、次のコード例では、セキュリティで保護された通信のブートストラップ バインディングの ID と、エンドポイントのバインディングの ID が一致していないため、セキュリティの種類と適合しない ID が公開されます。 セキュリティで保護された通信のバインディングでは DNS ID が設定され、<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> では UPN ID または SPN ID が設定されます。  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 バインドをスタックする方法の詳細について要素正しく、カスタム バインディングを参照してください[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)します。 カスタム バインディングの作成の詳細については、<xref:System.ServiceModel.Channels.SecurityBindingElement>を参照してください[方法。指定した認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)です。  
  
## <a name="see-also"></a>関連項目

- [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [方法: 指定した認証モード用の SecurityBindingElement を作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [方法: カスタムのクライアント Id 検証機能を作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [資格情報の種類の選択](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [ユーザー定義バインディングの作成](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [方法: 証明書のサムプリントを取得します。](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)

---
title: '方法: WSFederationHttpBinding を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: 3a6564683a856c8d1eb47b1569f156e0b6d5cc67
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636416"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>方法: WSFederationHttpBinding を作成する

Windows Communication Foundation (WCF) で、<xref:System.ServiceModel.WSFederationHttpBinding>クラス ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)構成で) フェデレーション サービスを公開するためのメカニズムを提供します。 これはクライアントに対して認証を要求するサービスであって、認証にはセキュリティ トークン サービスが発行するセキュリティ トークンが必要となります。 このトピックでは、必要な処理をコード中に埋め込む形、あるいは構成ファイルに必要な記述を加える形で、<xref:System.ServiceModel.WSFederationHttpBinding> の設定をする手順を説明します。 バインディングを作成すると、エンドポイントを設定してこのバインディングを使用できるようになります。

 基本的な手順の概略を以下に示します。

1. セキュリティ モードを選択します。 <xref:System.ServiceModel.WSFederationHttpBinding> には、メッセージ レベルでエンドツーエンドのセキュリティを提供する `Message` を指定できます。複数のホップや `TransportWithMessageCredential` にまたがる通信であってもこれは有効です。クライアントとサービスが HTTPS 上で直接接続できる場合に、特に性能を発揮します。

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> には、セキュリティ モードとして `None` を指定することもできます。 このモードは安全性が低く、デバッグ目的での使用のみを目的としています。 サービス エンドポイントが展開された場合、<xref:System.ServiceModel.WSFederationHttpBinding>そのセキュリティ モードを設定すると`None`、結果として得られるクライアントのバインド (によって生成された、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) は、<xref:System.ServiceModel.WSHttpBinding>で、セキュリティ モード`None`します。

     `WSFederationHttpBinding` の場合、システムに組み込まれている他のバインディングとは違って、クライアント資格情報の種類を選択する必要はありません。 これは、常に、発行されたトークンを資格情報として使うからです。 WCF では、指定された発行者からトークンを取得し、そのトークンをクライアントの認証にサービスを示します。

2. フェデレーション クライアントの場合、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> プロパティの値として、セキュリティ トークン サービスの URL を指定します。 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> としてバインディングを指定し、セキュリティ トークン サービスとの通信に使用します。

3. 省略可能です。 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> プロパティの値として、トークンの種類の URI (Uniform Resource Identifier) を指定します。 フェデレーション サービスについては、提示されれば受理できるトークンの種類を指定します。 フェデレーション クライアントについては、セキュリティ トークン サービスに要求するトークンの種類を指定します。

     トークンの種類を指定しなければ、クライアント側ではその URI なしで WS-Trust のセキュリティ トークン要求 (RTS) を生成します。また、サービス側では、クライアントが既定で SAML (Security Assertions Markup Language) 1.1 のトークンを提示して認証するものと想定します。

     SAML 1.1 トークンの URI は`http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`します。

4. 任意。 フェデレーション サービスの場合、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> プロパティの値として、セキュリティ トークン サービスのメタデータ URL を指定します。 メタデータ エンドポイントは、サービスがメタデータを公開するよう設定されている場合に、クライアントが適切なバインディング/エンドポイントのペアを選択するために必要です。 メタデータの公開の詳細については、次を参照してください。[メタデータの公開](publishing-metadata.md)します。

 他に設定できるプロパティとしては、発行されたトークンの証明キーとして使用するキーの種類、クライアント/サーバー間で使用するアルゴリズム スイート、サービス資格情報をネゴシエートするか明示的に指定するか、トークンに入っていればそれに応じてサービス側で処理できるクレームの種類、クライアントがセキュリティ トークン サービスに送信する要求に追加しなければならない他の XML 要素などがあります。

> [!NOTE]
>  `NegotiateServiceCredential` プロパティが意味をなすのは、`SecurityMode` の設定値が `Message` である場合に限ります。 `SecurityMode` の設定値が `TransportWithMessageCredential` であれば、`NegotiateServiceCredential` プロパティは無視されます。

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>必要な処理をコード中に埋め込む形で WSFederationHttpBinding を設定するには

1. <xref:System.ServiceModel.WSFederationHttpBinding> のインスタンスを作成します。

2. 必要に応じて、<xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.WSFederationHttpSecurityMode> または <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> に設定します。 場合以外の場合は、するアルゴリズム スイート<xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A>が必要ですが、設定、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A>プロパティから取得した値を<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>します。

3. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティに適切な値を設定します。

4. 設定、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>プロパティを<xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey`またはします。`AsymmetricKey` 必要に応じて。

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> プロパティに適切な値を設定します。 WCF は、値が設定されていない場合`http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`、SAML 1.1 トークンを示します。

6. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では省略可能。 セキュリティ トークン サービスのアドレスと ID 情報が設定された <xref:System.ServiceModel.EndpointAddress> を作成し、この <xref:System.ServiceModel.EndpointAddress> インスタンスを <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> プロパティに代入します。

7. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では不要。 作成、<xref:System.ServiceModel.Channels.Binding>の`SecurityTokenService`を割り当てると、<xref:System.ServiceModel.Channels.Binding>インスタンスを<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A>プロパティ。

8. クライアント側では不要。サービス側では省略可能。 セキュリティ トークン サービスのメタデータ用の <xref:System.ServiceModel.EndpointAddress> インスタンスを作成し、`IssuerMetadataAddress` プロパティに代入します。

9. クライアント側、サービス側とも省略可能。 必要な数の <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> インスタンスを生成し、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> プロパティで返されたコレクションに追加します。

10. クライアント側、サービス側とも省略可能。 必要な数の <xref:System.Xml.XmlElement> インスタンスを生成し、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> プロパティで返されたコレクションに追加します。

## <a name="to-create-a-federated-endpoint-in-configuration"></a>構成ファイルに必要な記述を加える形でフェデレーション エンドポイントを作成するには

1. 作成、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)の子として、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)アプリケーション構成ファイル内の要素。

2. 作成、 [\<バインド >](../../../../docs/framework/misc/binding.md)要素の子として[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)設定と、`name`属性に適切な値。

3. 作成、`<security>`要素の子として、 [\<バインド >](../../../../docs/framework/misc/binding.md)要素。

4. 必要に応じて、`mode` 要素の `<security>` 属性値に `Message` または `TransportWithMessageCredential` を設定します。

5. `<message>` 要素の子要素として `<security>` 要素を作成します。

6. 省略可能です。 `algorithmSuite` 要素の `<message>` 属性に適切な値を設定します。 既定値は、`Basic256` です。

7. 省略可能です。 非対称証明キーが必要ならば、`issuedKeyType` 要素の `<message>` 属性を `AsymmetricKey` に設定します。 既定値は、`SymmetricKey` です。

8. 省略可能です。 `issuedTokenType` 要素の `<message>` 属性を設定します。

9. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では省略可能。 `<issuer>` 要素の子要素として `<message>` 要素を作成します。

10. `address` 要素に `<issuer>` 属性を設定し、セキュリティ トークン サービスがトークン要求を受け付けるアドレスを指定します。

11. 省略可能です。 `<identity>` 子要素を追加し、セキュリティ トークン サービスの識別子を指定します。

12. 詳細については、次を参照してください。[サービス Id と認証](service-identity-and-authentication.md)します。

13. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では不要。 作成、 [\<バインド >](../../../../docs/framework/misc/binding.md)セキュリティ トークン サービスとの通信に使用できるバインディング セクション内の要素。 バインディングの作成の詳細については、次を参照してください。[方法。構成でサービス バインディング指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。

14. `binding` 要素の `bindingConfiguration` 属性および `<issuer>` 属性に設定して、前の手順で作成したバインディングを指定します。

15. クライアント側では不要。サービス側では省略可能。 <`<issuerMetadata>`> 要素の子要素として `message` 要素を作成します。 次に、`address` 要素の `<issuerMetadata>` 属性に、セキュリティ トークン サービスがメタデータを公開するアドレスを指定します。 オプションで、`<identity>` 子要素を追加し、セキュリティ トークン サービスの識別子を指定します。

16. クライアント側、サービス側とも省略可能。 `<claimTypeRequirements>` 要素の子要素として `<message>` 要素を追加します。 必須およびオプションのクレームを指定に追加することで、サービスが依存する[\<追加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)要素を`<claimTypeRequirements>`要素と、要求を指定する型、`claimType`属性。 さらに、`isOptional` 属性に、クレームが必須か省略可能かを設定します。

## <a name="example"></a>例

強制的に `WSFederationHttpBinding` を設定するコード例を以下に示します。

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>関連項目

- [フェデレーション](federation.md)
- [フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)
- [方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にします。](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)

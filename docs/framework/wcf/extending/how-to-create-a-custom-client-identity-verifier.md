---
title: '方法: カスタム クライアント ID 検証機能を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: d8529929870b14611c136221f1eefe3eb4ba3d42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338996"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>方法: カスタム クライアント ID 検証機能を作成する
*Identity*機能の Windows Communication Foundation (WCF) が事前に予想されるサービスの id を指定するクライアントを使用できます。 サーバーがクライアントに対して自身を認証するたびに、ID がこの予想 ID と照合されます (Id とそのしくみの詳細については、次を参照してください[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。)。  
  
 必要に応じて、カスタム ID 検証機能を使用して検証をカスタマイズできます。 たとえば、追加のサービス ID 検証チェックを実行できます。 この例では、カスタム ID 検証機能で、サーバーから戻された X.509 証明書の追加のクレームをチェックします。 サンプル アプリケーションでは、次を参照してください。[サービス Id サンプル](../../../../docs/framework/wcf/samples/service-identity-sample.md)します。  
  
### <a name="to-extend-the-endpointidentity-class"></a>EndpointIdentity クラスを拡張するには  
  
1. <xref:System.ServiceModel.EndpointIdentity> クラスから派生する新しいクラスを定義します。 拡張子 `OrgEndpointIdentity` に名前を付ける例を次に示します。  
  
2. 拡張 <xref:System.ServiceModel.Security.IdentityVerifier> クラスで使用するプライベート メンバーとプロパティを追加し、サービスによって返されたセキュリティ トークンのクレームに対して ID チェックを実行します。 この例では、`OrganizationClaim` プロパティを定義します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>IdentityVerifier クラスを拡張するには  
  
1. <xref:System.ServiceModel.Security.IdentityVerifier> から派生する新しいクラスを定義します。 拡張子 `CustomIdentityVerifier` に名前を付ける例を次に示します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> メソッドをオーバーライドします。 このメソッドは、ID チェックが成功したか失敗したかを判定します。  
  
3. `CheckAccess` メソッドには 2 つのパラメーターがあります。 1 つ目は <xref:System.ServiceModel.EndpointIdentity> クラスのインスタンスです。 2 つ目は <xref:System.IdentityModel.Policy.AuthorizationContext> クラスのインスタンスです。  
  
     メソッド実装では、<xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> クラスの <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティから返されたクレームのコレクションを検査し、必要に応じて認証チェックを実行します。 この例では、まず種類が "識別名" のクレームをすべて検索し、次にその名前と <xref:System.ServiceModel.EndpointIdentity> の拡張 (`OrgEndpointIdentity`) とを比較します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>TryGetIdentity メソッドを実装するには  
  
1. <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> メソッドを実装します。このメソッドは、クライアントが <xref:System.ServiceModel.EndpointIdentity> クラスのインスタンスを返すことができるかどうかを判定します。 WCF インフラストラクチャの実装を呼び出す、`TryGetIdentity`メッセージからサービスの id を取得するには、最初のメソッド。 次に、インフラストラクチャは、返された `CheckAccess` と `EndpointIdentity` を使用して <xref:System.IdentityModel.Policy.AuthorizationContext> 実装を呼び出します。  
  
2. `TryGetIdentity` メソッドに次のコードを追加します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>カスタム バインディングを実装してカスタム ID 検証機能を設定するには  
  
1. <xref:System.ServiceModel.Channels.Binding> オブジェクトを返すメソッドを作成します。 この例は、まず <xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードを <xref:System.ServiceModel.SecurityMode.Message>、<xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> を <xref:System.ServiceModel.MessageCredentialType.None> に設定します。  
  
2. <xref:System.ServiceModel.Channels.BindingElementCollection> メソッドを使用して <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> を作成します。  
  
3. コレクションから <xref:System.ServiceModel.Channels.SecurityBindingElement> を返し、それを <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 変数にキャストします。  
  
4. <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> クラスの <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> プロパティを、以前作成した `CustomIdentityVerifier` クラスの新しいインスタンスに設定します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. 返されたカスタム バインドを使用してクライアントのインスタンスとクラスを作成します。 これにより、クライアントは、次のコードに示すようにサービスのカスタム ID 検証チェックを実行できるようになります。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>例  
 <xref:System.ServiceModel.Security.IdentityVerifier> クラスの完全な実装方法の例を次に示します。  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>例  
 <xref:System.ServiceModel.EndpointIdentity> クラスの完全な実装方法の例を次に示します。  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [サービス ID サンプル](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)

---
title: '方法: サポート資格情報を作成する'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 3ae2b59abf59b0256741ef4e908305d9f4350b4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093710"
---
# <a name="how-to-create-a-supporting-credential"></a>方法: サポート資格情報を作成する
カスタムのセキュリティ スキームでは、複数の資格情報が必要になることがあります。 たとえば、サービスが、ユーザー名とパスワードだけでなく、クライアントが 18 歳以上であることを証明する資格情報もクライアントに要求することがあります。 2 番目の資格情報が、*資格情報をサポートしている*します。 このトピックでは、Windows Communication Foundation (WCF) クライアントでこのような資格情報を実装する方法について説明します。  
  
> [!NOTE]
>  サポート資格情報の仕様は、WS-SecurityPolicy 仕様の一部です。 詳細については、次を参照してください。 [Web サービス セキュリティ仕様](https://go.microsoft.com/fwlink/?LinkId=88537)します。  
  
## <a name="supporting-tokens"></a>トークンのサポート  
 メッセージのセキュリティを使用する場合に簡単に言うと、*プライマリ資格情報*は常に (たとえば、X.509 証明書または Kerberos チケット) メッセージをセキュリティで保護するために使用します。  
  
 セキュリティ バインディングを使用して、仕様で定義された、*トークン*メッセージ交換をセキュリティで保護します。 A*トークン*はセキュリティ資格情報を表したものです。  
  
 セキュリティ バインディングは、セキュリティ バインディング ポリシーで特定されたプライマリ トークンを使用して、署名を作成します。 この署名と呼ばれます、*メッセージ署名*します。  
  
 メッセージ署名に関連付けられたトークンによって提供されるクレームを増やすために、追加のトークンを指定できます。  
  
## <a name="endorsing-signing-and-encrypting"></a>保証、署名、および暗号化  
 サポート資格情報の結果、*サポート トークン*メッセージ内で送信されます。 WS-SecurityPolicy 仕様では、次の表に示すように、サポート トークンをメッセージに追加する方法が 4 つ定義されています。  
  
|目的|説明|  
|-------------|-----------------|  
|符号付き|サポート トークンはセキュリティ ヘッダーに追加され、メッセージ署名によって署名されます。|  
|保証|*保証トークン*メッセージ署名します。|  
|署名および保証|署名付き保証トークンは、メッセージ署名から生成された `ds:Signature` 要素全体を署名し、それ自体がこのメッセージ署名によって署名されます。つまり、両方のトークン (メッセージ署名に使用されるトークンと署名付き保証トークン) がお互いに署名します。|  
|署名および暗号化|暗号化された署名付きサポート トークンは、`wsse:SecurityHeader` に表示されたときに暗号化されている署名付きサポート トークンです。|  
  
## <a name="programming-supporting-credentials"></a>サポート資格情報のプログラミング  
 サポート トークンを作成する必要がありますを使用するサービスを作成する、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)します。 (詳細については、次を参照してください。[方法。SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md))。  
  
 カスタム バインドを作成する最初の手順は、次の 3 種類のいずれかのセキュリティ バインド要素を作成することです。  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 すべてのクラスは、次の 4 つの関連プロパティを備えた <xref:System.ServiceModel.Channels.SecurityBindingElement> から継承します。  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>スコープ  
 サポート資格情報には、次の 2 つのスコープがあります。  
  
-   *エンドポイント サポート トークン*エンドポイントのすべての操作をサポートします。 つまり、サポート トークンによって表される資格情報は、エンドポイントの任意の操作が呼び出されたときにいつでも使用できます。  
  
-   *操作サポート トークン*特定のエンドポイントの操作のみをサポートします。  
  
 プロパティ名に示されているように、サポート資格情報は必須またはオプションのどちらかになることができます。 つまり、サポート資格情報は必須ではありませんが、存在する場合は使用され、存在しない場合も認証は失敗しません。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>サポート資格情報を備えたカスタム バインディングを作成するには  
  
1.  セキュリティ バインド要素を作成します。 次の例では、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 認証モードで `UserNameForCertificate` を作成します。 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> メソッドを使用します。  
  
2.  サポート パラメーターを対応するプロパティ (`Endorsing`、`Signed`、`SignedEncrypted`、または `SignedEndorsed`) によって返される型のコレクションに追加します。 <xref:System.ServiceModel.Security.Tokens> 名前空間に存在する型には、<xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters> など、一般的に使用される型があります。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを作成し、<xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> クラスのインスタンスを、Endorsing プロパティによって返されるコレクションに追加する例を次に示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>関連項目

- [方法: SecurityBindingElement を使用してカスタム バインドを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)

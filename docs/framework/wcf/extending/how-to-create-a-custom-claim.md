---
title: '方法: カスタム クレームを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 1892e910a86e01b7b2ee0f6a2403ad7af4688808
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295381"
---
# <a name="how-to-create-a-custom-claim"></a>方法: カスタム クレームを作成する
Id モデル インフラストラクチャでは、Windows Communication Foundation (WCF) を作成するための組み込みクレームの種類とヘルパー関数の権限のセットを提供する<xref:System.IdentityModel.Claims.Claim>その種類と権限を持つインスタンス。 この組み込みクレームは、モデルに関する情報を WCF がサポートするクライアント資格情報の種類に既定で設計されています。 多くの場合はこの組み込みクレームで十分ですが、一部のアプリケーションでカスタム クレームが必要になる場合があります。 クレームは、クレームが適用されるリソースを示すクレームの種類と、リソースにアサートされる権限で構成されます。 このトピックでは、カスタム クレームを作成する方法について説明します。  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>プリミティブ データ型に基づくカスタム クレームを作成するには  
  
1. クレームの種類、リソースの値、<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> コンストラクターへの権限を渡すことで、カスタム クレームを作成します。  
  
    1.  クレームの種類の一意の値を指定します。  
  
         クレームの種類は一意の文字列識別子です。 カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。 WCF で定義されている要求の種類の一覧は、次を参照してください。、<xref:System.IdentityModel.Claims.ClaimTypes>クラス。  
  
    2.  プリミティブ データ型とリソースの値を選択します。  
  
         リソースはオブジェクトです。 CLR 型のリソースにはプリミティブを指定できます。たとえば、<xref:System.String> や <xref:System.Int32>、または任意のシリアル化可能な型を指定できます。 リソースの CLR 型は、要求は、さまざまなポイントに、WCF によってシリアル化されるため、シリアル化可能である必要があります。 プリミティブ型はシリアル化できます。  
  
    3.  WCF またはカスタムの権利に一意の値によって定義されている権限を選択します。  
  
         権限は一意の文字列識別子です。 WCF によって定義されている権限が定義されている、<xref:System.IdentityModel.Claims.Rights>クラス。  
  
         カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。  
  
         次のコード例では、`http://example.org/claims/simplecustomclaim` という名前のリソース用の `Driver's License` というクレームの種類と <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限を持つカスタム クレームを作成します。  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>プリミティブ以外のデータ型に基づくカスタム クレームを作成するには  
  
1. クレームの種類、リソースの値、<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> コンストラクターへの権限を渡すことで、カスタム クレームを作成します。  
  
    1.  クレームの種類の一意の値を指定します。  
  
         クレームの種類は一意の文字列識別子です。 カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。 WCF で定義されている要求の種類の一覧は、次を参照してください。、<xref:System.IdentityModel.Claims.ClaimTypes>クラス。  
  
    2.  リソース用のシリアル化可能な、プリミティブ型以外の型を選択または定義します。  
  
         リソースはオブジェクトです。 リソースの CLR 型は、要求は、さまざまなポイントに、WCF によってシリアル化されるため、シリアル化可能である必要があります。 プリミティブ型は既にシリアル化できます。  
  
         新しい型を作成する場合は、<xref:System.Runtime.Serialization.DataContractAttribute> をクラスに適用します。 また、クレームの一部としてシリアル化する必要のある新しい型のすべてのメンバーにも <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用します。  
  
         `MyResourceType` というカスタム リソース型を定義するコード例を次に示します。  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  WCF またはカスタムの権利に一意の値によって定義されている権限を選択します。  
  
         権限は一意の文字列識別子です。 WCF によって定義されている権限が定義されている、<xref:System.IdentityModel.Claims.Rights>クラス。  
  
         カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。  
  
         次のコード例では、`http://example.org/claims/complexcustomclaim` というクレームの種類 (`MyResourceType` カスタム リソース型) および <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限を持つカスタム クレームを作成します。  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>例  
 次のコード例で、プリミティブ リソース型を持つカスタム クレームと、プリミティブ以外のリソース型を持つカスタム クレームの作成方法を示します。  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)

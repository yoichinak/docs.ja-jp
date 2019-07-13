---
title: '方法: カスタム承認ポリシーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 05130e809356369ee2b43d9af86acf69fe527e9a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902331"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>方法: カスタム承認ポリシーを作成する
Id モデル インフラストラクチャでは、Windows Communication Foundation (WCF) には、クレーム ベースの承認モデルがサポートしています。 クレームは、トークンから抽出され、状況に応じてカスタム承認ポリシーによって処理されてから、承認決定を行う際に確認できる <xref:System.IdentityModel.Policy.AuthorizationContext> に格納されます。 カスタム ポリシーを使用して、入力トークンからのクレームを、アプリケーションが要求するクレームに変換することができます。 この方法では、WCF がサポートする、さまざまなトークンの種類から提供されるさまざまなクレームの詳細からアプリケーション層を隔離することができます。 このトピックでは、カスタム承認ポリシーの実装方法と、サービスで使用するポリシーのコレクションにカスタム承認ポリシーを追加する方法について説明します。  
  
### <a name="to-implement-a-custom-authorization-policy"></a>カスタム承認ポリシーを実装するには  
  
1. <xref:System.IdentityModel.Policy.IAuthorizationPolicy> から派生する新しいクラスを定義します。  
  
2. クラスのコンストラクター内で一意の文字列を生成し、プロパティがアクセスされたときにその文字列を返すことによって、読み取り専用の <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> プロパティを実装します。  
  
3. ポリシーの発行者を表す <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> を返すことによって、読み取り専用の <xref:System.IdentityModel.Claims.ClaimSet> プロパティを実装します。 これは、アプリケーションを表す `ClaimSet`、または組み込み `ClaimSet` (静的な `ClaimSet` プロパティから返される <xref:System.IdentityModel.Claims.ClaimSet.System%2A> など) にすることができます。  
  
4. 次の手順に従って、<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> メソッドを実装します。  
  
### <a name="to-implement-the-evaluate-method"></a>Evaluate メソッドを実装するには  
  
1. このメソッドには、<xref:System.IdentityModel.Policy.EvaluationContext> クラスのインスタンスとオブジェクト参照の 2 つのパラメーターが渡されます。  
  
2. カスタム承認ポリシーを追加した場合<xref:System.IdentityModel.Claims.ClaimSet>インスタンスの現在のコンテンツに関係なく、 <xref:System.IdentityModel.Policy.EvaluationContext>、各追加`ClaimSet`呼び出すことによって、<xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29>メソッドと戻り値`true`から、<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>メソッド。 `true` を返すことは、承認インフラストラクチャに対して、承認ポリシーがその処理を完了したため、もう一度呼び出す必要がないことを知らせることになります。  
  
3. カスタム承認ポリシーで `EvaluationContext` 内に特定のクレームが既に存在するときにのみクレーム セットを追加する場合は、`ClaimSet` プロパティから返された <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> インスタンスを調べて、該当するクレームを見つけます。 クレームが見つかった場合は、<xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> メソッドを呼び出して新しいクレーム セットを追加します。追加するクレーム セットがない場合は、`true` を返し、承認インフラストラクチャに承認ポリシーがその処理を完了したことを知らせます。 クレームが存在しない場合は `false` を返し、他の承認ポリシーで `EvaluationContext` にさらにクレーム セットを追加する場合は、もう一度承認ポリシーを呼び出す必要があることを知らせます。  
  
4. より複雑な処理シナリオでは、<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> メソッドの 2 番目のパラメーターを使用して、特定の評価のために <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> メソッドに対するその後の呼び出し時に承認インフラストラクチャから返される状態変数を格納します。  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>構成を使用してカスタム承認ポリシーを指定するには  
  
1. `policyType` 要素の `add` 要素にある `authorizationPolicies` 要素の `serviceAuthorization` 属性でカスタム承認ポリシーの種類を指定します。  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>コードを使用してカスタム承認ポリシーを指定するには  
  
1. <xref:System.Collections.Generic.List%601> の <xref:System.IdentityModel.Policy.IAuthorizationPolicy> を作成します。  
  
2. カスタム承認ポリシーのインスタンスを作成します。  
  
3. リストに承認ポリシー インスタンスを追加します。  
  
4. カスタム承認ポリシーごとに手順 2. と 3. を繰り返します。  
  
5. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> プロパティにリストの読み取り専用バージョンを割り当てます。  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>例  
 完成した <xref:System.IdentityModel.Policy.IAuthorizationPolicy> の実装例を次に示します。  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [方法: クレームを比較します。](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [方法: サービスのカスタム承認マネージャーを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)

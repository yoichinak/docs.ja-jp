---
title: '方法: サービスで使用するカスタム承認マネージャーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: ffdfe41db05eb5f2dd55a233f8ed646401777d0f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040292"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>方法: サービスで使用するカスタム承認マネージャーを作成する

Windows Communication Foundation (WCF) の Id モデルインフラストラクチャでは、拡張可能なクレームベースの承認モデルがサポートされています。 クレームはトークンから抽出され、状況に応じてカスタム承認ポリシーによって処理されてから、<xref:System.IdentityModel.Policy.AuthorizationContext> に格納されます。 承認マネージャーは、<xref:System.IdentityModel.Policy.AuthorizationContext> 内のクレームを検査して承認に関する決定を行います。

既定では、承認に関する決定は、<xref:System.ServiceModel.ServiceAuthorizationManager> クラスによって行われますが、カスタム承認マネージャーを作成することによってオーバーライドできます。 カスタム承認マネージャーを作成するには、<xref:System.ServiceModel.ServiceAuthorizationManager> から派生するクラスを作成し、<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッドを実装します。 承認に関する決定は、<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッド内で行われます。このメソッドは、アクセスが許可されている場合は `true` を返し、拒否されている場合は `false` を返します。

承認決定がメッセージ本文の内容に依存する場合は、<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドを使用します。

パフォーマンスの問題があるので、可能であればアプリケーションを再デザインして、承認決定でメッセージ本文にアクセスする必要がないようにしてください。

サービスのカスタム承認マネージャーは、コードまたは構成に登録できます。

### <a name="to-create-a-custom-authorization-manager"></a>カスタム承認マネージャーを作成するには

1. <xref:System.ServiceModel.ServiceAuthorizationManager> クラスからクラスを派生させます。

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> メソッドをオーバーライドします。

    <xref:System.ServiceModel.OperationContext> メソッドに渡される <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> を使用して、承認に関する決定を行います。

    承認に関する決定を行うために、<xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> メソッドを使用してカスタム クレーム `http://www.contoso.com/claims/allowedoperation` を検索する方法を次のコード例に示します。

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a>コードを使用してカスタム承認マネージャーを登録するには

1. カスタム承認マネージャーのインスタンスを作成し、これを <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> プロパティに割り当てます。

    <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> には、<xref:System.ServiceModel.ServiceHostBase.Authorization%2A> プロパティを使用してアクセスできます。

    `MyServiceAuthorizationManager` カスタム承認マネージャーを登録するコード例を次に示します。

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>構成を使用してカスタム承認マネージャーを登録するには

1. サービスの構成ファイルを開きます。

2. [動作\<>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)に[ serviceauthorization\<>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を追加します。

    Serviceauthorization `serviceAuthorizationManagerType` > に属性を追加し、その値をカスタム承認マネージャーを表す型に設定します。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)

3. クライアントとサービスの間の通信をセキュリティで保護するバインディングを追加します。

    この通信用に選択されたバインディングによって、<xref:System.IdentityModel.Policy.AuthorizationContext> に追加されるクレームが決まります。これは、カスタム承認マネージャーが承認に関する決定を行うために使用します。 システム指定のバインディングの詳細については、「[システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。

4. サービス > 要素を追加`behaviorConfiguration`し、属性の値を[ \<behavior >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素の name 属性の値に設定することによって、動作をサービスエンドポイントに関連付けます。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)

    サービスエンドポイントの構成の詳細について[は、「」を参照してください。構成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)にサービスエンドポイントを作成します。

    カスタム承認マネージャー `Samples.MyServiceAuthorizationManager` を登録するコード例を次に示します。

    ```xml
    <configuration>
      <system.serviceModel>
        <services>
          <service
              name="Microsoft.ServiceModel.Samples.CalculatorService"
              behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <endpoint address=""
                      binding="wsHttpBinding_Calculator"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
          </service>
        </services>
        <bindings>
          <WSHttpBinding>
           <binding name = "wsHttpBinding_Calculator">
             <security mode="Message">
               <message clientCredentialType="Windows"/>
             </security>
            </binding>
          </WSHttpBinding>
        </bindings>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />
             </behavior>
         </serviceBehaviors>
       </behaviors>
      </system.serviceModel>
    </configuration>
    ```

    > [!WARNING]
    > serviceAuthorizationManagerType を指定する場合、文字列には、完全修飾型名、 コンマ、型が定義されているアセンブリの名前が含まれている必要があります。 アセンブリ名を省略した場合、WCF は、System.ServiceModel.dll から型を読み込もうとします。

## <a name="example"></a>例

<xref:System.ServiceModel.ServiceAuthorizationManager> メソッドのオーバーライドを含む <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> クラスの基本実装を次のコード例に示します。 このコード例は、<xref:System.IdentityModel.Policy.AuthorizationContext> のカスタム クレームを調べ、そのカスタム クレームのリソースが `true` のアクション値と一致した場合に <xref:System.ServiceModel.OperationContext> を返します。 <xref:System.ServiceModel.ServiceAuthorizationManager>クラスの完全な実装については、「[承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)」を参照してください。

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)

---
title: 資格情報ネゴシエーションを使用しない Windows クライアントを使用するメッセージ セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 43bc222bb69aafa3fa3492d79d35fbc492055ead
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344833"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>資格情報ネゴシエーションを使用しない Windows クライアントを使用するメッセージ セキュリティ
次のシナリオでは、Windows Communication Foundation (WCF) クライアントと Kerberos のプロトコルで保護されたサービスを説明します。  
  
 サービスとクライアントは、いずれも同じドメインまたは信頼できるドメインに配置されています。  
  
> [!NOTE]
>  このシナリオの違いと[メッセージ セキュリティと Windows クライアント](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)はこのシナリオが、アプリケーション メッセージを送信する前に、サービスとサービスの資格情報をネゴシエートしません。 また、このシナリオでは Kerberos プロトコルを使用するので、Windows ドメイン環境が必要になります。  
  
 ![メッセージ資格情報ネゴシエーションを使用しないセキュリティ](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|特徴|説明|  
|--------------------|-----------------|  
|セキュリティ モード|メッセージ|  
|相互運用性|○ Kerberos トークン プロファイル互換クライアントを使用する WS-Security|  
|認証 (サーバー)|サーバーとクライアントの相互認証|  
|認証 (クライアント)|サーバーとクライアントの相互認証|  
|整合性|はい|  
|機密性|はい|  
|Transport|HTTP|  
|バインディング|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>サービス  
 次のコードと構成は、別々に実行します。 次のいずれかの操作を行います。  
  
-   構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。  
  
-   提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。  
  
### <a name="code"></a>コード  
 次のコードは、メッセージ セキュリティを使用するサービス エンドポイントを作成します。 このコードは、サービス資格情報のネゴシエーションとセキュリティ コンテキスト トークン (SCT) の確立を無効にします。  
  
> [!NOTE]
>  ネゴシエートせずに Windows の資格情報を使用するには、サービスのユーザー アカウントが、Active Directory ドメインを使用して登録されたサービス プリンシパル名 (SPN) にアクセスする必要があります。 これは次の 2 つの方法で実行できます。  
  
1. `NetworkService` アカウントまたは `LocalSystem` アカウントを使用してサービスを実行します。 サービスのメタデータ (Web サービスの説明でサービスのエンドポイント内で適切な SPN 要素を WCF が自動的に生成されますので、これらのアカウントでは、コンピューターのコンピューター、Active Directory ドメインに参加したときに確立された SPN にアクセス、言語、または WSDL) です。  
  
2. 任意の Active Directory ドメイン アカウントを使用してサービスを実行します。 この場合、そのドメイン アカウント用の SPN を確立する必要があります。 これを行うには、Setspn.exe ユーティリティ ツールを使用する方法があります。 サービスのアカウントの SPN が作成されると、そのメタデータ (WSDL) を通じてサービスのクライアントに公開する WCF を構成します。 これを行うには、アプリケーション構成ファイルまたはコードのどちらかを使用して、公開されるエンドポイントのエンドポイント ID を設定します。 プログラムで ID を公開する方法を次の例に示します。  
  
 Spn の詳細について、Kerberos プロトコル、および Active Directory を参照してください。 [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330)します。 エンドポイント id の詳細については、次を参照してください。 [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)します。  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>構成  
 コードの代わりに次の構成を使用できます。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Client  
 次のコードと構成は、別々に実行します。 次のいずれかの操作を行います。  
  
-   コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。  
  
-   エンドポイント アドレスを定義しないクライアントを作成します。 代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。 次に例を示します。  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>コード  
 クライアントを構成する場合のコード例を次に示します。 セキュリティ モードは Message に設定され、クライアント資格情報の種類は Windows に設定されています。 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティと <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> プロパティには、`false` が設定されていることに注意してください。  
  
> [!NOTE]
>  ネゴシエートせずに Windows の資格情報を使用するには、サービスとの通信を開始する前に、サービスのアカウントの SPN を使用してクライアントを構成する必要があります。 クライアントは SPN を使用して Kerberos トークンを取得し、サービスとの通信を認証し保護します。 サービスの SPN を使用してクライアントを構成する方法を次の例に示します。 使用する場合、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)クライアントを生成するサービスの SPN は自動的に反映されますクライアント サービスのメタデータ (WSDL) から、サービスのメタデータが含まれている場合その情報。 サービスのメタデータにその SPN を含めるサービスを構成する方法の詳細については、このトピックの「"Service"セクションを参照してください。  
>   
>  Spn、Kerberos、および Active Directory の詳細については、次を参照してください。 [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330)します。 エンドポイント id の詳細については、次を参照してください。 [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)トピック。  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>構成  
 クライアントを構成する場合のコード例を次に示します。 なお、 [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md)要素は、サービスの SPN を Active Directory ドメイン サービスのアカウントに登録されている一致するように設定する必要があります。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Windows Server AppFabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

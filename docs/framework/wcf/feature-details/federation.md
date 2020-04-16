---
title: フェデレーション
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 9616a5afb88e46bb5d69f1cd253c854cc1684d9f
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464184"
---
# <a name="federation"></a>フェデレーション
ここでは、フェデレーション セキュリティの概念について簡単に説明します。 また、フェデレーション セキュリティ アーキテクチャを展開するための Windows 通信財団 (WCF) のサポートについても説明します。 フェデレーションを示すサンプル アプリケーションについては、「[フェデレーションのサンプル](../../../../docs/framework/wcf/samples/federation-sample.md)」を参照してください。  
  
## <a name="definition-of-federated-security"></a>フェデレーション セキュリティの定義  
 フェデレーション セキュリティにより、クライアントがアクセスするサービスと、関連する認証および承認の手順を明確に分離できます。 また、フェデレーション セキュリティを使用すると、異なる信頼レルムに属する複数のシステム、ネットワーク、および組織間のコラボレーションが可能になります。  
  
 WCF では、フェデレーション セキュリティを採用する分散システムの構築と展開をサポートしています。  
  
### <a name="elements-of-a-federated-security-architecture"></a>フェデレーション セキュリティ アーキテクチャの要素  
 次の表に示すように、フェデレーション セキュリティ アーキテクチャには 3 つの主要な要素があります。  
  
|要素|説明|  
|-------------|-----------------|  
|ドメイン/レルム|セキュリティ管理または信頼の単位。 ドメインには通常、1 つの組織が含まれます。|  
|フェデレーション|信頼が確立されたドメインのコレクション。 信頼のレベルは異なる場合がありますが、通常は認証が含まれ、また、ほぼ常に承認が含まれます。 標準的なフェデレーションには、一連のリソースへの共有アクセスのために信頼が確立された多くの組織が含まれる場合があります。|  
|STS (セキュリティ トークン サービス)|セキュリティ トークンを発行する Web サービス。つまり、信頼できる証拠に基づいて、サービスを信頼する任意の相手に対してアサーションを行います。 これによりドメイン間における信頼の橋渡しの基礎が形成されます。|  
  
### <a name="example-scenario"></a>シナリオ例  
 次の図は、フェデレーション セキュリティの例を示しています。  
  
 ![一般的なフェデレーション セキュリティ シナリオを示す図。](./media/federation/typical-federated-security-scenario.gif)  
  
 このシナリオでは、A と B の 2 つの組織があります。組織 B には、組織 A の一部のユーザーにとって有用な Web リソース (Web サービス) があります。  
  
> [!NOTE]
> ここでは、*用語*リソース 、*サービス*、および*Web サービス*を同じ意味で使用します。  
  
 通常、組織 B は、組織 A のユーザーに対して、サービスにアクセスする前になんらかの有効な形式の認証を行うことを要求します。 さらに、組織 B では、当該の特定リソースにアクセスするためにユーザーが承認されることを要求する場合もあります。 この問題に対処し、組織 A のユーザーが組織 B のリソースにアクセスできるようにする 1 つの方法として、次のような方法があります。  
  
- 組織 A のユーザーは、各自の資格情報 (ユーザー名とパスワード) を組織 B に登録します。  
  
- 組織 A のユーザーがリソースにアクセスするには、リソースにアクセスする前に自分の資格情報を組織 B に提示して認証を受けます。  
  
 この方法には、次の 3 つの重大な欠点があります。  
  
- 組織 B では、ローカル ユーザーの資格情報の管理に加えて、組織 A のユーザーの資格情報の管理も必要になります。  
  
- 組織 A のユーザーは、組織 A 内のリソースにアクセスするために通常使用する資格情報以外に、別の資格情報セットを保持する (つまり、別のユーザー名とパスワードを覚えておく) 必要があります。通常、これは、複数のサービス サイトで同じユーザー名とパスワードが使用される可能性を高めるため、脆弱なセキュリティ対策と言えます。  
  
- 組織 B にあるリソースの価値を認識する組織の数が増えても、アーキテクチャを拡張できません。  
  
 上記の欠点に対処する別の方法として、フェデレーション セキュリティの使用があります。 この方法では、組織 A と組織 B が信頼関係を確立し、セキュリティ トークン サービス (STS: Security Token Service) を使用して、確立された信頼を仲介できるようにします。  
  
 フェデレーション セキュリティ アーキテクチャでは、組織 A のユーザーが、組織 B の Web サービスにアクセスする場合に、組織 B の STS から発行された有効なセキュリティ トークンを提示する必要があることを認識しています。この STS が、特定のサービスへのアクセスを認証および承認します。  
  
 STS B に接続したユーザーは、STS に関連付けられたポリシーから別のレベルの間接指定を受け取ります。 このユーザーは、STS B がセキュリティ トークンを発行する前に、STS A (クライアントの信頼レルム) の有効なセキュリティ トークンを提示しておく必要があります。 これは、2 つの組織間で確立された信頼関係の結果であり、組織 B が組織 A のユーザーの ID を管理する必要がないことを意味します。実際には、STS B は通常`issuerAddress`、NULL と`issuerMetadataAddress`. 詳細については、「[方法 : ローカル発行者を構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)」を参照してください。 その場合、クライアントはローカル ポリシーを調べ、STS A を検索します。この構成は*ホーム 領域フェデレーション*と呼ばれ、STS B は STS A に関する情報を保持する必要がないため、より適切に拡張できます。  
  
 ユーザーは、組織 A の STS に接続し、組織 A 内の他のリソースにアクセスする際に通常使用する認証資格情報を提示して、セキュリティ トークンを取得します。これにより、ユーザーが複数の資格情報セットを保持する必要があるという問題や、複数のサービス サイトで同じ資格情報セットを使用するという問題が、ある程度解決されます。  
  
 STS A からセキュリティ トークンを取得したユーザーは、このトークンを STS B に提示します。組織 B はユーザーの要求の承認手順を進め、独自のセキュリティ トークン セットからユーザーにセキュリティ トークンを発行します。 ユーザーは、このトークンを組織 B のリソースに提示し、サービスにアクセスします。  
  
## <a name="support-for-federated-security-in-wcf"></a>WCF におけるフェデレーション セキュリティのサポート  
 WCF は[\<、>フェデレーション](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)セキュリティ アーキテクチャを展開するためのターンキー のサポートを提供します。  
  
 [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素は、エンコードのワイヤー形式としてテキストと XML を使用して、要求/応答通信スタイルの基になるトランスポート 機構として HTTP を使用する必要がある、安全で信頼性の高い相互運用可能なバインディングを提供します。  
  
 フェデレーション セキュリティ シナリオで[\<の wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)の使用は、次のセクションで説明されているように、論理的に独立した 2 つのフェーズに分離できます。  
  
### <a name="phase-1-design-phase"></a>第 1 フェーズ : 設計  
 設計フェーズでは、クライアントは[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe) を](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)使用して、サービス エンドポイントが公開するポリシーを読み取り、サービスの認証と承認の要件を収集します。 次のフェデレーション セキュリティの通信パターンをクライアントで作成するために、適切なプロキシが構築されます。  
  
- クライアント信頼レルムにある STS からセキュリティ トークンを取得する。  
  
- サービス信頼レルムにある STS にトークンを提示する。  
  
- サービス信頼レルムにある STS からセキュリティ トークンを取得する。  
  
- サービスにトークンを提示してサービスにアクセスする。  
  
### <a name="phase-2-run-time-phase"></a>第 2 フェーズ : 実行時  
 ランタイム フェーズでは、クライアントは WCF クライアント クラスのオブジェクトをインスタンス化し、WCF クライアントを使用して呼び出しを行います。 WCF の基になるフレームワークは、フェデレーション セキュリティ通信パターンで前述の手順を処理し、クライアントがシームレスにサービスを使用できるようにします。  
  
## <a name="sample-implementation-using-wcf"></a>WCF を使用した実装のサンプル  
 次の図は、WCF のネイティブ サポートを使用するフェデレーション セキュリティ アーキテクチャの実装例を示しています。  
  
 ![フェデレーション セキュリティ実装のサンプルを示す図。](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>MyService の例  
 `MyService` サービスは、`MyServiceEndpoint` を介して単一のエンドポイントを公開します。 このエンドポイントに関連付けられたアドレス、バインディング、およびコントラクトを次の図に示します。  
  
 ![MyService エンドポイントの詳細を示す図。](./media/federation/myserviceendpoint-details.gif)  
  
 サービス エンドポイント`MyServiceEndpoint`は[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)を使用し、STS B によって発行された要求を`accessAuthorized`含む有効なセキュリティ アサーション マークアップ言語 (SAML) トークンを必要とします。これは、サービス構成で宣言によって指定されます。  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> `MyService` が要求するクレームについては、細かい点に注意が必要です。 2 番目の図は、`MyService` が `accessAuthorized` クレームを含む SAML トークンを要求していることを示しています。 より正確には、これで、`MyService` が必要とするクレームの種類が指定されます。 このクレームの種類の完全修飾名は、`http://tempuri.org:accessAuthorized`サービス構成ファイルで使用される (関連する名前空間と共に) です。 このクレームの値は、このクレームが存在することが示しており、STS B によって `true` に設定されると想定されます。  
  
 このポリシーは、`MyServiceOperationRequirement` の一部として実装されている `MyService` クラスによって実行時に適用されます。  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 STS B を次の図に示します。前述のように、セキュリティ トークン サービス (STS) も Web サービスであり、エンドポイントやポリシーなどを関連付けることができます。  
  
 ![セキュリティ トークン サービス B を示す図。](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B は、セキュリティ トークンを要求する際に使用できる `STSEndpoint` という単一のエンドポイントを公開します。 具体的には、STS B は、`accessAuthorized` クレームを含む SAML トークンを発行します。このトークンは、サービスにアクセスするために `MyService` サービス サイトで提示できます。 ただし、STS B は、STS A によって発行された `userAuthenticated` クレームを含む有効な SAML トークンを提示することをユーザーに要求します。 これは、STS 構成で宣言によって指定されます。  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> この場合も`userAuthenticated`、要求は STS B で要求される要求の種類です。このクレームの種類の完全修飾名は、`http://tempuri.org:userAuthenticated`関連付けられた名前空間と共に、STS 構成ファイルで使用されます。 このクレームの値は、このクレームが存在することを示しており、STS A によって `true` に設定されると想定されます。  
  
 STS B の一部として実装されているこのポリシーは、`STS_B_OperationRequirement` クラスによって実行時に適用されます。  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 アクセス チェックで問題がなければ、STS B は、`accessAuthorized` クレームを含む SAML トークンを発行します。  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 STS A を次の図に示します。  
  
 ![フェデレーション](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 STS B と同様に、STS A もセキュリティ トークンを発行する Web サービスであり、そのための単一のエンドポイントを公開します。 ただし、別のバインド (`wsHttpBinding`) を使用し、ユーザーが`emailAddress`有効な CardSpace を要求します。 応答で、STS A は `userAuthenticated` クレームを含む SAML トークンを発行します。 これは、サービス構成で宣言によって指定されます。  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 STS A の一部として実装されているこのポリシーは、`STS_A_OperationRequirement` クラスによって実行時に適用されます。  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 アクセスが `true` であれば、STS A は、`userAuthenticated` クレームを含む SAML トークンを発行します。  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>組織 A のクライアント  
 `MyService` サービスの呼び出しに必要な手順と共に、組織 A のクライアントを次の図に示します。 全体の処理を示すために、他の機能コンポーネントも示します。  
  
 ![MyService サービス呼び出しの手順を示す図。](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>まとめ  
 フェデレーション セキュリティを使用すると、役割を明確に分離できるため、安全で拡張性のあるサービス アーキテクチャを構築できます。 WCF は、分散アプリケーションを構築および展開するためのプラットフォームとして、フェデレーション セキュリティを実装するためのネイティブ サポートを提供します。  
  
## <a name="see-also"></a>関連項目

- [Security](../../../../docs/framework/wcf/feature-details/security.md)

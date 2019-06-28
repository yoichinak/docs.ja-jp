---
title: Windows Communication Foundation のセキュリティ動作
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 53d8fedb5f562dfbc4aec566f8d0c442b255e1c9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424675"
---
# <a name="security-behaviors-in-wcf"></a>Windows Communication Foundation のセキュリティ動作
Windows Communication Foundation (WCF) での動作は、サービス レベルまたはエンドポイント レベルでの実行時の動作を変更します。 (一般に、表示動作の詳細については[サービスの実行時の動作を指定する](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md))。*セキュリティ動作*および監査ログの資格情報、認証、承認、制御できるようにします。 動作は、プログラムまたは構成を通じて使用できます。 ここでは、セキュリティ機能に関連する以下の動作の構成について説明します。  
  
- [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)します。  
  
- [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)します。  
  
- [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)します。  
  
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)します。  
  
- [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)クライアントがメタデータにアクセスできるセキュリティで保護されたエンドポイントを指定することがもできます。  
  
## <a name="setting-credentials-with-behaviors"></a>動作を使用した資格情報の設定  
 使用して、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)と[ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)サービスまたはクライアントの資格情報の値を設定します。 基になるバインド構成によって、資格情報を設定する必要があるかどうかが決まります。 たとえば、セキュリティ モードが `None` に設定されている場合、クライアントとサービスは相互に認証を行わないため、どの種類の資格情報も必要ありません。  
  
 一方、サービス バインディングでは、クライアント資格情報の種類が必要になることがあります。 その場合は、動作を使用して資格情報の値を設定することが必要になる場合があります (資格情報の種類の詳細については、次を参照してください[資格情報の種類を選択する](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)。)。Windows 資格情報を使用して認証を行う場合などは、実際の資格情報の値が環境によって自動的に設定されるため、資格情報の別のセットを指定する場合を除き、資格情報の値を明示的に設定する必要がないこともあります。  
  
 すべてのサービス資格情報の子要素として見つかった、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)します。 サービス資格情報として使用される証明書を次の例に示します。  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>サービス資格情報  
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) 4 つの子要素が含まれています。 以下のセクションでは、これらの要素とそれぞれの使い方について説明します。  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > 要素  
 メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定するには、この要素を使用します。 定期的に更新される証明書を使用している場合は、証明書のサムプリントが変更されます。 その場合、証明書を同じサブジェクト名で再発行できるため、`X509FindType` としてサブジェクト名を使用します。  
  
 詳細については、要素を使用して、次を参照してください。[方法。クライアント資格情報の値を指定](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)します。  
  
### <a name="certificate-of-clientcertificate-element"></a>\<証明書 > の\<clientCertificate > 要素  
 使用して、 [\<証明書 >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)要素サービスは、クライアントと安全に通信するには、事前に、クライアントの証明書がある必要とします。 このような状況は、双方向通信パターンを使用する場合に生じます。 より一般的な要求/応答パターンでは、クライアントが自身の証明書を要求に含め、サービスはこの証明書を使用して、クライアントへの応答をセキュリティで保護します。 ただし、双方向通信パターンには要求も応答もありません。 サービスは、クライアントの証明書を通信から推測できないため、クライアントへのメッセージをセキュリティで保護するためにクライアントの証明書が前もって必要になります。 クライアントの証明書を帯域外方式で取得し、この要素を使用して証明書を指定する必要があります。 双方向サービスの詳細については、次を参照してください。[方法。双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)します。  
  
### <a name="authentication-of-clientcertificate-element"></a>\<認証 > の\<clientCertificate > 要素  
 [\<認証 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)要素では、クライアントを認証する方法をカスタマイズすることができます。 `CertificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。 既定では、レベルに設定が`ChainTrust`で終了する証明書の階層で各証明書を検索するを指定する、*ルート機関*チェーンの上部にあります。 これは最もセキュリティで保護されているモードです。 また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れるよう指定します。 自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。 クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。 また、値を `Custom` に設定することもできます。 `Custom` 値に設定する場合は、`CustomCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。 独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication > 要素  
 発行されるトークンのシナリオには、3 つの段階があります。 最初の段階でのサービスにアクセスしようとしています。 クライアントが参照される、*セキュア トークン サービス*(STS)。 次に、STS がクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。 最後に、クライアントがトークンを持ってサービスに戻ります。 サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。 トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。 [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)要素はこのようなセキュリティ トークン サービス証明書のリポジトリです。 証明書を追加するには、使用、 [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)します。 挿入、 [\<追加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)各証明書、次の例に示すようにします。  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 既定では、証明書はセキュリティ トークン サービスから取得する必要があります。 このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。  
  
 使用する必要があります、 [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)利用するフェデレーション アプリケーション内のコレクションを*セキュア トークン サービス*(STS) を発行する`SamlSecurityToken`セキュリティ トークン。 STS がセキュリティ トークンを発行する場合、このセキュリティ トークンに `SamlAudienceRestrictionCondition` を追加して、セキュリティ トークンの提供先となる Web サービスの URI を指定できます。 これにより、受け取り側 `SamlSecurityTokenAuthenticator` Web サービスは、次のようにしてこのチェックが行われるように指定することで、発行されたセキュリティ トークンがこの Web サービスを対象としていることを確認できます。  
  
- 設定、`audienceUriMode`属性の[ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)に`Always`または`BearerKeyOnly`します。  
  
- このコレクションに URI を追加して、有効な URI のセットを指定します。 これを行うには、挿入、 [\<追加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)の各 URI に対して  
  
 詳細については、「 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 」を参照してください。  
  
 詳細については、この構成要素を使用して、次を参照してください。[方法。フェデレーション サービスで資格情報を構成](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)します。  
  
#### <a name="allowing-anonymous-cardspace-users"></a>匿名の CardSpace ユーザーの許可  
 `AllowUntrustedRsaIssuers` 要素の `<IssuedTokenAuthentication>` 属性を `true` に設定すると、任意の RSA キー ペアで署名された自己発行トークンを提示することがすべてのクライアントに明示的に許可されます。 発行者が*信頼されていない*キーに関連付けられている発行者のデータがあるないためです。 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ユーザーは、ID の自己提供クレームを含む自己発行カードを作成できます。 この機能を使用するときは十分に注意してください。 この機能を使用する場合は、RSA 公開キーを、ユーザー名と一緒にデータベースに格納する必要のある比較的安全なパスワードとして考えます。 サービスへのクライアント アクセスを許可する前に、クライアントから提示された RSA 公開キーを、提示されたユーザー名に対応する格納済みの公開キーと比較して検証します。 これは、ユーザーが各自のユーザー名を登録し、自己発行の RSA 公開キーに関連付けることができる登録プロセスが確立されていることが前提となります。  
  
## <a name="client-credentials"></a>クライアント資格情報  
 クライアント資格情報は、相互認証が必要な場合にサービスに対するクライアントの認証に使用されます。 また、このセクションを使用して、クライアントがサービスの証明書によってサービスへのメッセージをセキュリティで保護する必要がある場合に使用するサービス証明書を指定することもできます。  
  
 セキュリティ トークン サービスまたはローカル発行者から発行されたトークンを使用するフェデレーション シナリオの一部として、クライアントを構成することもできます。 フェデレーション シナリオの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。 すべてのクライアント資格情報が見つかります、 [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)、次のコードに示すようにします。  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### <a name="clientcertificate-element"></a>\<clientCertificate > 要素  
 この要素で、クライアントの認証に使用する証明書を設定します。 詳細については、「[方法 :クライアント資格情報の値を指定](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)します。  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 この機能は、Windows の Active Directory およびインターネット インフォメーション サービス (IIS) と共に有効にする必要があります。 詳細については、次を参照してください。 [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443)します。  
  
#### <a name="issuedtoken-element"></a>\<issuedToken > 要素  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)トークン、またはセキュリティ トークン サービスで使用する動作のローカル発行者の構成に使用する要素が含まれています。 ローカル発行者を使用するクライアントの構成については、次を参照してください。[方法。ローカル発行者を構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)します。  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 既定のセキュリティ トークン サービス アドレスを指定します。 これは、使用時に、<xref:System.ServiceModel.WSFederationHttpBinding>またはフェデレーション バインディングの発行者アドレスが、セキュリティ トークン サービスの URL を指定していません `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` または`null`です。 そのような場合、<xref:System.ServiceModel.Description.ClientCredentials> は、ローカルの発行者およびバインディングのアドレスと共に構成し、その発行者と通信するために使用する必要があります。  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 使用して、 [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)セキュリティ トークン サービスと通信するときに使用される WCF クライアントの動作を追加します。 クライアント動作を定義、 [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)セクション。 定義された動作を使用するには追加、<`add`> 要素を`<issuerChannelBehaviors>`2 つの属性を持つ要素。 次の例に示すように、`issuerAddress` をセキュリティ トークン サービスの URL に設定し、`behaviorConfiguration` 属性を定義済みのエンドポイントの動作の名前に設定します。  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > 要素  
 サービス証明書の認証を制御するには、この要素を使用します。  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)要素は、サービス証明書を指定しない場合に使用される単一の証明書を格納できます。  
  
 使用して、 [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)と[\<追加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)特定のサービスに関連付けられているサービス証明書を設定します。 `<add>` 要素には、証明書をサービスに関連付けるために使用する `targetUri` 属性があります。  
  
 [\<認証 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)要素は、証明書の認証に使用される信頼レベルを指定します。 既定のレベルは "ChainTrust" に設定され、チェーンの最上位の信頼された証明機関で終了する証明書の階層構造で各証明書を検索するよう指定します。 これは最もセキュリティで保護されているモードです。 また、値を "PeerOrChainTrust" に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れることを指定します。 自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。 クライアントを展開するときは、代わりに "ChainTrust" 値を使用します。 値を "Custom" または "None" に設定できます。 "Custom" 値を使用するには、`CustomCertificateValidatorType` 属性も証明書の検証に使用するアセンブリと型に設定する必要があります。 独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。 詳細については、「[方法 :カスタム証明書の検証を使用するサービスを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)します。  
  
 [\<認証 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)要素が含まれています、`RevocationMode`失効証明書をチェックする方法を指定する属性。 既定値は "online" です。この場合、証明書が失効していないかどうかが自動的にチェックされます。 詳細については、次を参照してください。 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)します。  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)要素には、承認、カスタム ロール プロバイダー、および偽装に影響する要素が含まれています。  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスは、サービス メソッドに適用されます。 この属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。 既定値は "UseWindowsGroups" で、リソースにアクセスしようとしている ID を Windows グループ ("管理者" や "ユーザー" など) で検索するよう指定します。 また、"UseAspNetRoles"を指定することもできます。 下で構成されるカスタム ロール プロバイダーを使用する、<`system.web` > 要素は、次のコードに示すようにします。  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 `roleProviderName` 属性で `principalPermissionMode` を使用する方法を次のコードに示します。  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>セキュリティ監査の構成  
 使用して、 [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)書き込み先のログとその内容を指定するログに記録するイベントの種類。 詳細については、次を参照してください。[監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)します。  
  
```xml  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>セキュリティで保護されたメタデータ交換  
 メタデータをクライアントにエクスポートすると、構成やクライアント コードのダウンロードが可能になるため、サービスとクライアントの開発者にとって便利です。 サービスが悪意のあるユーザーに公開されないようにするために、SSL over HTTP (HTTPS) 機構を使用して転送をセキュリティで保護できます。 転送を保護するには、まず、サービスをホストしているコンピューターの特定のポートに適切な X.509 証明書をバインドする必要があります。 (詳細については、次を参照してください[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。)。次に、追加、 [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)にサービス構成を設定し、`HttpsGetEnabled`属性を`true`します。 最後に、次の例に示すように、`HttpsGetUrl` 属性をサービス メタデータ エンドポイントの URL に設定します。  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>関連項目

- [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

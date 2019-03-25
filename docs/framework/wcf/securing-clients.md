---
title: クライアントのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: fb8d2161800b336cd7f605dda79f28dbb5b91848
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333470"
---
# <a name="securing-clients"></a>クライアントのセキュリティ保護
Windows Communication Foundation (WCF) サービスは、クライアントのセキュリティ要件を決定します。 つまり、使用するセキュリティ モード、およびクライアントが資格情報を提供するかどうかは、サービスによって指定されます。 そのため、クライアントをセキュリティで保護するプロセスは、サービスから取得したメタデータ (公開されている場合) を使用してクライアントを構築するという簡単なものになります。 クライアントを構成する方法は、メタデータによって指定されます。 クライアントが資格情報を提供することをサービスが要求する場合、要件に適した資格情報を取得する必要があります。 ここでは、このプロセスについて詳しく説明します。 セキュリティで保護されたサービスを作成する方法の詳細については、次を参照してください。 [Securing Services](../../../docs/framework/wcf/securing-services.md)します。  
  
## <a name="the-service-specifies-security"></a>サービスによるセキュリティの指定  
 WCF バインドでは、既定で、有効になっているセキュリティ機能があります。 (<xref:System.ServiceModel.BasicHttpBinding> を除く)。したがって、サービスは、WCF を使用して作成されている場合は、認証、機密性、整合性を確実にセキュリティが実装される非常に高くなります。 この場合、サービスが提供するメタデータによって、セキュリティで保護された通信チャネルの確立に必要なものが示されます。 サービス メタデータにセキュリティ要件がまったく含まれていない場合には、サービスでセキュリティ スキーム (SSL (Secure Sockets Layer) over HTTP など) を強制する方法はありません。 ただし、サービスがクライアントに資格情報の提供を求める場合は、クライアントの開発者、展開担当者、または管理者は、クライアントがサービスに対して認証を受けるときに実際に使用する資格情報を提供する必要があります。  
  
## <a name="obtaining-metadata"></a>メタデータの取得  
 クライアントを作成する場合、最初の手順はクライアントが通信を行うサービスからメタデータを取得することです。 これは、次の 2 つの方法で行うことができます。 最初に、サービスは metadata exchange (MEX) エンドポイントを公開または HTTP または HTTPS 経由でそのメタデータを使用できるように、ダウンロードできますを使用して、メタデータ、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)、両方を生成します。構成ファイルと同様に、クライアントは、コード ファイル。 (詳細については、ツールを使用して、次を参照してください[にアクセスするサービスの WCF クライアントを使用して](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)。)。サービスにより MEX エンドポイントが公開されておらず、かつ HTTP または HTTPS 上でメタデータが使用可能になっていない場合は、サービス作成者に連絡して、セキュリティ要件とメタデータについて記述したドキュメントを入手する必要があります。  
  
> [!IMPORTANT]
>  メタデータが信頼されたソースのものであり、改ざんされていないことを確認することをお勧めします。 HTTP プロトコルを使用して取得したメタデータはクリア テキストで送信されるため、改ざんされるおそれがあります。 サービスで <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> プロパティおよび <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを使用している場合は、サービス作成者から提供された URL で、HTTPS プロトコルを使用してデータをダウンロードします。  
  
## <a name="validating-security"></a>セキュリティの検証  
 メタデータのソースは、信頼されたソースと信頼関係のないソースの 2 つに大きく分けられます。 ソースを信頼しており、そのソースのセキュリティで保護された MEX エンドポイントからクライアント コードとその他のメタデータをダウンロードしている場合、何の懸念もなく、クライアントをビルドし、適切な資格情報を提供して実行できます。  
  
 ただし、ほとんど未知のソースからクライアントとメタデータをダウンロードする場合は、コードで使用しているセキュリティ対策を検証する必要があります。 たとえば、サービスにより (最低でも) 機密性と整合性とが要求されていない場合は、個人情報や財務情報を送信するクライアントを作成するようなことは絶対に避けてください。 この種の情報はサービスの所有者から見ることが可能なので、この種の情報の開示を行ってもよいと判断できる程度にはサービスの所有者を信頼できる必要があります。  
  
 したがって、信頼できないソースから受け取ったコードとメタデータを使用する場合には、それがこちらの必要とするセキュリティ レベルを満たしていることを確認する必要があります。  
  
## <a name="setting-a-client-credential"></a>クライアント資格情報の設定  
 クライアントへの資格情報の設定には、次の 2 つの手順があります。  
  
1.  確認、*クライアント資格情報の種類*サービスが必要です。 これは、2 つある方法のどちらかによって行います。 1 つ目の方法として、サービス作成者からドキュメントを入手している場合は、このドキュメントにサービスが要求するクライアント資格情報の種類が示されています (クライアント資格情報の種類が指定されている場合)。 2 番目の方法は Svcutil.exe ツールによって作成された構成ファイルしかない場合で、個々のバインディングを調べることで必要な資格情報の種類を特定できます。  
  
2.  実際のクライアント資格情報を指定します。 実際のクライアント資格情報と呼ばれる、*クライアント資格情報の値*型から区別するためにします。 たとえば、クライアント資格情報の種類として証明書が指定されている場合、サービスが信頼する証明機関によって発行された X.509 証明書を指定する必要があります。  
  
### <a name="determining-the-client-credential-type"></a>クライアント資格情報の種類の特定  
 Svcutil.exe ツールによって生成されたファイル、確認の構成がある場合、 [\<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)セクションをどのようなクライアント資格情報の種類が必要です。 このセクション内には、セキュリティ要件を指定するバインド要素があります。 具体的には、確認、\<セキュリティ > の各バインド要素。 この要素には `mode` 属性が含まれており、3 つの値のいずれか (`Message`、`Transport`、または `TransportWithMessageCredential`) に設定できます。 この属性の値によってモードが決定され、このモードによってどの子要素が有効なのかが決定されます。  
  
 `<security>`要素はいずれかを含めることができます、`<transport>`または`<message>`要素、またはその両方です。 セキュリティ モードと一致する要素が有効な要素です。 たとえば、次のコードでは、セキュリティ モードを `"Message"`、`<message>` 要素のクライアント資格情報の種類を `"Certificate"` に指定しています。 この場合、`<transport>` 要素は無視できます。 ただし、`<message>` 要素で X.509 証明書を提示する必要があることが指定されています。  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 次の例に示すように、`clientCredentialType` 属性が `"Windows"` に設定されている場合は、実際の資格情報の値を指定する必要はありません。 これは、Windows 統合セキュリティでは、クライアントを実行しているユーザーの実際の資格情報 (Kerberos トークン) が提供されるためです。  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>クライアント資格情報の値の設定  
 クライアントが資格情報を提供する必要があると特定された場合は、クライアントを構成する適切なメソッドを使用します。 たとえば、クライアント証明書を設定するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドを使用します。  
  
 X.509 証明書は広く使用されている資格情報の形式です。 資格情報は次の 2 つの方法で提供できます。  
  
-   クライアント コードで (`SetCertificate` メソッドを使用して) プログラミングする方法。  
  
 追加することで、 [\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)クライアントの構成ファイルのセクションを使用して、`clientCredentials`要素 (下記参照)。  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>設定、 \<clientCredentials > コード値  
 設定する、 [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)値コードでは、アクセスする必要があります、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>のプロパティ、<xref:System.ServiceModel.ClientBase%601>クラス。 このプロパティは、次の表に示すように、各種の資格情報の種類にアクセスできる <xref:System.ServiceModel.Description.ClientCredentials> オブジェクトを返します。  
  
|ClientCredential プロパティ|説明|メモ|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> を返します|クライアントがサービスに対して自身を認証するために提供する X.509 証明書を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<xref:System.ServiceModel.Security.HttpDigestClientCredential> を返します|HTTP ダイジェスト資格情報を表します。 この資格情報は、ユーザー名とパスワードのハッシュです。|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<xref:System.ServiceModel.Security.IssuedTokenClientCredential> を返します|フェデレーション シナリオで通常使用される、セキュリティ トークン サービスによって発行されるカスタム セキュリティ トークンを表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<xref:System.ServiceModel.Security.PeerCredential> を返します|Windows ドメインのピア メッシュに参加するためのピア資格情報を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> を返します|帯域外ネゴシエーションでサービスによって提供される X.509 証明書を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential> を返します|ユーザー名とパスワードのペアを表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<xref:System.ServiceModel.Security.WindowsClientCredential> を返します|Windows クライアントの資格情報 (Kerberos 資格情報) を表します。 このクラスのプロパティは読み取り専用です。|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>設定、 \<clientCredentials > 構成内の値  
 子要素として、エンドポイントの動作を使用して、資格情報の値が指定されて、 [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。 使用される要素は、クライアントの資格情報の種類によって異なります。 たとえば、次の例は、X.509 証明書を使用して設定を構成を示しています。、<[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 構成でクライアント資格情報を設定するには追加、 [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)要素を構成ファイル。 さらに、追加した動作要素は、サービスのエンドポイントにリンクする必要がありますを使用して、`behaviorConfiguration`の属性、 [\<エンドポイント > の\<クライアント >](../configure-apps/file-schema/wcf/endpoint-of-client.md)要素の次の例に示すようにします。 
  `behaviorConfiguration` 属性の値は、動作の `name` 属性の値と一致する必要があります。  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
>  クライアント資格情報の値の中には、アプリケーション構成ファイルを使用して設定できないものがあります (ユーザー名とパスワードや、Windows ユーザーとパスワードの値など)。 このような資格情報の値は、コードでのみ指定できます。  
  
 クライアント資格情報を設定する方法についての詳細については、次を参照してください。[方法。クライアント資格情報の値を指定](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)します。  
  
> [!NOTE]
>  次の構成例に示すように、`ClientCredentialType` が `SecurityMode` に設定されている場合、`"TransportWithMessageCredential",` は無視されます。  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)
- [構成エディター ツール (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)
- [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [方法: クライアント資格情報の値を指定します。](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [方法: クライアント資格情報の種類を指定します。](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)

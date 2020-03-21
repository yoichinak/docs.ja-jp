---
title: クライアント構成
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: ff82f56639ec451c04624d22fff0bcb03f46d946
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185371"
---
# <a name="client-configuration"></a>クライアント構成
Windows 通信基盤 (WCF) クライアント構成を使用して、クライアントがサービス エンドポイントへの接続に使用するクライアント エンドポイントの "ABC" プロパティであるアドレス、バインディング、動作、およびコントラクトを指定できます。 クライアント>要素には[\<、エンドポイント>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)要素があり、その属性はエンドポイントの AFC を構成するために使用されます。 [ \<](../../configure-apps/file-schema/wcf/client.md) これらの属性については、「[エンドポイントの構成」](#configuring-endpoints)セクションで説明します。  
  
 エンドポイント>要素には、メタデータ[\<>メタデータの](../../configure-apps/file-schema/wcf/metadata.md)インポートとエクスポートの設定を指定するために使用されるメタデータ要素、カスタム アドレス[\<ヘッダー](../../configure-apps/file-schema/wcf/headers.md)のコレクションを含むヘッダー>要素、および他のエンドポイントがメッセージを交換するエンドポイントの認証を有効にする[\<id>](../../configure-apps/file-schema/wcf/identity.md)要素も含まれます。 [ \<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) ヘッダー>と[\<id>](../../configure-apps/file-schema/wcf/identity.md)要素は、の一<xref:System.ServiceModel.EndpointAddress>部であり、[アドレス](../../wcf/feature-details/endpoint-addresses.md)の記事で説明します。 [ \<](../../configure-apps/file-schema/wcf/headers.md) メタデータ拡張機能の使用について説明するトピックへのリンクは、「[メタデータの構成」セクションに](#configuring-metadata)記載されています。  
  
## <a name="configuring-endpoints"></a>エンドポイントの構成  
 クライアント構成は、クライアントが 1 つ以上のエンドポイントを指定できるように設計されており、各エンドポイントは独自の名前、アドレス、およびコントラクトを持ち、各エンドポイントは[\<、その](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)エンドポイントを構成するために使用するクライアント構成[\<の要素>バインディング>と動作](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)を参照します。 クライアント構成ファイルは、WCF ランタイムが予期する名前であるため、"App.config" という名前にする必要があります。 クライアント構成ファイルの例を次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。 この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。 ワイルドカード エンドポイント構成名\*" " は使用可能で<xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A>、ファイル内のエンドポイント構成を読み込む必要があることをメソッドに示します。 この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。 `name` 属性の既定値は、他の名前と同様に一致する空の文字列です。  
  
 すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。 `address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。 ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。 詳細については、「アドレス」を参照[してください](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)。 序文が示すように、[\<ヘッダー>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)と[\<id>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素は、の<xref:System.ServiceModel.EndpointAddress>一部であり、[また、アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)トピックで説明します。  
  
 `binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。 参照できるようにするには、種類は登録された構成セクションを持っている必要があります。 前の例では、これは[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)セクションで、エンドポイントが<xref:System.ServiceModel.WSHttpBinding>を使用することを示します。 ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。 これらの要素のそれぞれは、(バインディング)型要素内で独自[\<のバインディング>](../../configure-apps/file-schema/wcf/bindings.md)要素を持ちます。 `bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。 その値は`name`[\<、バインド>](../../configure-apps/file-schema/wcf/bindings.md)要素の属性と一致します。 構成を使用してクライアント のバインドを構成する方法の詳細については、「[方法 : 構成でクライアント バインドを指定する](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)」を参照してください。  
  
 この`behaviorConfiguration`属性は、[\<エンドポイント](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)の[\<>動作](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)を指定するために使用>、エンドポイントが使用する動作を指定します。 その値は、動作`name`[\<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素の属性と一致します。 クライアントの動作を指定する構成の使用例については、「[クライアント動作の構成」](../../../../docs/framework/wcf/configuring-client-behaviors.md)を参照してください。  
  
 `contract` 属性は、エンドポイントが公開するコントラクトを指定します。 この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。 既定値は、サービスを実装するクラスの完全な型名です。  
  
### <a name="configuring-metadata"></a>メタデータの構成  
 [\<メタデータ>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)要素は、メタデータ インポート拡張機能の登録に使用される設定を指定するために使用されます。 メタデータ システムの拡張の詳細については、「メタデータ[システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [エンドポイント : アドレス、バインディング、およびコントラクト](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [クライアントの動作の構成](../../../../docs/framework/wcf/configuring-client-behaviors.md)

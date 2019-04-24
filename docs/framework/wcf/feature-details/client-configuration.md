---
title: クライアント構成
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: b9975c6caeedc94bf4a7773e71a95eb0d8c7aed2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144691"
---
# <a name="client-configuration"></a>クライアント構成
Windows Communication Foundation (WCF) クライアントの構成を使用して、アドレス、バインディング、動作、およびコントラクト、サービス エンドポイントへの接続にクライアントを使用して、クライアント エンドポイントの"ABC"プロパティを指定することができます。 [\<クライアント >](../../configure-apps/file-schema/wcf/client.md)要素には、 [\<エンドポイント >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)要素の属性を使用して、エンドポイントの abc プロパティを構成します。 これらの属性は、後ほど、[エンドポイントの構成](#configuring-endpoints)セクション。  
  
 [\<エンドポイント >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)要素も含まれています、 [\<メタデータ >](../../configure-apps/file-schema/wcf/metadata.md)のインポートとエクスポートのメタデータの設定を指定するために使用する要素を[ \<ヘッダー >](../../configure-apps/file-schema/wcf/headers.md)カスタム アドレス ヘッダーのコレクションを格納する要素と[ \<identity >](../../configure-apps/file-schema/wcf/identity.md)他のエンドポイントによるエンドポイントの認証を有効にする要素メッセージを交換します。 [\<ヘッダー >](../../configure-apps/file-schema/wcf/headers.md)と[ \<identity >](../../configure-apps/file-schema/wcf/identity.md)要素の一部である、<xref:System.ServiceModel.EndpointAddress>詳細については、[アドレス](../../wcf/feature-details/endpoint-addresses.md)記事。 メタデータの拡張機能の使用方法を説明するトピックへのリンクが記載、[構成メタデータ](#configuring-metadata)セクション。  
  
## <a name="configuring-endpoints"></a>エンドポイントの構成  
 クライアントの構成が 1 つ指定するクライアントを許可するように設計、またはそれぞれ独自の名前を持つ複数のエンドポイント アドレス、および各を参照すると、契約、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)と[ \<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)そのエンドポイントを構成に使用するクライアント構成内の要素。 クライアント構成ファイルに名前を付ける"App.config"ため、これは、WCF ランタイムが予期される名前です。 クライアント構成ファイルの例を次に示します。  
  
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
  
 省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。 この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。 ワイルドカードのエンドポイント構成名"\*"があるし、することを示します、<xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A>メソッドが提供される、正確に 1 つである使用可能、それ以外の場合に、ファイル内のエンドポイント構成を読み込む必要がありますが、例外をスローします。 この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。 `name` 属性の既定値は、他の名前と同様に一致する空の文字列です。  
  
 すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。 `address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。 ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。 詳細については、次を参照してください。[アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)します。 導入が示すとおり、 [\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素の一部である、<xref:System.ServiceModel.EndpointAddress>も詳細については、 [アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)トピック。  
  
 `binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。 参照できるようにするには、種類は登録された構成セクションを持っている必要があります。 前の例では、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)セクションで、エンドポイントが使用することを示す、<xref:System.ServiceModel.WSHttpBinding>します。 ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。 独自のこれらの各[\<バインド >](../../../../docs/framework/misc/binding.md) (バインド) 型の要素内の要素。 `bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。 その値と対応している、`name`の属性、 [\<バインド >](../../../../docs/framework/misc/binding.md)要素。 詳細については、クライアントを構成する方法についての構成を使用してバインドを参照してください[方法。構成でクライアント バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)します。  
  
 `behaviorConfiguration`を指定する属性が使用される[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)の[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)エンドポイントを使用する必要があります。 その値と対応している、`name`の属性、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素。 クライアントの動作を指定する構成を使用しての例は、次を参照してください。[クライアントの動作を構成する](../../../../docs/framework/wcf/configuring-client-behaviors.md)します。  
  
 `contract` 属性は、エンドポイントが公開するコントラクトを指定します。 この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。 既定値は、サービスを実装するクラスの完全な型名です。  
  
### <a name="configuring-metadata"></a>メタデータの構成  
 [\<メタデータ >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)要素を使用して、拡張機能をインポートするメタデータを登録するための設定を指定します。 メタデータ システムの拡張の詳細については、次を参照してください。[メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)します。  
  
## <a name="see-also"></a>関連項目

- [エンドポイント:アドレス、バインディング、およびコントラクト](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [クライアントの動作の構成](../../../../docs/framework/wcf/configuring-client-behaviors.md)

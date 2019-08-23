---
title: 簡略化された構成
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 5aaca8ae8c456e2377326ee2e9e22c3dcf6a21a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922997"
---
# <a name="simplified-configuration"></a>簡略化された構成
Windows Communication Foundation (WCF) サービスの構成は複雑なタスクになる場合があります。 さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。 構成ファイルは WCF サービスの柔軟性を向上させますが、多くの問題を検出するためのソースでもあります。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。  
  
## <a name="simplified-configuration"></a>簡略化された構成  
 WCF サービス構成ファイルの <`system.serviceModel`> セクションには、ホストされている各サービスの <`service`> 要素が含まれています。 <`service`> 要素には <`endpoint`> 要素のコレクションが含まれており、各サービスに対して公開されるエンドポイントと、必要に応じて一連のサービス動作を指定します。 <`endpoint`の > 要素は、エンドポイントによって公開されるアドレス、バインディング、およびコントラクトを指定します。また、必要に応じて、構成およびエンドポイントの動作をバインドします。 <`system.serviceModel`> セクションには、サービスまた`behaviors`はエンドポイントの動作を指定できる < の > 要素も含まれています。 次の例は、構成`system.serviceModel`ファイルの < > セクションを示しています。  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<`service`> 要素の要件を削除することにより、WCF サービスの構成が容易になります。 <`service`> セクションを追加していない場合、または <`service`> セクションにエンドポイントを追加せず、サービスがプログラムによってエンドポイントを定義していない場合は、既定のエンドポイントのセットがサービスに自動的に追加されます。サービスによって実装された各コントラクトのサービスベースアドレスと。 これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。 エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。 サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。 既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。 これらの設定は、<`protocolMappings``system.serviceModel`> セクション内の < > セクションで指定します。 <`protocolMappings`> セクションには、バインドの種類にマップされたトランスポートプロトコルスキームの一覧が含まれています。 サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。 次の例では、`protocolMappings`< > 要素を使用します。  
  
> [!WARNING]
>  バインディングまたは動作のような既定の構成要素を変更すると、構成階層の下のレベルで定義されたサービスはこれらの既定のバインディングおよび動作を使用している可能性があるため、影響を受けることがあります。 したがって、既定のバインディングおよび動作を変更する場合は、これらの変更が階層の他のサービスに影響を与える可能性があることに注意する必要があります。  
  
> [!NOTE]
> インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされるサービスは、仮想ディレクトリをベース アドレスとして使用します。  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 前の例では、"http" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.BasicHttpBinding> を使用します。 "net.tcp" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.NetTcpBinding> を使用します。 ローカルの App.config または Web.config ファイルの設定はオーバーライドできます。  
  
 <`protocolMappings`> セクション内の各要素は、スキームとバインドを指定する必要があります。 必要に応じて、 `bindingConfiguration`構成ファイルの <`bindings`> セクション内でバインド構成を指定する属性を指定することもできます。 `bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。  
  
 サービスの動作は、既定のエンドポイントに対して`behavior`構成されます`serviceBehaviors`。これには < > セクション内の匿名の < > セクションを使用します。 `behavior`<`serviceBehaviors`> 内の名前のない < > 要素は、サービスの動作を構成するために使用されます。 たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 エンドポイントの動作は <`behavior``serviceBehaviors`> セクション内の匿名 < > セクションを使用して構成します。  
  
 以下は、このトピックの最初にある例と同じ内容ですが、簡略化された構成モデルを使用している構成ファイルの例です。  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。 ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。 WCF クライアントを手動で構成する場合は、クライアント > 要素を\<構成に追加し、呼び出すエンドポイントを指定する必要があります。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してサービスを構成する方法](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [サービスのバインディングの構成](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [システムが提供するバインディングの構成](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスの構成](../../../docs/framework/wcf/configuring-services.md)
- [WCF サービスの構成](configuring-services.md)
- [コード内での WCF サービスの構成](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)

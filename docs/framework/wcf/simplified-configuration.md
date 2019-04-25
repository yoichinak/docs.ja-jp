---
title: 簡略化された構成
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184055"
---
# <a name="simplified-configuration"></a>簡略化された構成
Windows Communication Foundation (WCF) サービスを構成すると、複雑な作業ができる場合があります。 さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。 構成ファイルは、WCF サービスの柔軟性を向上させ、多くの問題を見つけるためにハードのソースもができます。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。  
  
## <a name="simplified-configuration"></a>簡略化された構成  
 WCF サービス構成ファイルで、<`system.serviceModel`> セクションが含まれています、<`service`> ホストされているサービスごとの要素。 <`service`> 要素にはコレクションが含まれています <`endpoint`> 各サービスと必要に応じてサービスの動作のセットに対して公開されるエンドポイントを指定する要素。 <`endpoint`> 要素の指定、アドレス、バインディング、およびコントラクトによって公開される、エンドポイントでは、必要に応じてバインド構成およびエンドポイント動作。 <`system.serviceModel`> セクションにも含まれています、<`behaviors`> 要素をサービスまたはエンドポイント動作を指定することができます。 次の例は、<`system.serviceModel`> 構成ファイルのセクション。  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 要件を削除することで簡単に WCF サービスを構成できるように、<`service`> 要素。 追加しない場合、<`service`> セクションにエンドポイントを追加したり、<`service`> セクションと、サービスがないプログラムでエンドポイントを定義、その後、一連の既定のエンドポイントは、サービスごとに 1 つに自動的に追加サービスのベース アドレス、サービスによって実装される各コントラクトに対して。 これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。 エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。 サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。 既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。 これらの設定で指定を <`protocolMappings`> セクション内の <`system.serviceModel`> セクション。 <`protocolMappings`> セクションには、バインドの型にマップされているトランスポート プロトコル スキームの一覧が含まれています。 サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。 次の例では、<`protocolMappings`> 要素。  
  
> [!WARNING]
>  バインディングまたは動作のような既定の構成要素を変更すると、構成階層の下のレベルで定義されたサービスはこれらの既定のバインディングおよび動作を使用している可能性があるため、影響を受けることがあります。 したがって、既定のバインディングおよび動作を変更する場合は、これらの変更が階層の他のサービスに影響を与える可能性があることに注意する必要があります。  
  
> [!NOTE]
>  インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされるサービスは、仮想ディレクトリをベース アドレスとして使用します。  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 前の例では、"http" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.BasicHttpBinding> を使用します。 "net.tcp" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.NetTcpBinding> を使用します。 ローカルの App.config または Web.config ファイルの設定はオーバーライドできます。  
  
 内の各要素の <`protocolMappings`> セクションは、スキームとバインドを指定する必要があります。 必要に応じて指定できます、`bindingConfiguration`内でバインド構成を指定する属性を <`bindings`> 構成ファイルのセクション。 `bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。  
  
 匿名を使用して既定のエンドポイント サービスの動作が構成されている <`behavior`> セクション内 <`serviceBehaviors`> セクション。 いずれかの名前のない <`behavior`> 内の要素 <`serviceBehaviors`> サービスの動作を構成するために使用します。 たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。  
  
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
  
 匿名を使用してエンドポイントの動作が構成されている <`behavior`> セクション内 <`serviceBehaviors`> セクション。  
  
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
>  この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。 ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。 WCF クライアントを手動で構成している場合は、追加する必要があります。、\<クライアント > 要素を構成し、呼び出すエンドポイントを指定します。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してサービスを構成する方法](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [サービスのバインディングの構成](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [システムが提供するバインディングの構成](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスの構成](../../../docs/framework/wcf/configuring-services.md)
- [WCF サービスの構成](configuring-services.md)
- [コード内での WCF サービスの構成](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)

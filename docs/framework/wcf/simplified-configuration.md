---
title: 簡略化された構成
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 567f03e8f35ed72ba7e2a602bf47257158741fb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321154"
---
# <a name="simplified-configuration"></a>簡略化された構成
Windows Communication Foundation (WCF) サービスの構成は複雑なタスクになる場合があります。 さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。 構成ファイルは WCF サービスの柔軟性を向上させますが、多くの問題を検出するためのソースでもあります。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。  
  
## <a name="simplified-configuration"></a>簡略化された構成  
 WCF サービス構成ファイルの < `system.serviceModel` > セクションには、ホストされている各サービスの < `service` > 要素が含まれています。 < @No__t-0 > 要素には、各サービスに対して公開されるエンドポイントと、必要に応じて一連のサービス動作を指定する < `endpoint` > 要素のコレクションが含まれます。 < @No__t-0 > 要素は、エンドポイントによって公開されるアドレス、バインディング、およびコントラクトを指定します。また、必要に応じて、構成およびエンドポイントの動作をバインドします。 < @No__t-0 > セクションには、サービスまたはエンドポイントの動作を指定できる < `behaviors` > 要素も含まれています。 次の例は、構成ファイルの < @no__t 0 > セクションを示しています。  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] < `service` > 要素の要件を削除することにより、WCF サービスの構成が容易になります。 < @No__t-0 > セクションを追加しなかった場合、または < `service` > セクションにエンドポイントを追加していない場合に、サービスでエンドポイントがプログラムによって定義されていないと、既定のエンドポイントのセットがサービスに自動的に追加されます (サービスベースのアドレスごとに1つ)。サービスによって実装された各コントラクトに対して、およびがあります。 これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。 エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。 サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。 既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。 これらの設定は、< `system.serviceModel` > セクション内の < `protocolMappings` > セクションで指定します。 < @No__t-0 > セクションには、バインドの種類にマップされたトランスポートプロトコルスキームの一覧が含まれています。 サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。 次の例では、< `protocolMappings` > 要素を使用します。  
  
> [!WARNING]
> バインディングまたは動作のような既定の構成要素を変更すると、構成階層の下のレベルで定義されたサービスはこれらの既定のバインディングおよび動作を使用している可能性があるため、影響を受けることがあります。 したがって、既定のバインディングおよび動作を変更する場合は、これらの変更が階層の他のサービスに影響を与える可能性があることに注意する必要があります。  
  
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
  
 < @No__t-0 > セクション内の各要素は、スキームとバインドを指定する必要があります。 必要に応じて、構成ファイルの < `bindings` > セクション内のバインド構成を指定する @no__t 0 属性を指定することもできます。 `bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。  
  
 サービスの動作は、既定のエンドポイント用に構成されています。そのためには、< `serviceBehaviors` > セクション内の < @no__t 0 > セクションを使用します。 < @No__t-1 > 内のすべての名前のない < @no__t 0 > 要素は、サービスの動作を構成するために使用されます。 たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。  
  
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
  
 エンドポイントの動作は、< `serviceBehaviors` > セクション内の匿名 < @no__t 0 > セクションを使用して構成されます。  
  
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
> この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。 ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。 WCF クライアントを手動で構成する場合は、@no__t 0client > 要素を構成に追加し、呼び出すエンドポイントを指定する必要があります。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してサービスを構成する方法](configuring-services-using-configuration-files.md)
- [サービスのバインディングの構成](configuring-bindings-for-wcf-services.md)
- [システムが提供するバインディングの構成](./feature-details/configuring-system-provided-bindings.md)
- [サービスの構成](configuring-services.md)
- [WCF サービスの構成](configuring-services.md)
- [コード内での WCF サービスの構成](configuring-wcf-services-in-code.md)

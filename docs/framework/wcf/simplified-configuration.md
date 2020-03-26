---
title: 簡略化された構成
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249631"
---
# <a name="simplified-configuration"></a>簡略化された構成
Windows 通信基盤 (WCF) サービスを構成することは、複雑な作業になる場合があります。 さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。 構成ファイルは WCF サービスの柔軟性を高めますが、問題を見つけるのが難しい多くのソースでもあります。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。  
  
## <a name="simplified-configuration"></a>簡略化された構成  
 WCF サービス構成ファイルでは、<`system.serviceModel`> セクションには`service`、ホストされる各サービスの<>要素が含まれています。 >要素`service`<には、各サービスに公開`endpoint`されるエンドポイントを指定する<>要素のコレクションと、必要に応じて一連のサービス動作が含まれます。 <>`endpoint`要素は、エンドポイントによって公開されるアドレス、バインディング、およびコントラクトを指定し、必要に応じて、構成とエンドポイントの動作をバインドします。 <`system.serviceModel`> セクションには、サービス`behaviors`またはエンドポイントの動作を指定できる<>要素も含まれています。 次の例は、構成`system.serviceModel`ファイルの<>セクションを示しています。  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<>要素の要件を削除することで、WCF サービスの`service`構成が容易になります。 <`service`> セクションを追加したり、><`service`セクションにエンドポイントを追加したりしない場合、サービスがプログラムでエンドポイントを定義しない場合、サービスに対して 1 つずつ、サービスによって実装される各コントラクトに対して、サービスに対して既定のエンドポイントのセットが自動的に追加されます。 これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。 エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。 サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。 既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。 これらの設定は、<`protocolMappings` `system.serviceModel`> セクション内の<> セクションで指定します。 <>`protocolMappings`セクションには、バインディングの種類にマップされたトランスポート プロトコル スキームの一覧が含まれています。 サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。 次の例では、<>`protocolMappings`要素を使用します。  
  
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
  
 <>`protocolMappings`セクション内の各要素は、スキームとバインディングを指定する必要があります。 必要に応じて、構成`bindingConfiguration`ファイルの<>`bindings`セクション内のバインディング構成を指定する属性を指定できます。 `bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。  
  
 サービス動作は、<> セクション内の匿名<>`behavior`セクションを使用して`serviceBehaviors`、既定のエンドポイントに対して構成されます。 名前のない<>`behavior`要素<>`serviceBehaviors`内でサービスの動作を構成するために使用されます。 たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。  
  
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
  
 エンドポイントの動作は、>セクション内の`behavior`匿名<>`serviceBehaviors`セクション<使用して構成されます。  
  
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
> この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。 ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。 WCF クライアントを手動で構成する場合は、\<クライアント>要素を構成に追加し、呼び出すエンドポイントを指定する必要があります。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してサービスを構成する方法](configuring-services-using-configuration-files.md)
- [サービスのバインディングの構成](configuring-bindings-for-wcf-services.md)
- [システムが提供するバインディングの構成](./feature-details/configuring-system-provided-bindings.md)
- [サービスの構成](configuring-services.md)
- [WCF サービスの構成](configuring-services.md)
- [コード内での WCF サービスの構成](configuring-wcf-services-in-code.md)

---
title: NetHttpBinding の使用
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 5090cfdfeb068acda1e1092e408f3cd747c574c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121018"
---
# <a name="using-the-nethttpbinding"></a>NetHttpBinding の使用
<xref:System.ServiceModel.NetHttpBinding> HTTP や WebSocket のサービスを使用するために設計されたバインドと既定でバイナリ エンコードを使用します。 <xref:System.ServiceModel.NetHttpBinding> 要求/応答コントラクトまたは双方向コントラクトと共に使用するかどうかを検出し、一致するように動作の変更 - 双方向コントラクトの要求/応答コントラクトと Websocket の HTTP が使用されます。 この動作は、<xref:System.ServiceModel.Channels.WebSocketTransportUsage> 設定を使用してオーバーライドできます。  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> -これは、要求/応答コントラクトにも使用される websocket です。  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> -これは Websocket が使用することを防ぎます。 この設定で二重のコントラクトを使用しようとすると、例外が発生します。  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> -これにより、既定値は、し、前述のように動作します。  
  
 <xref:System.ServiceModel.NetHttpBinding> HTTP モードと WebSocket モードの両方で信頼できるセッションをサポートしています。 WebSocket モードでは、セッションがトランスポートによって提供されます。  
  
> [!WARNING]
>  <xref:System.ServiceModel.NetHttpBinding> を使用していて、バインドの TransferMode が TransferMode.Streamed に設定されている場合、大きいストリームによってデッドロックが発生する可能性があり、呼び出しがタイムアウトします。 この問題を回避するには、小さいメッセージを送信するか、TransferMode.Buffered を使用してください。  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>NetHttpBinding を使用するサービスの構成  
 <xref:System.ServiceModel.NetHttpBinding> は、他のバインドと同様に構成できます。 次の構成スニペットは、<xref:System.ServiceModel.NetHttpBinding> を使用して WCF サービスを構成する方法を示しています。  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 次のコード スニペットは、コードで <xref:System.ServiceModel.NetHttpBinding> を追加する方法を示しています。  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>関連項目

- [サービスのバインディングの構成](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)
- [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
- [双方向サービス](../../../../docs/framework/wcf/feature-details/duplex-services.md)

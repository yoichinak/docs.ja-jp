---
title: カスタム メッセージ フィルター
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 34e6d851bd0aa3515c5c43521be6213451b7ed12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003068"
---
# <a name="custom-message-filter"></a>カスタム メッセージ フィルター
このサンプルでは、Windows Communication Foundation (WCF) を使用してエンドポイントにメッセージをディスパッチするメッセージ フィルターを交換する方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 チャネルでの最初のメッセージがサーバーに到着すると、サーバーは、URI に関連付けられているエンドポイントがある場合に、どのエンドポイントがメッセージを受信する必要があるかを判断する必要があります。 この処理は、<xref:System.ServiceModel.Dispatcher.MessageFilter> に関連付けられている <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> オブジェクトで制御されます。  
  
 サービスの各エンドポイントには、単一の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> があります。 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> には、<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> と <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> の両方があります。 これら 2 つのフィルタを結合したものが、このエンドポイントに使用されるメッセージ フィルタです。  
  
 エンドポイントの <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> の既定では、アドレス指定されているメッセージと、サービス エンドポイントの <xref:System.ServiceModel.EndpointAddress> に一致するアドレスを照合します。 既定で、<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>のエンドポイントが受信メッセージのアクションを検査し、サービス エンドポイントのコントラクトの操作のアクションのいずれかに対応するアクション メッセージと一致する (だけ`IsInitiating` = `true`アクションと見なされます)。 その結果、エンドポイントのフィルタの既定で一致と見なされるのは、メッセージの To ヘッダーがエンドポイントの <xref:System.ServiceModel.EndpointAddress> に一致し、メッセージのアクションがエンドポイントの操作のいずれかのアクションと一致するという、2 つの条件がどちらも満たされる場合だけです。  
  
 これらのフィルタは、動作を使用して変更できます。 サンプルのサービスは、次のように <xref:System.ServiceModel.Description.IEndpointBehavior> を作成して、<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> と <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> を置き換えます。  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 2 つのアドレス フィルタは、次のように定義されます。  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` は構成可能になり、2 つの異なるバリエーションを設定できます。  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 バリエーション 1 では 'e' が含まれる (ただし任意のアクションを含む) アドレスのみを照合します。これに対して、バリエーション 2 では 'e' が含まれないアドレスのみを照合します。  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 構成ファイルでは、サービスは次のように新しい動作を登録します。  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 次に、各バリエーションの `endpointBehavior` 構成を次のように作成します。  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 最後に、サービスのエンドポイントは、`behaviorConfigurations` の 1 つを次のように参照します。  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 クライアント アプリケーションの実装は単純で、URI の値を 2 番目の (`via`) パラメータとして <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> に渡すことによって、2 つのチャネルをサービスの URI に作成し、各チャネルに 1 つのメッセージを送信します。ただし、チャネルごとに異なるエンドポイント アドレスが使用されます。 この結果、次のクライアントの出力に示すように、クライアントからの送信メッセージにはそれぞれ異なる宛先が指定され、サーバーはこれに応じて応答します。  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 サーバーの構成ファイルのバリエーションを切り替えると、フィルターが入れ替わり、クライアントには逆の動作が表示されます (`urn:e` へのメッセージは正常に送信されますが、`urn:a` へのメッセージはエラーになります)。  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. ソリューションをビルドする手順については、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
2. 単一コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
3. 複数コンピューター構成でサンプルを実行する」の手順に従います[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)Client.cs の次の行を変更します。  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     つまり、localhost をサーバー名に置き換えます。  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  

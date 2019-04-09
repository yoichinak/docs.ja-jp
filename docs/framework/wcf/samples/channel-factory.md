---
title: チャネル ファクトリ
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 8e04dd762e0abad7796d90aff5615134ba22539c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119731"
---
# <a name="channel-factory"></a>チャネル ファクトリ
このサンプルでは、クライアント アプリケーションが、生成されたクライアントではなく <xref:System.ServiceModel.ChannelFactory> クラスを含むチャネルを作成できる方法を示します。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して、サービス エンドポイントにチャネルを作成します。 使用してクライアント型を生成するサービス エンドポイントへのチャネルを作成する、通常、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成された型のインスタンスを作成します。 また、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用してチャネルを作成することもできます。サンプルを参照してください。 次のサンプル コードによって作成されたサービスがサービスに同じ、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)します。  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  このサンプルを複数コンピュータのシナリオで実行している場合は、前述のコードの "localhost" を、サービスを実行中のコンピュータの完全修飾名に置き換える必要があります。 このサンプルは、エンドポイント アドレスを設定する構成を使用していません。したがって、コード内でアドレスを設定する必要があります。  
  
 チャネルが作成されたら、生成されたクライアントと同様にサービス操作を呼び出すことができます。  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 チャネルを閉じるには、最初にチャネルを <xref:System.ServiceModel.IClientChannel> インターフェイスにキャストする必要があります。 これは、生成されたチャネルが `ICalculator` インターフェイスによってクライアント アプリケーション内で宣言されているからです。このインターフェイスには `Add` および `Subtract` などのメソッドは含まれていますが、`Close` は含まれていません。 `Close` メソッドは、<xref:System.ServiceModel.ICommunicationObject> インターフェイスで発生します。  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアント アプリケーションをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。 このサンプルではメタデータの公開は有効化されないことに注意してください。 最初にこのサンプルのメタデータ公開を有効にして、クライアント型を再生成する必要があります。  
  
3.  1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
### <a name="to-run-the-sample-cross-machine"></a>サンプルを複数コンピュータで実行するには  
  
1.  次のコードの "localhost" を、サービスを実行中のコンピューターの完全修飾名に置き換えます。  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  

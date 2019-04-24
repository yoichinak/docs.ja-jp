---
title: セキュリティ検証
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 1ad52431d68af847d7c26a0a3bd42dbcb3ce51c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334654"
---
# <a name="security-validation"></a>セキュリティ検証
このサンプルでは、サービスが特定の条件を満たしていることを確認するカスタム動作を使用して、コンピューター上のサービスを検証する方法を示します。 このサンプルでは、サービス上の各エンドポイントをスキャンし、セキュリティ保護されたバインディング要素が含まれているかどうかを確認するカスタム動作を使用して、サービスを検証します。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="endpoint-validation-custom-behavior"></a>エンドポイント検証のカスタム動作  
 `Validate` インターフェイスに含まれる <xref:System.ServiceModel.Description.IServiceBehavior> メソッドにユーザー コードを追加することによって、サービスまたはエンドポイントにカスタム動作を与え、ユーザー定義のアクションを実行することができます。 次のコードを使用すると、サービスに含まれる各エンドポイントをループし、バインディング コレクションからセキュリティ保護されたバインディングが検索されます。  
  
```csharp
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their    
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 次のコードを Web.config ファイルに追加すると、サービスで識別される `serviceValidate` 動作の拡張が追加されます。  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 動作の拡張がサービスに追加されると、`endpointValidate` の動作を Web.config ファイルの動作リストに追加でき、さらにはサービスに追加できるようになります。  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 動作とその拡張が Web.config ファイルに追加されると、動作は個別のサービスに適用されます。一方で Machine.config ファイルに追加された場合は、動作はコンピューター上でアクティブなすべてのサービスに適用されます。  
  
> [!NOTE]
>  動作をすべてのサービスに追加する場合、Machine.config ファイルの変更を行う前に、このファイルのバックアップを推奨するメッセージが表示されます。  
  
 ここで、このサンプルの client\bin ディレクトリに用意されたクライアントを実行します。 例外は、次のメッセージで発生します。"要求されたサービス 'http://localhost/servicemodelsamples/service.svc' アクティブにできませんでした"。 これは予期される例外です。エンドポイント検証の動作により、エンドポイントがセキュリティで保護されていないと見なされ、サービスが開始されないためです。 さらにこの動作によって、エンドポイントがセキュリティ保護されていないという内部例外がスローされ、システム イベント ビューアで "WebHost" カテゴリの "System.ServiceModel 4.0.0.0" ソースの下にメッセージが書き込まれます。 さらにこのサンプルでは、サービスのトレースを有効にできます。 これによって、サービス トレース ビューア ツールを使用してサービス トレースの結果を開き、エンドポイント検証の動作からスローされた例外を表示することができます。  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>エンドポイント検証エラーの例外メッセージをイベント ビューアーで表示するには  
  
1. をクリックして、**開始**メニュー**を実行しています**.  
  
2. 型`eventvwr`クリック**OK**。  
  
3. イベント ビューアー ウィンドウで次のようにクリックします。**アプリケーション**します。  
  
4. "WebHost"カテゴリの下に最近追加された"System.ServiceModel 4.0.0.0"イベントをダブルクリックして、**アプリケーション**安全でないエンドポイントのメッセージを表示するウィンドウ。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)

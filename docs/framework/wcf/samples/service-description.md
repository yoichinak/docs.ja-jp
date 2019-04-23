---
title: サービスの説明
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d68bc3f304a9ade8ab17729fb23b5bd89b007d0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771324"
---
# <a name="service-description"></a>サービスの説明
サービスの説明のサンプルでは、サービスが実行時にそのサービスの説明情報を取得する方法を示します。 サンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)で、追加のサービス操作が、サービスに関する説明情報を返すように定義します。 返される情報には、サービスのベース アドレスとエンドポイントが示されます。 サービスは、<xref:System.ServiceModel.OperationContext>、<xref:System.ServiceModel.ServiceHost>、および <xref:System.ServiceModel.Description.ServiceDescription> クラスを使用してこの情報を提供します。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルには、`IServiceDescriptionCalculator` という電卓コントラクトの修正バージョンがあります。 このコントラクトでは、`GetServiceDescriptionInfo` という名前の追加サービス操作が定義されています。このサービス操作は、サービスのベース アドレス (1 つまたは複数) とサービス エンドポイント (1 つまたは複数) を説明する、複数行の文字列をクライアントに返します。  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 `GetServiceDescriptionInfo` の実装コードには、サービス エンドポイントを示す <xref:System.ServiceModel.Description.ServiceDescription> が使用されています。 サービス エンドポイントには相対アドレスを指定できるので、最初にサービスのベース アドレスが示されます。 この情報をすべて取得するには、コードで <xref:System.ServiceModel.OperationContext.Current%2A> を使用して操作コンテキストを取得します。 その操作コンテキストから、<xref:System.ServiceModel.ServiceHost> とその <xref:System.ServiceModel.Description.ServiceDescription> オブジェクトが取得されます。 サービスのベース エンドポイント一覧を示すには、コードにより、サービス ホストの <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> コレクションを反復処理します。 サービスのサービス エンドポイント一覧を示すには、コードにより、サービス説明のエンドポイント コレクションを反復処理します。  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 サンプルを実行すると、電卓操作が表示され、次に `GetServiceDescriptionInfo` 操作によって返されたサービス情報が表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  

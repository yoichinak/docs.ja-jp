---
title: '方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184836"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する
Wcf (WCF) では、クライアント Web サイト上の JavaScript から呼び出すことができる ASP.NET AJAX 対応エンドポイントを使用できるようにするサービスを作成できます。 このようなエンドポイントを作成するには、構成ファイルを使用するか、他のすべての Windows 通信基盤 (WCF) エンドポイントと同様に、または構成要素を必要としないメソッドを使用できます。 ここでは、構成を使用する方法について説明します。  
  
 サービス エンドポイントを AJAX 対応にASP.NETできるようにする手順の部分は、エンドポイントを使用<xref:System.ServiceModel.WebHttpBinding>して[\<、エンドポイントの動作を有効](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)にして、エンドポイントの動作を追加>設定します。 エンドポイントを構成した後、サービスを実装してホストする手順は、WCF サービスで使用されるものと似ています。 動作例については、「 HTTP [POST を使用した AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)」を参照してください。  
  
 構成を使用せずに AJAX ASP.NETエンドポイントを構成する方法の詳細については、「[方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)」を参照してください。  
  
## <a name="to-create-a-basic-wcf-service"></a>基本的な WCF サービスを作成するには  
  
1. 属性でマークされたインターフェイスを使用して、基本的な<xref:System.ServiceModel.ServiceContractAttribute>WCF サービス コントラクトを定義します。 各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. `ICalculator` を使用して、`CalculatorService` サービス コントラクトを実装します。  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. 名前空間ブロック内にラップすることにより、`ICalculator` と `CalculatorService` の実装の名前空間を定義します。  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>サービスに ASP.NET AJAX エンドポイントを作成するには  
  
1. 動作構成を作成し、サービス[\<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)の AJAX 対応エンドポイントASP.NET対して WebScript>の有効化動作を指定します。  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <xref:System.ServiceModel.WebHttpBinding> と、前の手順で定義した ASP.NET AJAX 動作を使用するサービスのエンドポイントを作成します。  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a>IIS でサービスをホストするには  
  
1. IIS でサービスをホストするには、アプリケーションで .svc 拡張子の新しいサービス ファイルを作成します。 サービスに適切な[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ情報を追加して、このファイルを編集します。 たとえば、`CalculatorService` サンプルに対応するサービス ファイルのコンテンツには、次の情報が記述されています。  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. IIS でのホストの詳細については、「[方法 : IIS で WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)」を参照してください。  
  
## <a name="to-call-the-service"></a>サービスを呼び出すには  
  
1. エンドポイントは .svc ファイルに対する空のアドレスで構成されるため、サービスは現在利用可能になり、service.svc/\<操作>に要求を送信して呼び出すことができます 。 `Add` これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにエンドポイント URL を入力することで使用できます。 例については、 HTTP [POST を使用した AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)

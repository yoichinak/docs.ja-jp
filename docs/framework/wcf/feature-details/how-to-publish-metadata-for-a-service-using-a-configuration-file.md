---
title: '方法: 構成ファイルを使用してサービスのメタデータを公開する'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 367ebeee5c12d809a758f1bee73dfaadda85788d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295537"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>方法: 構成ファイルを使用してサービスのメタデータを公開する
これは、Windows Communication Foundation (WCF) サービスのメタデータの公開を示す 2 つの操作方法に関するトピックのいずれかです。 構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は 2 つあります。 このトピックでは、構成ファイルを使用してサービスのメタデータを公開する方法について説明します。  
  
> [!CAUTION]
>  このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。 クライアントは、サービスからメタデータを取得できます。 安全な方法でメタデータを公開するサービスを必要とする場合は、次を参照してください。[メタデータ エンドポイントのセキュリティで保護されたカスタム](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)します。  
  
 コードでメタデータの公開の詳細については、次を参照してください。[方法。コードを使用してサービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)します。 メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。 コードが動作していることを確認するには、基本的な WCF サービスを作成します。 簡略化のため、次のコードに基本的な自己ホスト型サービスが用意されています。  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 これは、構成ファイルを使用して構成された自己ホスト型サービスです。 以下の構成ファイルをベースとして使用します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>アプリケーション構成ファイルを使用して WCF サービスのメタデータを公開するには  
  
1. `</services>` 要素を閉じた後、App.config ファイル内に `<behaviors>` 要素を作成します。  

2. `<behaviors>` 要素内に `<serviceBehaviors>` 要素を追加します。  

3. `<behavior>`要素に `<serviceBehaviors>` 要素を追加し、`name` 要素の `<behavior>` 属性に値を指定します。  

4. `<serviceMetadata>` 要素を `<behavior>` 要素に追加します。 `httpGetEnabled` 属性を `true` に設定し、`policyVersion` 属性を Policy15 に設定します。 `httpGetEnabled` HTTP GET 要求からのメタデータ要求に応答するサービスを使用します。 `policyVersion` メタデータを生成するときに、Ws-policy 1.5 に準拠するようにサービスに通知します。  

5. 次のコード例に示すように、`behaviorConfiguration` 要素に `<service>` 属性を追加し、手順 1. で追加した `name` 要素の `<behavior>` 属性を指定します。  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. 1 つ以上の `<endpoint>` 要素を追加して、コントラクトを `IMetadataExchange` に設定します。コード例を次に示します。  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. 前の手順で追加したメタデータ エンドポイントについて、`binding` 属性に次のいずれかの値を設定します。  
  
    -   `mexHttpBinding` HTTP 公開の場合、  
  
    -   `mexHttpsBinding` HTTPS 公開の場合、  
  
    -   `mexNamedPipeBinding` 名前付きパイプ公開の場合、  
  
    -   `mexTcpBinding` TCP 公開の場合、  
  
8. 前の手順で追加したメタデータ エンドポイントについて、次のいずれかに等しいアドレスを設定します。  
  
    -   ベース アドレスがメタデータ バインディングと同じ場合に、公開ポイントとしてホスト アプリケーションのベース アドレスを使用するための空の文字列  
  
    -   ホスト アプリケーションにベース アドレスがある場合、相対アドレス  
  
    -   絶対アドレス  
  
9. コンソール アプリケーションのビルドと実行  
  
10. Internet Explorer を使用して、サービスのベース アドレスを参照 (http://localhost:8001/MetadataSampleこのサンプルでは) し、メタデータの公開が有効であることを確認します。 ない場合は、結果のページの上部にあるメッセージが表示されます。「このサービスのメタデータの公開は現在無効です。」  
  
### <a name="to-use-default-endpoints"></a>既定のエンドポイントを使用するには  
  
1. 既定のエンドポイントを使用するサービスでメタデータを構成するには、前の例のように、構成ファイルで <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を指定します。ただし、エンドポイントは指定しないでください。 構成ファイルは、次のようになります。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     サービスの <xref:System.ServiceModel.Description.ServiceMetadataBehavior> では `httpGetEnabled` が `true` に設定されているため、サービスではメタデータの公開が有効になっています。また、エンドポイントが明示的に追加されていないため、ランタイムは既定のエンドポイントを追加します。 既定のエンドポイントについては、「[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、基本的な WCF サービスとサービスのメタデータを公開する構成ファイルの実装を示します。  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [方法: マネージド アプリケーションで WCF サービスをホストする](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)
- [メタデータ アーキテクチャの概要](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [方法: コードを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)

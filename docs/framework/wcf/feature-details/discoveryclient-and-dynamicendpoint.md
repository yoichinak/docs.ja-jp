---
title: DiscoveryClient と DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 1f3e9a25e82c4515ee649736ed162ab858aa6ff7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205031"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient と DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> <xref:System.ServiceModel.Discovery.DynamicEndpoint> 2 つのクラスが、クライアント側でサービスを検索するために使用します。 <xref:System.ServiceModel.Discovery.DiscoveryClient> 条件の設定、特定の一致するサービスの一覧を表示し、サービスに接続することができますを提供します。 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 同じ操作を実行し、さらに、いずれか見つかったサービスに自動的に接続します。 <xref:System.ServiceModel.Discovery.DynamicEndpoint> には任意のエンドポイントを指定でき、構成に検索条件も追加できます。このため、ソリューションに探索機能が必要だが、クライアント ロジックを変更したくないという場合は、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を使用すると、エンドポイントを変更するだけで済み、便利です。 <xref:System.ServiceModel.Discovery.DiscoveryClient> その一方で使用できます、検索操作をより細かく制御できます。 次に、それぞれのクラスの用途と利点について詳しく説明します。  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> は、同期および非同期の Find メソッド、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベント、および <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントを定義します。  さらに、同期および非同期の Resolve メソッド、および <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> イベントも定義します。 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドまたは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> メソッドを使用して、サービスを検索します。 これらのメソッドは両方とも <xref:System.ServiceModel.Discovery.FindCriteria> インスタンスを受け取ります。このインスタンスにより、コントラクト型名、スコープ、要求した結果の最大数、およびスコープ一致規則の指定が可能になります。 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> メソッドを呼び出す際には、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントおよび <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> イベントが使用できます。 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 発生したときに、<xref:System.ServiceModel.Discovery.DiscoveryClient>サービスから応答を受信します。 これを使用して、検索操作の進捗状況を示すプログレス バーを表示できます。 また、受け取った検索応答を処理するのにも使用できます。 検索操作が完了すると、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベントが発生します。 最大数の応答を受信した場合、または <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> が経過した場合に、これが発生することがあります。 検索操作が完了すると、結果が <xref:System.ServiceModel.Discovery.FindResponse> インスタンスで返されます。 <xref:System.ServiceModel.Discovery.FindResponse> には <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションが含まれており、これには、一致するサービスのアドレス、コントラクト型名、拡張子、リッスン URI、およびスコープが格納されています。 この情報を使用して、一致するいずれかのサービスに接続し、呼び出すことができます。 次の例では、System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) メソッドを呼び出し、見つかったサービスの呼び出し、返されたメタデータを使用する方法を示します。 使用する利点<xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)>が見つかったし、し、後で使用するエンドポイントの一覧をキャッシュすることができます。 このキャッシュを使用して、さまざまなエラー状況を処理するカスタム ロジックを構築できます。  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 次の例は、検索操作を非同期で実行する方法を示しています。  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 エンドポイント アドレスに基づいてサービスを検索するには、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> メソッドおよび <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> メソッドを使用します。 エンドポイント アドレスをネットワーク アドレスで指定できないアドレスの場合は、これが便利です。 Resolve メソッドは、<xref:System.ServiceModel.Discovery.ResolveCriteria> のインスタンスを受け取ります。このインスタンスは、解決するサービスのエンドポイント アドレス、解決操作の最大期間、および拡張のセットを指定できるようにします。 次の例は、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> メソッドを使用してサービスを解決する方法を示しています。  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 標準エンドポイントです (詳細については、次を参照してください。[標準エンドポイント](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) 検索を実行すると自動的に一致するサービスを選択します。 <xref:System.ServiceModel.Discovery.DynamicEndpoint> を作成して、検索するコントラクトおよび使用するバインディングを渡し、<xref:System.ServiceModel.Discovery.DynamicEndpoint> インスタンスを WCF クライアントに渡します。 次の例は、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を作成および使用して電卓サービスを呼び出す方法を示しています。 クライアントが開かれるたびに、探索が実行されます。 構成で定義されている任意のエンドポイントをオンにできます、<xref:System.ServiceModel.Discovery.DynamicEndpoint>を追加して、`kind ="dynamicEndpoint"`属性をエンドポイント構成要素。  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a>関連項目

- [スコープを使用した探索](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Basic](../../../../docs/framework/wcf/samples/basic-sample.md)

---
title: 探索アナウンスとアナウンス クライアント
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040178"
---
# <a name="discovery-announcements-and-announcement-client"></a>探索アナウンスとアナウンス クライアント

WCF 検出機能を使用すると、コンポーネントはその可用性をアナウンスできます。 そのように構成されている場合、サービスは Hello アナウンスと Bye アナウンスを送信します。 クライアントまたはその他のコンポーネントは、それらのアナウンス メッセージをリッスンして、対応します。 これにより、クライアントは別の手段でサービスを認識します。 アナウンス機能にはいくつかの用途があります。たとえば、サービスがネットワークに頻繁に出入りする場合は、サービスを検索するよりも、アナウンスを利用する方が効果的です。 この方法を使用すると、ネットワーク トラフィックが減少し、クライアントは、アナウンスを受信するとすぐに、そのサービスが存在するかどうかを知ることができます。

## <a name="discovery-announcements"></a>探索アナウンス

アナウンスが構成されたサービスがネットワークに参加し、探索可能になると、そのサービスは、リッスンしているクライアントにそのサービスの可用性をアナウンスする Hello メッセージを送信します。 このメッセージには、サービスのコントラクト、エンドポイント アドレス、および関連付けられたスコープなど、探索関連の情報が含まれています。 アナウンス メッセージを送信する先を <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> クラスで指定できます。 アナウンス エンドポイントが <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> の場合、Hello および Bye はマルチキャストです。また、アナウンス エンドポイントがユニキャストの場合、メッセージは指定されたエンドポイントに直接送信されます。

> [!NOTE]
> アナウンスは、サービス ホストが開いたときと閉じたときに送信されます。 これらの呼び出しが適切に終了しない場合は、アナウンス メッセージが送信されないことがあります。たとえば、サービスがエラーになった場合は、Bye アナウンス メッセージが送信されません。

> [!TIP]
> アナウンス機能をカスタマイズして、選択したタイミングでアナウンスを送信することができます。

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] では、<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> および <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> が標準エンドポイントとして定義されているため、サービスとクライアントが簡単に Hello アナウンスと Bye アナウンスを送信できます。

### <a name="announcements-on-the-service"></a>サービスのアナウンス

アナウンスを送信するようにサービスを構成するには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> をアナウンス エンドポイントと共に追加します。 次の例は、この動作をプログラムでサービス ホストに追加する方法を示しています。 この例では、アナウンスが、その標準エンドポイントで指定される場所へのマルチキャストであることを暗黙で示す `UdpAnnouncementEndpoint` を使用しています。

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

この動作は、次の例に示すように、構成ファイルで構成することもできます。

```xml
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

前の例では、サービスが自動的にアナウンス メッセージを送信するように構成します。 <xref:System.ServiceModel.Discovery.AnnouncementClient> クラスを使用して、アナウンス メッセージを明示的に送信することもできます。

### <a name="announcements-on-the-client"></a>クライアントのアナウンス

クライアント アプリケーションは、アナウンス サービスをホストして Hello メッセージと Bye メッセージに応答し、<xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> イベントと <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> イベントを定期受信する必要があります。 その方法を次の例に示します。

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;

// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();

    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}
```

Hello メッセージまたは Bye メッセージを受信したら、次の例に示すように、<xref:System.ServiceModel.Discovery.AnnouncementEventArgs> を介してエンドポイント探索メタデータにアクセスできます。

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}
```

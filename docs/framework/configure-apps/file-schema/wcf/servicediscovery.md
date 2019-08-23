---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936274"
---
# <a name="servicediscovery"></a>\<serviceDiscovery >
サービス エンドポイントの探索可能性を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceDiscovery >  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<発表の >](announcementendpoint.md)|アナウンス エンドポイントのコレクション。 このセクションを使用して、アナウンス メッセージの送信に使用するエンドポイントを指定します。|  
|[\<discoveryEndpoint >](discoveryendpoint.md)|探索エンドポイントのコレクション。 このセクションを使用して、探索メッセージをリッスンするエンドポイントを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 サービスの動作構成に追加すると、この構成要素により、サービスの探索可能性はすべてのエンドポイントで有効になります。 このようなエンドポイントの探索機能をさらに構成するには、 [ \<discoveryendpoint >](discoveryendpoint.md)または[ \<発表者 >](announcementendpoint.md)子要素を使用します。 サービスのお知らせを送信するために使用するエンドポイント構成 (オンライン/Hello およびオフライン/Bye) を指定してアナウンスを構成するには、[ [ \<発表](announcementendpoint.md)者の >] セクションを使用します。 探索メッセージをリッスンするエンドポイントを手動で指定するには、 [ \<discoveryendpoint >](discoveryendpoint.md)セクションを使用します。  
  
## <a name="example"></a>例  
 次の構成例では、CalculatorService を探索可能に指定しています。また、オプションで、使用するアナウンス エンドポイントを指定しています。  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

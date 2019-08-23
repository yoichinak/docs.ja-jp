---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918707"
---
# <a name="host"></a>\<ホスト >
サービス ホストの設定を指定します。  
  
 \<system.ServiceModel >  
\<services>  
\<サービス >  
\<ホスト >  
  
## <a name="syntax"></a>構文  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|サービス ホストによって使用されるベース アドレスを指定する `baseAddress` 要素のコレクション。|  
|[\<timeOuts>](timeouts.md)|サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<service>](service.md)|Windows Communication Foundation (WCF) サービスの設定を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [ホスティング](../../../wcf/feature-details/hosting.md)

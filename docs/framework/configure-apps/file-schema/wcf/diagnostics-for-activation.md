---
title: <diagnostics>アクティブ化の場合
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919219"
---
# <a name="diagnostics-for-activation"></a>\<アクティブ化のための診断 >
Windows Communication Foundation (WCF) リスナーの診断機能を構成します。  
  
 \<system.serviceModel.activation>  
\<診断 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`performanceCountersEnabled`|診断用パフォーマンス カウンターが有効であるかどうかを示すブール値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel.activation >](system-servicemodel-activation.md)|リスナー プロセス SMSvcHost.exe の設定が含まれています。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>

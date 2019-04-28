---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 2db168d48e3959a7d80a10ca27134f58e3fcb2de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758159"
---
# <a name="services"></a>\<services>
サービスは、設定ファイルの `services` セクションで定義されます。 各サービスには、独自の `service` 設定セクションがあります。  
  
 \<system.ServiceModel >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServicesSection>

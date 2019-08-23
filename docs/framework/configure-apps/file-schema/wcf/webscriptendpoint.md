---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940402"
---
# <a name="webscriptendpoint"></a>\<webScriptEndpoint >
この構成要素は、 [ \<enablewebscript >](enablewebscript.md)動作を自動的に追加する固定[ \<の webHttpBinding >](webhttpbinding.md)バインドを持つ標準エンドポイントを定義します。 このエンドポイントは、ASP.NET AJAX アプリケーションから呼び出されるサービスを作成する場合に使用します。  
  
\<system.ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|webEndpointType|エンドポイントの種類を指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>

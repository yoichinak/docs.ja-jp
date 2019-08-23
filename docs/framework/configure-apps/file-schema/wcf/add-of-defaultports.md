---
title: <add> の <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926709"
---
# <a name="add-of-defaultports"></a>\<defaultports の\<> を追加し >
クライアント アプリケーションがリッスンする既定の通信エンドポイント。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<useRequestHeadersForMetadataAddress >  
\<defaultPorts >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|ポート|既定の通信ポート番号を指定する整数。|  
|scheme|通信ポートに関連付けられているプロトコル設定のグループを示す文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.DefaultPortElement>

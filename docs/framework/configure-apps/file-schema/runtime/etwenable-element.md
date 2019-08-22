---
title: <etwEnable> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f24e9a06137744dbc97d5f34cda7ad6eab873700
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663739"
---
# <a name="etwenable-element"></a>\<etwEnable > 要素
共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。  
  
 \<configuration> 要素  
\<runtime> 要素  
\<etwEnabled >  
  
## <a name="syntax"></a>構文  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> ETW を有効にするかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|true|ETW を有効にします。 Windows Vista および Windows Server 2008 オペレーティングシステム以降のバージョンの Windows では、これが既定です。|  
|False|ETW を無効にします。 これは、以前のバージョンの Windows では既定です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 Windows Vista 以降では、ETW は既定で有効になっています。 アプリケーションの ETW を無効にするには、この要素を使用します。 以前のバージョンの Windows では、この要素を使用して、アプリケーションの ETW を有効にします。  
  
> [!NOTE]
>  ETW は、レジストリ設定を使用して、サーバー上でグローバルに有効または無効にすることができます。 「 [.NET Framework のログ記録の制御](../../../performance/controlling-logging.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、アプリケーションの ETW トレースを有効にする方法を示しています。  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [.NET Framework のログ記録の制御](../../../performance/controlling-logging.md)

---
title: <etwEnable> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba411114bfb853e06c83adb42713d43f1452d9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135071"
---
# <a name="etwenable-element"></a>\<etwEnable > 要素
共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。  
  
 \<configuration > 要素  
\<ランタイム > 要素  
\<etwEnabled>  
  
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
|true|ETW を有効にします。 これは、Windows、Windows Vista および Windows Server 2008 オペレーティング システム以降のバージョンの既定値です。|  
|False|ETW を無効にします。 これは、Windows の以前のバージョンの既定値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 ETW は Windows Vista 以降、既定で有効です。 アプリケーションの ETW を無効にするのにには、この要素を使用します。 Windows の以前のバージョンでは、アプリケーションの ETW を有効にするのにこの要素を使用します。  
  
> [!NOTE]
>  ETW を有効になっているか、レジストリ設定を使用して、サーバーでグローバルに無効にします。 参照してください[.NET Framework のログ記録を制御する](../../../../../docs/framework/performance/controlling-logging.md)します。  
  
## <a name="example"></a>例  
 次の例では、アプリケーションの ETW トレースを有効にする方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [.NET Framework のログ記録の制御](../../../../../docs/framework/performance/controlling-logging.md)

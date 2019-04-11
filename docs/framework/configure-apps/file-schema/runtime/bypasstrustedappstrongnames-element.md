---
title: <bypassTrustedAppStrongNames> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c39d9a1e3da9cccb2f027e9597a6f2272d187ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179141"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames > 要素
完全信頼に読み込まれる完全に信頼されたアセンブリに厳密な名前の検証をバイパスするかどうかを指定します<xref:System.AppDomain>します。  
  
 \<configuration>  
\<runtime>  
\<bypassTrustedAppStrongNames>  
  
## <a name="syntax"></a>構文  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 完全信頼アセンブリの厳密な名前の検証を回避するバイパス機能が有効になっているかどうかを指定します。 この機能を有効にすると、アセンブリが読み込まれると正確性の厳密な名前は検証されません。 既定値は `true` です。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`true`|アセンブリが完全信頼に読み込まれるときに、完全信頼アセンブリの厳密な名前の署名は検証されません<xref:System.AppDomain>します。 既定値です。|  
|`false`|アセンブリが完全信頼に読み込まれるときに完全信頼アセンブリの厳密な名前の署名は検証<xref:System.AppDomain>です。 署名の正確性ののみ、厳密な名前の署名がチェックします。別の厳密な名前の一致しないと比較されます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 厳密な名前のバイパス機能は、完全信頼アセンブリの厳密な名前の署名の検証のオーバーヘッドを回避できます。  
  
 バイ パス機能は、厳密な名前で署名されていて、次の特性を持つアセンブリに適用されます。  
  
-   なく完全に信頼された、<xref:System.Security.Policy.StrongName>証拠 (たとえば、`MyComputer`ゾーン証拠)。  
  
-   完全に信頼された <xref:System.AppDomain> に読み込まれる。  
  
-   その <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティに基づいた場所から読み込まれる。  
  
-   遅延署名されていない。  
  
> [!NOTE]
>  バイパス機能がオフになっているコンピューター上のすべてのアプリケーションのレジストリ キーを使用して場合は、この構成ファイルの設定に影響はありません。 詳細については、「[方法 :厳密な名前のバイパス機能を無効にする](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)します。  
  
## <a name="example"></a>例  
 次の例では、完全信頼アセンブリの厳密な名前の署名を検証する動作を指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [方法: 厳密な名前のバイパス機能を無効にする](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)

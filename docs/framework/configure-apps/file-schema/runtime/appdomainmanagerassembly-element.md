---
title: <appDomainManagerAssembly> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe1dfbd62a6967ae51031fa12f80e9c5563dc44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704922"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly > 要素
プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。  
  
 \<configuration>  
\<runtime>  
\<appDomainManagerAssembly>  
  
## <a name="syntax"></a>構文  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`value`|必須の属性です。 プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリの表示名を指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 アプリケーション ドメイン マネージャーの種類を指定するには、この両方の要素を指定する必要があります、 [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)要素。 これらの要素のいずれかが指定されていない場合、その他は無視されます。  
  
 既定のアプリケーション ドメインが読み込まれるときに<xref:System.TypeLoadException>が、指定したアセンブリが存在しない場合、またはアセンブリに指定した型が含まれていない場合にスローされます、 [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)要素とプロセスは、開始に失敗します。 アセンブリが見つかりましたが、バージョン情報が一致しない場合、<xref:System.IO.FileLoadException>がスローされます。  
  
 既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの種類を指定すると、既定のアプリケーション ドメインから作成されたその他のアプリケーション ドメインは、アプリケーション ドメイン マネージャーの型を継承します。 使用して、<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>と<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>プロパティを新しいアプリケーション ドメインの別のアプリケーション ドメイン マネージャーの種類を指定します。  
  
 アプリケーション ドメイン マネージャーの種類を指定するには、完全な信頼のアプリケーションが必要です。 (たとえば、デスクトップで実行されているアプリケーションは完全な信頼があります。)アプリケーションには、完全な信頼がない場合、<xref:System.TypeLoadException>がスローされます。  
  
 アセンブリの表示名の形式の場合、次を参照してください。、<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>プロパティ。  
  
 この構成要素はでのみ使用できますが、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]以降。  
  
## <a name="example"></a>例  
 次の例では、プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを指定する方法を示しています、`MyMgr`で入力、`AdMgrExample`アセンブリ。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<appDomainManagerType > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType メソッド](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)

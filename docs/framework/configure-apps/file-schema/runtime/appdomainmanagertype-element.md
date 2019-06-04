---
title: <appDomainManagerType> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19cd74f0e2550ec91cb56e70cf34a03bd84fc60e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487741"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType > 要素
既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの役割を果たす種類を指定します。  
  
 \<configuration>  
\<runtime>  
\<appDomainManagerType>  
  
## <a name="syntax"></a>構文  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`value`|必須の属性です。 プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーとして機能する名前空間を含む、型の名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 アプリケーション ドメイン マネージャーの種類を指定するには、この両方の要素を指定する必要があります、 [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)要素。 これらの要素のいずれかが指定されていない場合、その他は無視されます。  
  
 既定のアプリケーション ドメインが読み込まれるときに<xref:System.TypeLoadException>で指定されたアセンブリでは、指定した型が存在しない場合にスローされる、 [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)要素; とプロセスが失敗する起動します。  
  
 既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの種類を指定すると、既定のアプリケーション ドメインから作成されたその他のアプリケーション ドメインは、アプリケーション ドメイン マネージャーの型を継承します。 使用して、<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>と<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>プロパティを新しいアプリケーション ドメインの別のアプリケーション ドメイン マネージャーの種類を指定します。  
  
 アプリケーション ドメイン マネージャーの種類を指定するには、完全な信頼のアプリケーションが必要です。 (たとえば、デスクトップで実行されているアプリケーションは完全な信頼があります。)アプリケーションには、完全な信頼がない場合、<xref:System.TypeLoadException>がスローされます。  
  
 型および名前空間の形式が使用されるのと同じ形式、<xref:System.Type.FullName%2A?displayProperty=nameWithType>プロパティ。  
  
 この構成要素は、以降、.NET Framework 4 でのみ使用できます。  
  
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
- [\<appDomainManagerAssembly > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)
- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType メソッド](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)

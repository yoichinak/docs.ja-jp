---
title: <appDomainManagerAssembly> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154429"
---
# <a name="appdomainmanagerassembly-element"></a>\<要素>アセンブリ
プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
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
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 アプリケーション ドメイン マネージャーの種類を指定するには、この要素と要素の[\<appDomainManagerType>](appdomainmanagertype-element.md)両方を指定する必要があります。 これらの要素のいずれかが指定されていない場合、もう一方は無視されます。  
  
 既定のアプリケーション ドメインが読み<xref:System.TypeLoadException>込まれると、指定したアセンブリが存在しない場合、またはアセンブリに[\<appDomainManagerType>](appdomainmanagertype-element.md)要素で指定された型が含まれていない場合、スローされます。プロセスが開始されない。 アセンブリが見つかったがバージョン情報が一致しない場合は、<xref:System.IO.FileLoadException>がスローされます。  
  
 既定のアプリケーション ドメインに対してアプリケーション ドメイン マネージャーの種類を指定すると、既定のアプリケーション ドメインから作成された他のアプリケーション ドメインは、アプリケーション ドメイン マネージャーの種類を継承します。 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>プロパティと<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>プロパティを使用して、新しいアプリケーション ドメインに対して異なるアプリケーション ドメイン マネージャーの種類を指定します。  
  
 アプリケーション ドメイン マネージャーの種類を指定するには、アプリケーションに完全な信頼が必要です。 (たとえば、デスクトップで実行されているアプリケーションには完全な信頼があります)。アプリケーションに完全な信頼がない場合は、<xref:System.TypeLoadException>がスローされます。  
  
 アセンブリの表示名の形式については、プロパティを<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>参照してください。  
  
 この構成要素は、.NET Framework 4 以降でのみ使用できます。  
  
## <a name="example"></a>例  
 次の例は、プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーがアセンブリ内の`MyMgr`型であることを指定`AdMgrExample`する方法を示しています。  
  
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
- [\<要素>タイプ](appdomainmanagertype-element.md)
- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [SetAppDomainManagerType メソッド](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)

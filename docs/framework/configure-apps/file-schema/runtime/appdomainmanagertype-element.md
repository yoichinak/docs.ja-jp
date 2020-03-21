---
title: <appDomainManagerType> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154428"
---
# <a name="appdomainmanagertype-element"></a>\<要素>タイプ
既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの役割を果たす種類を指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>タイプ**  
  
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
|`value`|必須の属性です。 プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーとして機能する、名前空間を含む型の名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 アプリケーション ドメイン マネージャーの種類を指定するには、この要素と[\<、>要素の両方](appdomainmanagerassembly-element.md)を指定する必要があります。 これらの要素のいずれかが指定されていない場合、もう一方は無視されます。  
  
 既定のアプリケーション ドメインが読み<xref:System.TypeLoadException>込まれると、指定した型が[\<、appDomainManagerAssembly>](appdomainmanagerassembly-element.md)要素で指定されたアセンブリに存在しない場合はスローされます。プロセスが開始されない。  
  
 既定のアプリケーション ドメインに対してアプリケーション ドメイン マネージャーの種類を指定すると、既定のアプリケーション ドメインから作成された他のアプリケーション ドメインは、アプリケーション ドメイン マネージャーの種類を継承します。 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>プロパティと<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>プロパティを使用して、新しいアプリケーション ドメインに対して異なるアプリケーション ドメイン マネージャーの種類を指定します。  
  
 アプリケーション ドメイン マネージャーの種類を指定するには、アプリケーションに完全な信頼が必要です。 (たとえば、デスクトップで実行されているアプリケーションには完全な信頼があります)。アプリケーションに完全な信頼がない場合は、<xref:System.TypeLoadException>がスローされます。  
  
 型と名前空間の形式は、<xref:System.Type.FullName%2A?displayProperty=nameWithType>プロパティに使用される形式と同じです。  
  
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
- [\<要素>アセンブリ](appdomainmanagerassembly-element.md)
- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [SetAppDomainManagerType メソッド](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)

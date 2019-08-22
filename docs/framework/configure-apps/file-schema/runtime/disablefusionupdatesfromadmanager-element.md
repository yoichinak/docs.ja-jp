---
title: <disableFusionUpdatesFromADManager> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663773"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > 要素
アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドする既定の動作を無効化するかどうかを指定します。  
  
 \<configuration> 要素  
\<runtime> 要素  
\<disableFusionUpdatesFromADManager>  
  
## <a name="syntax"></a>構文  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> Fusion 設定をオーバーライドする既定の機能が無効になっているかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|Fusion の設定をオーバーライドする機能を無効にしないでください。 これは、.NET Framework 4 から始まる既定の動作です。|  
|1|Fusion の設定をオーバーライドする機能を無効にします。 これにより、.NET Framework の以前のバージョンの動作に戻ります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework 4 以降では、既定の動作は、実装に<xref:System.AppDomainManager>渡される<xref:System.AppDomainSetup>オブジェクトの<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティまたは<xref:System.AppDomainSetup.SetConfigurationBytes%2A>メソッドを使用して、オブジェクトが構成設定をオーバーライドできるようにすることです。メソッドの (の<xref:System.AppDomainManager>サブクラス内)。 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 既定のアプリケーションドメインでは、変更した設定によって、アプリケーション構成ファイルで指定された設定が上書きされます。 他のアプリケーションドメインで<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>は、メソッドまたは<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>メソッドに渡された構成設定がオーバーライドされます。  
  
 新しい構成情報を渡すか、null (`Nothing` Visual Basic) を渡して、渡された構成情報を削除することができます。  
  
 <xref:System.AppDomainSetup.ConfigurationFile%2A> プロパティ<xref:System.AppDomainSetup.SetConfigurationBytes%2A>とメソッドの両方に構成情報を渡さないでください。 構成情報を両方に渡すと、 <xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティに渡す情報は無視されます。 <xref:System.AppDomainSetup.SetConfigurationBytes%2A>これは、メソッドによってアプリケーション構成ファイルの構成情報がオーバーライドされるためです。 <xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティを使用する場合は、 <xref:System.AppDomainSetup.SetConfigurationBytes%2A>メソッドに null (`Nothing` Visual Basic) を渡して、メソッドまたは<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>メソッドの<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>呼び出しで指定された構成バイトを削除できます。  
  
 構成情報<xref:System.AppDomainSetup>に加えて、 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッドの実装に渡されるオブジェクトの次の設定を変更できます。 <xref:System.AppDomainSetup.ApplicationBase%2A>、 <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A>、、、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A><xref:System.AppDomainSetup.DisallowCodeDownload%2A> 、、<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>、 、、<xref:System.AppDomainSetup.DynamicBase%2A>、、、および。<xref:System.AppDomainSetup.ShadowCopyFiles%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>  
  
 `<disableFusionUpdatesFromADManager>`要素を使用する代わりに、レジストリ設定を作成するか、環境変数を設定することによって、既定の動作を無効にすることができます。 レジストリで、または`COMPLUS_disableFusionUpdatesFromADManager` `HKLM\Software\Microsoft\.NETFramework`の下`HKCU\Software\Microsoft\.NETFramework`にという名前の DWORD 値を作成し、値を1に設定します。 コマンドラインで、環境変数`COMPLUS_disableFusionUpdatesFromADManager`を1に設定します。  
  
## <a name="example"></a>例  
 `<disableFusionUpdatesFromADManager>`要素を使用して Fusion 設定をオーバーライドする機能を無効にする方法を次の例に示します。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [ランタイムがアセンブリを検索する方法](../../../deployment/how-the-runtime-locates-assemblies.md)

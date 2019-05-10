---
title: <disableCachingBindingFailures> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4893adaf528f1a9ef8fc8eab8027406fd8520cc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704792"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures > 要素
バインディングを調査して、アセンブリが見つからなかったために発生したエラーのキャッシュを無効にするかどうかを指定します。  
  
 \<configuration > 要素  
\<runtime> 要素  
\<disableCachingBindingFailures>  
  
## <a name="syntax"></a>構文  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> バインディングを調査して、アセンブリが見つからなかったために発生したエラーのキャッシュを無効にするかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|バインディングを調査して、アセンブリが見つからなかったために発生したエラーのキャッシュを無効にできません。 これは、.NET Framework version 2.0 以降で既定のバインドの動作です。|  
|1|バインディングを調査して、アセンブリが見つからなかったために発生したエラーのキャッシュを無効にします。 この設定は、.NET Framework version 1.1 のバインドの動作に戻ります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 以降、.NET Framework version 2.0 では、アセンブリを読み込むための既定の動作は、すべてのバインドと読み込みエラーをキャッシュするのには。 アセンブリを読み込もうとしましたが失敗した場合、後続の要求に同じアセンブリの読み込みは即座に失敗、アセンブリを検索しようとするとします。 この要素は、バインディング、アセンブリをプローブ パスに見つかりませんだったために発生したエラーの既定の動作を無効にします。 このようなエラーをスロー<xref:System.IO.FileNotFoundException>します。  
  
 いくつかのバインドと読み込みエラーは、この要素の影響は受けませんされ、常にキャッシュされます。 アセンブリが見つかりましたが、読み込むことができないために、このようなエラーが発生します。 スロー<xref:System.BadImageFormatException>または<xref:System.IO.FileLoadException>します。 次の一覧には、このようなエラーのいくつかの例が含まれています。  
  
- ロードしようとした場合、ファイルが有効なアセンブリではない、悪意のあるファイルは、適切なアセンブリに置き換えられます場合でも、後続のアセンブリの読み込みは失敗します。  
  
- ファイル システムによってロックされているアセンブリをロードしようとすると、アセンブリは、ファイル システムでリリースされた後でもアセンブリの読み込みを後続の試行は失敗します。  
  
- プローブのパスがロードしようとしているアセンブリの 1 つまたは複数のバージョンが、それらの間で要求している特定のバージョンがない、正しいバージョンがプローブ パスに移動された場合でもそのバージョンをロードしようは失敗します。  
  
## <a name="example"></a>例  
 次の例では、アセンブリ バインディング エラーを調査して、アセンブリが見つからなかったために発生したのキャッシュを無効にする方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)

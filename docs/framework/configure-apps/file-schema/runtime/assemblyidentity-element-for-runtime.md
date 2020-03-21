---
title: <runtime> の <assemblyIdentity> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154310"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<ランタイム>の\<アセンブリID>要素
アセンブリに関する識別情報を格納します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<アセンブリバインディング>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<従属アセンブリ>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<アセンブリ識別>**  
  
## <a name="syntax"></a>構文  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須の属性です。<br /><br /> アセンブリの名前|  
|`culture`|省略可能な属性です。<br /><br /> アセンブリの言語と国/地域を指定する文字列。|  
|`publicKeyToken`|省略可能な属性です。<br /><br /> アセンブリの厳密な名前を指定する 16 進値。|  
|`processorArchitecture`|省略可能な属性です。<br /><br /> "x86"、"amd64"、"msil"、または "ia64"の値の 1 つで、プロセッサ固有のコードを含むアセンブリのプロセッサ アーキテクチャを指定します。 値は大文字と小文字を区別しません。 属性に他の値が割り当てられている場合`<assemblyIdentity>`、要素全体は無視されます。 [https://docs.microsoft.com/azure/active-directory/develop/scenario-protected-web-api-overview](<xref:System.Reflection.ProcessorArchitecture>) をご覧ください。|  
  
## <a name="processorarchitecture-attribute"></a>プロセッサアーキテクチャ属性  
  
|Value|説明|  
|-----------|-----------------|  
|`amd64`|AMD x86-64 アーキテクチャのみ。|  
|`ia64`|インテル・イタニウム・アーキテクチャーのみ。|  
|`msil`|プロセッサおよびワードあたりのビット数に関して中立|  
|`x86`|ネイティブまたは Windows on Windows (WOW) 環境で、64 ビット プラットフォーム上の 32 ビット x86 プロセッサ。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`dependentAssembly`|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。 各アセンブリ`<dependentAssembly>`に 1 つの要素を使用します。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 すべての**\<従属アセンブリアセンブリ>** 要素は、子要素**\<>アセンブリを**1 つ持つ必要があります。  
  
 属性が`processorArchitecture`存在する`<assemblyIdentity>`場合、要素は対応するプロセッサ アーキテクチャを持つアセンブリにのみ適用されます。 属性が`processorArchitecture`存在しない場合、要素は`<assemblyIdentity>`、任意のプロセッサ アーキテクチャを持つアセンブリに適用できます。  
  
 次の例は、2 つの異なる 2 つのプロセッサ アーキテクチャを対象とし、バージョンが同期して維持されていない同じ名前の 2 つのアセンブリの構成ファイルを示しています。アプリケーションが x86 プラットフォームで実行されると、`<assemblyIdentity>`最初の要素が適用され、もう一方の要素は無視されます。 アプリケーションが x86 または ia64 以外のプラットフォームで実行される場合、両方が無視されます。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 構成ファイルに属性のない`<assemblyIdentity>``processorArchitecture`要素が含まれ、プラットフォームに一致する要素が含まれていない場合は、`processorArchitecture`属性のない要素が使用されます。  
  
## <a name="example"></a>例  
 アセンブリに関する情報を提供する方法を次の例に示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [アセンブリ バージョンのリダイレクト](../../redirect-assembly-versions.md)

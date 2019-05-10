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
ms.openlocfilehash: d5766b76f18dce441cb260887a753dcf64642a6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674234"
---
# <a name="assemblyidentity-element-for-runtime"></a><runtime> の <assemblyIdentity> 要素
アセンブリに関する識別情報が含まれています。  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<dependentAssembly>  
\<assemblyIdentity>  
  
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
|`culture`|省略可能な属性です。<br /><br /> 言語と国/地域のアセンブリを指定する文字列。|  
|`publicKeyToken`|省略可能な属性です。<br /><br /> アセンブリの厳密な名前を指定する 16 進値。|  
|`processorArchitecture`|省略可能な属性です。<br /><br /> いずれか、値"x86"、"amd64"、"msil"または"ia64"プロセッサ固有のコードを含むアセンブリのプロセッサ アーキテクチャを指定します。 値小文字は区別されません。 かどうか、属性が他の値、全体が割り当てられます`<assemblyIdentity>`要素は無視されます。 以下を参照してください。<xref:System.Reflection.ProcessorArchitecture>|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture の属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`amd64`|AMD の x86 アーキテクチャのみです。|  
|`ia64`|Intel Itanium アーキテクチャの場合のみです。|  
|`msil`|プロセッサおよびワードあたりのビット数に関して中立です。|  
|`x86`|32 ビット x86 プロセッサ、ネイティブまたは 64 ビット プラットフォームでの Windows (WOW) 環境での Windows でします。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`dependentAssembly`|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。 1 つを使用して、`<dependentAssembly>`各アセンブリの要素。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 すべて **\<dependentAssembly >** 要素が 1 つの **\<assemblyIdentity >** 子要素。  
  
 場合、`processorArchitecture`属性が存在する、`<assemblyIdentity>`要素は、対応するプロセッサ アーキテクチャを使用してアセンブリにのみ適用されます。 場合、`processorArchitecture`属性が存在しない、`<assemblyIdentity>`要素は、すべてのプロセッサ アーキテクチャを持つアセンブリに適用できます。  
  
 次の例を対象に 2 つの 2 つの異なるプロセッサ アーキテクチャ、およびバージョンがない管理が同期して 2 つのアセンブリと同じ名前の構成ファイルを示しています。X86 では、アプリケーションが実行される場合、最初のプラットフォーム`<assemblyIdentity>`要素が適用され、その他は無視されます。 アプリケーションは、x86、または ia64 以外のプラットフォームで実行する場合は両方とも無視されます。  
  
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
  
 構成ファイルが含まれている場合、`<assemblyIdentity>`要素なしで`processorArchitecture`属性、およびプラットフォームでない要素に一致する要素が含まれていない、`processorArchitecture`属性を使用します。  
  
## <a name="example"></a>例  
 次の例では、アセンブリに関する情報を提供する方法を示します。  
  
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

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

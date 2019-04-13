---
title: <qualifyAssembly> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4741c6a4745bdba00fdb525b39b70d0b15e005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109449"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly > 要素
部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<qualifyAssembly>  
  
## <a name="syntax"></a>構文  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`partialName`|必須の属性です。<br /><br /> コードに表示されるアセンブリの部分的な名前を指定します。|  
|`fullName`|必須の属性です。<br /><br /> グローバル アセンブリ キャッシュに表示されるアセンブリの完全な名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 呼び出す、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>部分的なアセンブリ名を使用して、メソッドにより、共通言語ランタイム アプリケーション ベース ディレクトリのみでアセンブリを検索します。 使用して、  **\<qualifyAssembly >** (名前、バージョン、公開キー トークン、およびカルチャ) のアセンブリの完全な情報を入力し、検索する共通言語ランタイムが発生する、アプリケーション構成ファイル内の要素グローバル アセンブリ キャッシュ内のアセンブリ。  
  
 **FullName**属性がアセンブリ id の 4 つのフィールドを含める必要があります。 名前、バージョン、公開キー トークン、およびカルチャ。 **それよりも**属性は、アセンブリを参照部分的にする必要があります。 アセンブリのテキスト名 (最も一般的なケース) を少なくとも指定する必要がありますが、バージョン、公開キー トークン、またはカルチャ (または、4 つが、すべての 4 つの任意の組み合わせ) にも含めることができます。 **それよりも**の呼び出しで指定された名前に一致する必要があります。 たとえば、指定することはできません`"math"`として、**それよりも**、構成ファイルと呼び出し属性`Assembly.Load("math, Version=3.3.3.3")`コードにします。  
  
## <a name="example"></a>例  
 次の例は、呼び出しを論理的にオンに`Assembly.Load("math")`に`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [部分アセンブリ参照](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))

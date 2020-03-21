---
title: <bindingRedirect> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154297"
---
# <a name="bindingredirect-element"></a>\<バインドリダイレクト>要素
1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<アセンブリバインディング>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<従属アセンブリ>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<バインドリダイレクト>**  
  
## <a name="syntax"></a>構文  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`oldVersion`|必須の属性です。<br /><br /> 初めに要求されていたアセンブリのバージョンを指定します。 アセンブリのバージョン番号の形式は *、メジャー.マイナー.ビルド.リビジョンです*。 このバージョン番号の各部分で有効値は、0 ～ 65535 です。<br /><br /> バージョン範囲は、次の形式でも指定できます。<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|必須の属性です。<br /><br /> 最初に要求されたバージョンの代わりに使用するアセンブリのバージョンを *、次の*形式で指定します。<br /><br /> この値では `oldVersion` より前のバージョンを指定できます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`dependentAssembly`|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。 アセンブリごとに 1 つの dependentAssembly 要素を使用します。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 厳密な名前付きアセンブリに対して .NET Framework アプリケーションを構築すると、実行時に新しいバージョンが利用できる場合でも、既定で、アプリケーションの構築時に使用したアセンブリのバージョンが使用されます。 ただし、新しいバージョンのアセンブリで実行するようにもアプリケーションを構成できます。 ランタイムがこれらのファイルを使用して使用するアセンブリ バージョンを決定する方法の詳細については、「[ランタイムがアセンブリを検索する方法](../../../deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
 複数の `bindingRedirect` 要素を `dependentAssembly` 要素に含めることによって、複数のアセンブリ バージョンをリダイレクトできます。 また、アセンブリの新しいバージョンから古いバージョンにリダイレクトすることもできます。  
  
 アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。 これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。 アクセス許可は、 にフラグ<xref:System.Security.Permissions.SecurityPermissionFlag>を設定することによって<xref:System.Security.Permissions.SecurityPermission>付与されます。 詳細については、「[アセンブリ バインディング リダイレクト セキュリティ 権限](../../assembly-binding-redirection-security-permission.md)」を参照してください。  
  
## <a name="example"></a>例  
 あるアセンブリ バージョンを別のバージョンにリダイレクトする例を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [アセンブリ バージョンのリダイレクト](../../redirect-assembly-versions.md)

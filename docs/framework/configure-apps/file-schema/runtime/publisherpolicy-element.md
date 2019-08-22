---
title: <publisherPolicy> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c8f8744d3ef1ca30eb05a4c8c3290d8a514714b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663514"
---
# <a name="publisherpolicy-element"></a>\<Publisherpolicy apply > 要素
ランタイムが発行元ポリシーを適用するかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<assemblyBinding>  
\<dependentAssembly >  
\<Publisherpolicy apply >  
  
## <a name="syntax"></a>構文  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`apply`|発行者ポリシーを適用するかどうかを指定します。|  
  
## <a name="apply-attribute"></a>属性の適用  
  
|[値]|説明|  
|-----------|-----------------|  
|`yes`|発行者ポリシーを適用します。 これは、既定の設定です。|  
|`no`|発行者ポリシーは適用されません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 コンポーネントベンダーがアセンブリの新しいバージョンをリリースする場合、ベンダーには発行者ポリシーを含めることができるため、以前のバージョンを使用するアプリケーションでは新しいバージョンが使用されるようになりました。 特定のアセンブリに対して発行者ポリシーを適用するかどうかを指定するには、  **\<publisherpolicy apply >** 要素を **\<dependentAssembly >** 要素に配置します。  
  
 **適用**属性の既定の設定は **[はい]** です。 **適用**属性を [**いいえ** **]** に設定すると、アセンブリの以前のすべての設定がオーバーライドされます。  
  
 アプリケーション構成ファイルの[ \<publisherpolicy apply apply = "no"/>](publisherpolicy-element.md)要素を使用して、アプリケーションが発行者ポリシーを明示的に無視するためのアクセス許可が必要です。 権限は、 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission>にフラグを設定することによって付与されます。 詳細については、「[アセンブリバインディングリダイレクトのセキュリティアクセス許可](../../assembly-binding-redirection-security-permission.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、アセンブリの発行者ポリシー `myAssembly`をオフにします。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [ランタイムがアセンブリを検索する方法](../../../deployment/how-the-runtime-locates-assemblies.md)
- [アセンブリ バージョンのリダイレクト](../../redirect-assembly-versions.md)

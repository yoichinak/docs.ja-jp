---
title: webRequestModules の <add> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f99c5b0dc7eab57d4e3e86f49dbbb3228c7b7d8b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664219"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<webRequestModules の > 要素の追加 (ネットワーク設定)
アプリケーションにカスタム Web 要求モジュールを追加します。  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`prefix`|この Web 要求モジュールによって処理される要求の URI プレフィックス。|  
|`type`|この Web 要求モジュールを実装するコンマで<xref:System.Type.FullName%2A>区切られた、完全修飾型名 (プロパティ<xref:System.Reflection.Assembly.FullName%2A>によって示されます) とアセンブリ名 (プロパティによって示されます)。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|ネットワークホストから情報を要求するために使用するモジュールを指定します。|  
  
## <a name="remarks"></a>Remarks  
 属性`prefix`は、指定された Web 要求モジュールを使用する URI プレフィックスを定義します。 通常、Web 要求モジュールは、HTTP や FTP などの特定のプロトコルを処理するように登録されますが、サーバー上の特定のサーバーまたはパスへの要求を処理するように登録できます。  
  
 Web 要求モジュールは、URI 照合プレフィックスが<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>メソッドに渡されたときに作成されます。  
  
 `prefix`属性の値は、有効な URI の先頭の文字である必要があります。 たとえば、 `http` や `http://www.contoso.com`になります。
  
 `type`属性の値は、有効な型名と、それに対応するアセンブリ名をコンマで区切って指定する必要があります。
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、HTTP 用のカスタム Web 要求モジュールを登録します。 Version および PublicKeyToken の値は、指定されたモジュールの正しい値に置き換える必要があります。  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.WebRequest>
- [ネットワーク設定スキーマ](index.md)

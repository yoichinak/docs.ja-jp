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
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155025"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<web 要求モジュールの>要素を追加する (ネットワーク設定)
カスタム Web 要求モジュールをアプリケーションに追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を追加する**

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
|`type`|この Web 要求モジュールを実装する<xref:System.Type.FullName%2A>完全修飾型名 (プロパティで示される)<xref:System.Reflection.Assembly.FullName%2A>とアセンブリ名 (プロパティで示される名前) をコンマで区切ります。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|ネットワーク ホストから情報を要求するために使用するモジュールを指定します。|  
  
## <a name="remarks"></a>解説  
 属性`prefix`は、指定された Web 要求モジュールを使用する URI プレフィックスを定義します。 Web 要求モジュールは、通常、HTTP や FTP などの特定のプロトコルを処理するために登録されますが、サーバー上の特定のサーバーまたはパスへの要求を処理するために登録できます。  
  
 Web 要求モジュールは、URI 一致プリフィックスがメソッドに<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>渡されるときに作成されます。  
  
 属性の`prefix`値は、有効な URI の先頭文字である必要があります。 たとえば、`http` または `http://www.contoso.com` です。
  
 属性の`type`値は、有効な型名と対応するアセンブリ名をコンマで区切って指定する必要があります。
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、HTTP 用のカスタム Web 要求モジュールを登録します。 バージョンと公開キートークンの値を、指定したモジュールの正しい値に置き換える必要があります。  
  
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

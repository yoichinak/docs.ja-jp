---
title: webRequestModules の <remove> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154726"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a>\<web 要求モジュール (ネットワーク設定) の要素>を削除します。
カスタム Web 要求モジュールをアプリケーションから削除します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を削除する**
  
## <a name="syntax"></a>構文  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`prefix`|この Web 要求モジュールによって処理される要求の URI プレフィックス。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|ネットワーク ホストから情報を要求するために使用するモジュールを指定します。|  
  
## <a name="remarks"></a>解説  
 要素`remove`は、指定された URI プレフィックスに登録されている Web 要求モジュールを削除します。  
  
 属性の`prefix`値は、有効な URI の先頭文字である必要があります。`http``http://www.contoso.com`  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  

次の例では、HTTP 用の既存の Web 要求モジュールを削除し、HTTP 要求用の新`www.contoso.com`しいカスタム Web 要求モジュールを登録します。
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
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

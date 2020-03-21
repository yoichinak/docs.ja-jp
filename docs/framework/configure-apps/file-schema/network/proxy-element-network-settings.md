---
title: <proxy> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154791"
---
# <a name="proxy-element-network-settings"></a>\<プロキシ>要素(ネットワーク設定)
プロキシ サーバーを定義します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<既定のプロキシ>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<プロキシ>**

## <a name="syntax"></a>構文  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`autoDetect`|プロキシを自動的に検出するかどうかを指定します。 既定値は `unspecified` です。|  
|`bypassonlocal`|ローカル リソースの場合に、プロキシがバイパスされるかどうかを指定します。 ローカル リソースには、ローカル`http://localhost`サーバー `http://loopback`( `http://127.0.0.1`、 、 、 、`http://webserver`) 、およびピリオド ( ) のない URI が含まれます。 既定値は `unspecified` です。|  
|`proxyaddress`|使用するプロキシ URI を指定します。|  
|`scriptLocation`|構成スクリプトの場所を指定します。 この属性には、`bypassonlocal`この属性を使用しないでください。 |  
|`usesystemdefault`|インターネット エクスプローラのプロキシ設定を使用するかどうかを指定します。 に設定すると`true`、それ以降の属性は Internet Explorer プロキシ設定より優先されます。 既定値は `unspecified` です。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="text-value"></a>テキスト値  
  
## <a name="remarks"></a>解説  
 この`proxy`要素は、アプリケーションのプロキシ サーバーを定義します。 この要素が構成ファイルに存在しない場合、.NET Framework は Internet Explorer のプロキシ設定を使用します。  
  
 属性の`proxyaddress`値は、整形式の統一リソース インジケーター (URI) である必要があります。  
  
 この`scriptLocation`属性は、プロキシ構成スクリプトの自動検出を参照します。 Internet Explorer で [自動構成スクリプトを使用する] オプションが選択されている場合、このクラスは構成スクリプト (通常は Wpad.dat という名前) を検索しようとします。 **Use automatic configuration script** <xref:System.Net.WebProxy> 任意`bypassonlocal`の値に設定されている場合`scriptLocation`は無視されます。
  
 バージョン`usesystemdefault`2.0 に移行する .NET Framework バージョン 1.1 アプリケーションの属性を使用します。  
  
 属性が無効な既定プロキシ`proxyaddress`を指定した場合は、例外がスローされます。 例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本原因に関する詳細情報が含まれています。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、Internet Explorer プロキシの既定値を使用し、プロキシ アドレスを指定し、ローカル アクセス用にプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)

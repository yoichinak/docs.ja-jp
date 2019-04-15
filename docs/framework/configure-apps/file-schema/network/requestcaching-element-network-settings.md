---
title: <requestCaching> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: af290e4b9258a08425a15e297ff538502edea916
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164854"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching > 要素 (ネットワーク設定)
ネットワーク要求のキャッシュ メカニズムを制御します。  
  
 \<configuration>  
\<system.net>  
\<requestCaching>  
  
## <a name="syntax"></a>構文  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`isPrivateCache`|キャッシュが別のユーザーの情報との間の分離を提供するかどうかを指定します。 既定値は `true` です。 この値は`false`中間層アプリケーション。|  
|`disableAllCaching`|キャッシュは、すべての Web 応答の無効になり、プログラムでオーバーライドされることはできませんを指定します。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列挙値の値の 1 つ。 既定値は `BypassCache` です。|  
|`unspecifiedMaximumAge`|その後、コンテンツを期限切れとマークが既定の時間を指定します。|  
  
## <a name="policylevel-attribute"></a>policyLevel 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`Default`|リソースに新しいもコンテンツの長さは正確では、有効期限、変更、およびコンテンツの長さの属性が存在する場合は、キャッシュされたリソースを返します。|  
|`BypassCache`|サーバーからリソースを返します。|  
|`CacheOnly`|コンテンツの長さが存在し、エントリのサイズと一致する場合は、キャッシュされたリソースを返します。|  
|`CacheIfAvailable`|コンテンツの長さが指定されたエントリのサイズと一致する場合、キャッシュされたリソースを返しますそれ以外の場合、リソースはサーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|キャッシュされたリソースのタイムスタンプが、サーバー上のリソースのタイムスタンプと同じである場合、キャッシュされたリソースを返しますそれ以外の場合、リソースは、キャッシュに格納されているサーバーからダウンロードされ、呼び出し元に返されます。|  
|`Reload`|サーバーからリソースをダウンロード、キャッシュに格納およびリソースを呼び出し元に返します。|  
|`NoCacheNoStore`|キャッシュされたリソースが存在する場合は削除されます。 リソースは、サーバーからがダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|タイムスタンプが、サーバー上のリソースのタイムスタンプと同じである場合は、リソースのキャッシュされたコピーを使用して、要求に応じます。それ以外の場合、リソースの呼び出し元に表示される、サーバーからダウンロードし、キャッシュに格納されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|省略可能な要素です。<br /><br /> HTTP キャッシュがアクティブでかどうかし、既定のキャッシュ ポリシーの記述について説明します。|  
|[\<defaultFtpCachePolicy > 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|省略可能な要素です。<br /><br /> FTP キャッシュがアクティブでかどうかし、既定のキャッシュ ポリシーを記述について説明します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="example"></a>例  
 次の例では、すべてのキャッシュを無効にする方法を示します。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

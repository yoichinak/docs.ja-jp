---
title: <ipv6> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664094"
---
# <a name="ipv6-element-network-settings"></a>\<ipv6> 要素 (ネットワーク設定)
<xref:System.Net.Dns> クラスの廃止されたメンバーからインターネット プロトコル バージョン 6 (IPv6) 応答を有効にします。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<ipv6 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`enabled`|<xref:System.Net.Dns>クラスのメンバーがインターネットプロトコルバージョン 6 (IPv6) アドレスを返すかどうかを指定します。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>Remarks  
 <xref:System.Net.Dns>この設定により、 <xref:System.Net.Dns.BeginGetHostByName%2A>クラスの廃止されたメンバー ( <xref:System.Net.Dns.GetHostByName%2A>、 <xref:System.Net.Dns.BeginResolve%2A> <xref:System.Net.Dns.EndGetHostByName%2A>、、 <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A>、、、および<xref:System.Net.Dns.Resolve%2A>) の IPv6 サポートが有効になります。 <xref:System.Net?displayProperty=nameWithType>名前空間のその他のメンバーについては、オペレーティングシステムで ipv6 が有効になっている場合、ipv6 アドレスが返されることがあります。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Net.Dns>クラスの IPv6 サポートを有効にする方法を示します。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)

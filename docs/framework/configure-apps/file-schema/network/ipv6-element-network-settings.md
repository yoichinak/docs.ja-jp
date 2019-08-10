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
ms.openlocfilehash: b8969cecf8ffb2ef23522f193bb322b1170e6111
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705065"
---
# <a name="ipv6-element-network-settings"></a>\<ipv6> 要素 (ネットワーク設定)
<xref:System.Net.Dns>クラスの廃止されたメンバーからインターネット プロトコル バージョン 6 (IPv6) 応答を有効にします。  
  
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
|`enabled`|指定するかどうかのメンバー、<xref:System.Net.Dns>クラスは、インターネット プロトコル バージョン 6 (IPv6) アドレスを返します。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>Remarks  
 この設定により、IPv6 のサポートの廃止されたメンバーの<xref:System.Net.Dns>クラス: <xref:System.Net.Dns.BeginGetHostByName%2A>、 <xref:System.Net.Dns.BeginResolve%2A>、 <xref:System.Net.Dns.EndGetHostByName%2A>、 <xref:System.Net.Dns.EndResolve%2A>、 <xref:System.Net.Dns.GetHostByAddress%2A>、 <xref:System.Net.Dns.GetHostByName%2A>、および<xref:System.Net.Dns.Resolve%2A>します。 他のメンバー、<xref:System.Net?displayProperty=nameWithType>名前空間、IPv6 アドレスが表示されるオペレーティング システムで IPv6 が有効になっている場合。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例の IPv6 サポートを有効にする方法を示しています、<xref:System.Net.Dns>クラス。  
  
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
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

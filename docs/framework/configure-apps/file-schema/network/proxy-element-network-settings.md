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
ms.openlocfilehash: 8df9bbf2615776c2e023f03401785da95b2226eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204823"
---
# <a name="proxy-element-network-settings"></a>\<proxy> 要素 (ネットワーク設定)
プロキシ サーバーを定義します。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy>  
\<proxy>  
  
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
|`autoDetect`|プロキシが自動的に検出されたかどうかを指定します。 既定値は `unspecified` です。|  
|`bypassonlocal`|ローカル リソースに対してプロキシをバイパスするかどうかを指定します。 ローカル リソースには、ローカル サーバーが含まれます (`http://localhost`、 `http://loopback`、または`http://127.0.0.1`) とピリオドが付かないの URI (`http://webserver`)。 既定値は `unspecified` です。|  
|`proxyaddress`|プロキシに使用する URI を指定します。|  
|`scriptLocation`|構成スクリプトの場所を指定します。 使用しないでください、`bypassonlocal`この属性を持つ属性です。 |  
|`usesystemdefault`|Internet Explorer のプロキシ設定を使用するかどうかを指定します。 場合設定`true`、後続する属性は、Internet Explorer のプロキシ設定を上書きします。 既定値は `unspecified` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="text-value"></a>テキスト値  
  
## <a name="remarks"></a>Remarks  
 `proxy`要素は、アプリケーションのプロキシ サーバーを定義します。 構成ファイルからこの要素が不足している場合は、.NET Framework は Internet Explorer でプロキシ設定が使用されます。  
  
 値、`proxyaddress`属性が整形式 Uniform Resource Indicator (URI) にする必要があります。  
  
 `scriptLocation`属性はプロキシ構成スクリプトの自動検出を参照します。 <xref:System.Net.WebProxy>クラスはときに、構成スクリプト (通常は名前付き Wpad.dat) を検出しようとしています、**自動構成スクリプトを使用して、** Internet Explorer でオプションを選択します。 場合`bypassonlocal`任意の値に設定されている`scriptLocation`は無視されます。
  
 使用して、`usesystemdefault`バージョン 2.0 に移行しようとする .NET Framework version 1.1 アプリケーション用の属性。  
  
 場合、例外がスローされます、`proxyaddress`属性が、無効な既定のプロキシを指定します。 例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本原因に関する詳細情報が含まれています。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、既定値を Internet Explorer のプロキシを使用して、プロキシ アドレスを指定し、ローカル アクセスでプロキシをバイパスします。  
  
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
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

---
title: <system.Net> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154557"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net> 要素 (ネットワーク設定)
.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|インターネット要求の認証に使用するモジュールを指定します。|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|インターネット ホストへの接続の最大数を指定します。|  
|[defaultProxy](defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
|[メール設定](mailsettings-element-network-settings.md)|簡易メール転送プロトコル (SMTP) メール送信オプションを構成します。|  
|[要求キャッシュ](requestcaching-element-network-settings.md)|ネットワーク要求のキャッシュ メカニズムを制御します。|  
|[設定](settings-element-network-settings.md)|関連する子名前空間のクラスの<xref:System.Net>基本的なネットワーク オプションを構成します。|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|インターネット ホストからの情報を要求するために使用するモジュールを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[構成](../configuration-element.md)|すべての名前空間の設定が含まれています。|  
  
## <a name="remarks"></a>解説  
 system.net>要素には、<xref:System.Net>および関連する子名前空間のクラスの設定が含まれます。 [ \<](system-net-element-network-settings.md) この設定では、インターネット ホストから情報を受信するための認証モジュール、接続管理、メール設定、プロキシ サーバー、およびインターネット要求モジュールを構成します。  
  
## <a name="example"></a>例  
 クラスで使用される一般的な構成の<xref:System.Net>例を次に示します。  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ネットワーク設定スキーマ](index.md)

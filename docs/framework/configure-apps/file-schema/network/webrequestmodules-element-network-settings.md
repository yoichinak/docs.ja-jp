---
title: <webRequestModules> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154544"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> 要素 (ネットワーク設定)
ネットワーク ホストから情報を要求するために使用するモジュールを指定します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<>  
  
## <a name="syntax"></a>構文  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[追加](add-element-for-webrequestmodules-network-settings.md)|カスタム Web 要求モジュールをアプリケーションに追加します。|  
|[クリア](clear-element-for-webrequestmodules-network-settings.md)|登録されているすべての Web 要求モジュールをアプリケーションから削除します。|  
|[削除](remove-element-for-webrequestmodules-network-settings.md)|カスタム Web 要求モジュールをアプリケーションから削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="remarks"></a>解説  
 要素`webRequestModules`は、ネットワーク ホストへの情報<xref:System.Net.WebRequest>要求を処理するクラスの子孫を登録します。 Web 要求モジュールは、<xref:System.Net.IWebRequestCreate>インターフェイスを実装する必要があります。  
  
 .NET Framework には`http://`、 で`https://`始まる URI の Web`file://`要求モジュールが含まれています。 デフォルトのモジュールをオーバーライドするには、構成ファイルにカスタム モジュールを登録する必要があります。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、既定の HTTP モジュールを登録します。 バージョンと公開キートークンの値を、指定したモジュールの正しい値に置き換える必要があります。  
  
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
- <xref:System.Net.IWebRequestCreate>
- [ネットワーク設定スキーマ](index.md)

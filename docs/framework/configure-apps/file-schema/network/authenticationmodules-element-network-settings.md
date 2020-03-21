---
title: <authenticationModules> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154973"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModules> 要素 (ネットワーク設定)
ネットワーク要求の認証に使用するモジュールを指定します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<認証モジュール>**

## <a name="syntax"></a>構文  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[追加](add-element-for-authenticationmodules-network-settings.md)|認証モジュールをアプリケーションに追加します。|  
|[クリア](clear-element-for-authenticationmodules-network-settings.md)|アプリケーションからすべての認証モジュールをクリアします。|  
|[削除](remove-element-for-authenticationmodules-network-settings.md)|アプリケーションから認証モジュールを削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="remarks"></a>解説  
 この`authenticationModule`要素は、サーバーとの認証プロセスを実行する認証モジュールを指定します。 認証モジュールは、インターフェイスを<xref:System.Net.IAuthenticationModule>実装する必要があります。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 認証モジュールを有効にする例を次に示します。 バージョンと公開キートークンの値を、指定したモジュールの正しい値に置き換える必要があります。  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [ネットワーク設定スキーマ](index.md)

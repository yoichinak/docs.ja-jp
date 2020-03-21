---
title: bypasslist の <add> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155078"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<バイパスリスト>要素を追加する(ネットワーク設定)
IP アドレスまたは DNS 名をプロキシ バイパス リストに追加します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<既定のプロキシ>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<バイパスリスト>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を追加する**  
  
## <a name="syntax"></a>構文  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|**アドレス**|IP アドレスまたは DNS 名を記述する正規表現。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する正規表現のセットを提供します。|  
  
## <a name="remarks"></a>解説  
 この`add`要素は、IP アドレスまたは DNS サーバー名を記述した正規表現を、プロキシ サーバーをバイパスするアドレスの一覧に挿入します。  
  
 属性の`address`値は、IP アドレスまたはホスト名のセットを記述する正規表現である必要があります。  
  
 この要素の正規表現を指定する場合は注意が必要です。 正規表現 "[a-z]+\\.contoso\\.com" は、contoso.com ドメイン内の任意のホストと一致しますが、contoso.com.cpandl.com ドメイン内の任意のホストとも一致します。 contoso.com ドメイン内のホストのみを照合するには、アンカー ("$") "[a-z]+\\.contoso\\.com$" を使用します。  
  
 正規表現の詳細については、を参照してください。[.NET フレームワークの正規表現](../../../../standard/base-types/regular-expressions.md):  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、バイパス リストに 2 つのアドレスを追加します。 最初の手順では、contoso.com ドメイン内のすべてのサーバーのプロキシをバイパスします。2 番目のサーバーは、IP アドレスが 192.168 で始まるすべてのサーバーのプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)

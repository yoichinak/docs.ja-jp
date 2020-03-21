---
title: <bypasslist> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154947"
---
# <a name="bypasslist-element-network-settings"></a>\<要素>バイパスリスト (ネットワーク設定)
プロキシを使用しないアドレスを記述する正規表現のセットを提供します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<既定のプロキシ>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<バイパスリスト>**

## <a name="syntax"></a>構文  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[追加](add-element-for-bypasslist-network-settings.md)|IP アドレスまたは DNS 名をプロキシ バイパス リストに追加します。|  
|[クリア](clear-element-for-bypasslist-network-settings.md)|バイパス リストをクリアします。|  
|[削除](remove-element-for-bypasslist-network-settings.md)|プロキシ バイパス リストから IP アドレスまたは DNS 名を削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="remarks"></a>解説  
 バイパス リストには、プロキシ サーバーを介して<xref:System.Net.WebRequest>ではなく、インスタンスが直接アクセスする URI を記述する正規表現が含まれています。  
  
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

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
ms.openlocfilehash: d3d986dae478f49504dae21b9f39574b7887b4d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674624"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> 要素 (ネットワーク設定)
一連のプロキシを使用しないアドレスを記述する正規表現を提供します。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy>  
\<bypasslist>  
  
## <a name="syntax"></a>構文  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|プロキシ バイ パスの一覧には、IP アドレスまたは DNS 名を追加します。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|バイパス リストをクリアします。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|プロキシ バイ パスの一覧から IP アドレスまたは DNS 名を削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="remarks"></a>Remarks  
 バイパス リストには、Uri を記述する正規表現が含まれています。 を<xref:System.Net.WebRequest>インスタンスがプロキシ サーバーではなく直接アクセスします。  
  
 この要素の正規表現を指定するときに注意を使用する必要があります。 正規表現"[a ~ z] +\\.contoso\\.com"contoso.com.cpandl.com ドメイン内の任意のホストと一致させる任意のホストが、contoso.com ドメインに一致します。 Contoso.com ドメイン内のホストのみが一致するアンカー (「$」) を使用します:"[a ~ z] +\\.contoso\\.com$"です。  
  
 正規表現の詳細についてを参照してください。[.NET framework の正規表現](../../../../../docs/standard/base-types/regular-expressions.md)します。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、2 つのアドレスをバイパス リストに追加します。 1 つ目は、contoso.com ドメイン内のすべてのサーバーでプロキシをバイパスします。2 つ目は、192.168 で開始の IP アドレスを持つすべてのサーバーでプロキシをバイパスします。  
  
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
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

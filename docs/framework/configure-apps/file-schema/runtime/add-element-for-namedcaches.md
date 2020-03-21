---
title: <namedCaches> の <add> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154506"
---
# <a name="add-element-for-namedcaches"></a>\<名前付きキャッシュ\<>の>要素を追加します。
メモリ`namedCache`キャッシュのコレクション`namedCaches`にエントリを追加します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>のキャッシュ**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<メモリキャッシュ>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<名前付きキャッシュ>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を追加する**  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|-|-|  
|`CacheMemoryLimitMegabytes`|インスタンスの拡張可能な最大許容サイズ (MB 単位) を指定する<xref:System.Runtime.Caching.MemoryCache>整数値。 既定値は 0 で、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ設定ヒューリスティックが既定で使用されます。|  
|`Name`|キャッシュの名前。|  
|`PhysicalMemoryLimitPercentage`|キャッシュで使用できる物理的にインストールされたコンピュータ メモリの最大パーセントを指定する 0 ~ 100 の整数値。 既定値は 0 で、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ設定ヒューリスティックが既定で使用されます。|  
|`PollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は"HH:MM:SS"形式で入力されます。|  
  
### <a name="child-elements"></a>子要素  
 `None`  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<名前付きキャッシュ>](namedcaches-element-cache-settings.md)|名前付き<xref:System.Runtime.Caching.MemoryCache>インスタンスの構成設定のコレクションを格納します。|  
  
## <a name="remarks"></a>解説  
 要素`add`は、メモリ キャッシュの`namedCaches`コレクションにエントリを追加します。 要素を使用する前に[clear](clear-element-for-namedcaches.md)要素`add`を使用して、コレクション内に他の名前付きキャッシュがないことを確認できます。 この要素は、machine.config ファイルおよび Web.config ファイルで使用できます。  
  
## <a name="example"></a>例  
 メモリ キャッシュのコレクションに既定`namedCache`のエントリの設定を定義する`namedCaches`方法を次の例に示します。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [\<名前付きキャッシュ>要素 (キャッシュ設定)](namedcaches-element-cache-settings.md)

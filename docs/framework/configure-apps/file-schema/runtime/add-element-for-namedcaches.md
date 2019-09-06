---
title: <namedCaches> の <add> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252884"
---
# <a name="add-element-for-namedcaches"></a>\<namedCaches> の \<add> 要素
メモリキャッシュ`namedCache`の`namedCaches`コレクションにエントリを追加します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache>** ](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches>** ](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>型  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|-|-|  
|`CacheMemoryLimitMegabytes`|のインスタンスを拡張<xref:System.Runtime.Caching.MemoryCache>できる最大許容サイズ (メガバイト単位) を指定する整数値。 既定値は0です。これは、 <xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが既定で使用されることを意味します。|  
|`Name`|キャッシュの名前。|  
|`PhysicalMemoryLimitPercentage`|物理的にインストールされたコンピューターメモリのうち、キャッシュで使用できる最大パーセンテージを指定する 0 ~ 100 の整数値。 既定値は0です。これは、 <xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが既定で使用されることを意味します。|  
|`PollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は、"HH: MM: SS" 形式で入力します。|  
  
### <a name="child-elements"></a>子要素  
 `None`  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|名前付き<xref:System.Runtime.Caching.MemoryCache>インスタンスの構成設定のコレクションを格納します。|  
  
## <a name="remarks"></a>Remarks  
 要素`add`は、メモリキャッシュの`namedCaches`コレクションにエントリを追加します。 `add`要素を使用する前に[clear](clear-element-for-namedcaches.md)要素を使用して、コレクション内に他の名前付きキャッシュが存在しないことを確認できます。 この要素は、machine.config ファイルと web.config ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、メモリキャッシュの`namedCache` `namedCaches`コレクションに対する既定のエントリの設定を定義する方法を示しています。  
  
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

- [\<namedCaches > 要素 (キャッシュ設定)](namedcaches-element-cache-settings.md)

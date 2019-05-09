---
title: <namedCaches> の <add> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 9a7e370f9cce0e9ddf6dbe49984b7597e041eb84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674325"
---
# <a name="add-element-for-namedcaches"></a><namedCaches> の <add> 要素
追加、`namedCache`エントリを`namedCaches`メモリ キャッシュのコレクション。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <add name="default" />  
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
|`CacheMemoryLimitMegabytes`|(メガバイト) 単位の最大サイズを指定する整数値のインスタンスを<xref:System.Runtime.Caching.MemoryCache>まで拡張できます。 既定値は 0、つまり、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが既定で使用されます。|  
|`Name`|キャッシュの名前。|  
|`PhysicalMemoryLimitPercentage`|キャッシュで使用できるコンピューターを物理的にインストールされているメモリの最大パーセンテージを指定する整数 0 ~ 100 の値。 既定値は 0、つまり、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが既定で使用されます。|  
|`PollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は"HH:MM:SS"形式で入力します。|  
  
### <a name="child-elements"></a>子要素  
 `None`  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|名前付きの構成設定のコレクションを含む<xref:System.Runtime.Caching.MemoryCache>インスタンス。|  
  
## <a name="remarks"></a>Remarks  
 `add`要素へのエントリを追加する、`namedCaches`メモリ キャッシュのコレクション。 使用することができます、[オフ](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)要素を使用する前に、`add`という名前のコレクション内のキャッシュのあるものがあることの他の要素。 この要素は、machine.config ファイルでは、Web.config ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、既定の設定を定義する方法を示します`namedCache`エントリを`namedCaches`メモリ キャッシュのコレクション。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [\<namedCaches > 要素 (キャッシュ設定)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)

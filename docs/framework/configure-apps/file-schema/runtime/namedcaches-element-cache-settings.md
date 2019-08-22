---
title: <namedCaches> 要素 (キャッシュ設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663576"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches > 要素 (キャッシュ設定)
名前付き<xref:System.Runtime.Caching.MemoryCache>インスタンスの構成設定のコレクションを指定します。 プロパティ<xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>は、構成ファイルの1つ`namedCaches`以上の要素から構成設定のコレクションを参照します。  
  
 \<configuration>  
\<> のキャッシュ  
\<memoryCache>  
\<namedCaches>  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>型  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|のインスタンスを拡張<xref:System.Runtime.Caching.MemoryCache>できる最大許容サイズを mb 単位で指定する整数値。 既定値は0です。これは、 <xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが既定で使用されることを意味します。|  
|`name`|キャッシュの名前。|  
|`physicalMemoryLimitPercentage`|物理的にインストールされたコンピューターメモリのうち、キャッシュで使用できる最大パーセンテージを指定する 0 ~ 100 の整数値。 既定値は0です。これは、 <xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが既定で使用されることを意味します。|  
|`pollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は、"HH: MM: SS" 形式で入力します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|名前付きキャッシュを、メモリ キャッシュの `namedCaches` コレクションに追加します。|  
|[\<clear>](clear-element-for-namedcaches.md)|メモリ キャッシュの `namedCaches` コレクションを消去します。|  
|[\<remove>](remove-element-for-namedcaches.md)|名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。|  
  
## <a name="remarks"></a>Remarks  
 Web.config ファイルのメモリキャッシュ構成セクションに`add`は、 `namedCaches`コレクションの、 `remove`、 `clear`の各属性を含めることができます。 各`namedCaches`エントリは、 `name`属性によって一意に識別されます。  
  
 メモリキャッシュエントリのインスタンスを取得するには、アプリケーション構成ファイル内の情報を参照します。 既定では、構成ファイルにエントリが存在するのは既定のキャッシュインスタンスだけです。 既定のキャッシュインスタンスは、 <xref:System.Runtime.Caching.MemoryCache.Default%2A>プロパティから返されるインスタンスです。  
  
 Name 属性を "default" に設定した場合、要素は既定のメモリキャッシュインスタンスを使用します。  
  
## <a name="example"></a>例  
 次の例は、 `name`属性を "default" に設定することによって、キャッシュの名前を既定のキャッシュエントリ名に設定する方法を示しています。  
  
 `cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。 これらの属性を0に設定すると、 <xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ調整ヒューリスティックが使用されます。 キャッシュの実装では、現在のメモリ負荷と、絶対値および割合に基づくメモリ制限を2分ごとに比較します。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [\<memoryCache > 要素 (キャッシュ設定)](memorycache-element-cache-settings.md)

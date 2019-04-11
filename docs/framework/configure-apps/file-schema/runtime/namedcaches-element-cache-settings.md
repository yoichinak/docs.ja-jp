---
title: <namedCaches> 要素 (キャッシュ設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 36920a5e585c0c7581fbc4f84043d68550fbdac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104937"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches > 要素 (キャッシュ設定)
名前付きの構成設定のコレクションを指定します<xref:System.Runtime.Caching.MemoryCache>インスタンス。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>プロパティから 1 つまたは複数の構成設定のコレクションの参照`namedCaches`構成ファイルの要素。  
  
 \<configuration>  
\< system.runtime.caching >  
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
|`cacheMemoryLimitMegabytes`|メガバイト単位で、最大許容サイズを指定する整数値のインスタンスを<xref:System.Runtime.Caching.MemoryCache>まで拡張できます。 既定値は 0 の自動サイズ調整ヒューリスティック。 つまり、<xref:System.Runtime.Caching.MemoryCache>クラスは、既定で使用されます。|  
|`name`|キャッシュの名前。|  
|`physicalMemoryLimitPercentage`|キャッシュで使用できるコンピューターを物理的にインストールされているメモリの最大パーセンテージを指定する整数 0 ~ 100 の値。 既定値は 0 の自動サイズ調整ヒューリスティック。 つまり、<xref:System.Runtime.Caching.MemoryCache>クラスは、既定で使用されます。|  
|`pollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は"HH:MM:SS"形式で入力します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|名前付きキャッシュを、メモリ キャッシュの `namedCaches` コレクションに追加します。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|メモリ キャッシュの `namedCaches` コレクションを消去します。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。|  
  
## <a name="remarks"></a>Remarks  
 Web.config ファイルのメモリ キャッシュ構成セクションに含めることができます`add`、 `remove`、および`clear`の属性を`namedCaches`コレクション。 各`namedCaches`でエントリを一意に識別、`name`属性。  
  
 アプリケーション構成ファイル内の情報を参照することによって、メモリ キャッシュ エントリのインスタンスを取得できます。 既定では、既定のキャッシュ インスタンスの構成ファイルにエントリがあります。 既定のキャッシュ インスタンスがインスタンスから返される、<xref:System.Runtime.Caching.MemoryCache.Default%2A>プロパティ。  
  
 名前属性を"default"を設定した場合、要素は、既定のメモリ キャッシュ インスタンスを使用します。  
  
## <a name="example"></a>例  
 次の例では、既定のキャッシュ エントリ名に設定して、キャッシュの名前を設定する方法を示しています、`name`属性を"default"です。  
  
 `cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。 これらの属性を 0 に設定することを意味の自動サイズ調整ヒューリスティック、<xref:System.Runtime.Caching.MemoryCache>クラスを使用します。 キャッシュの実装では、絶対およびパーセントのメモリ制限 2 分ごとの現在のメモリ負荷を比較します。  
  
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

- [\<memoryCache > 要素 (キャッシュ設定)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)

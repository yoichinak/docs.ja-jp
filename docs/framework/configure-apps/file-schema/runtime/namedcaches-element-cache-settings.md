---
title: <namedCaches> 要素 (キャッシュ設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153959"
---
# <a name="namedcaches-element-cache-settings"></a>\<名前付きキャッシュ>要素 (キャッシュ設定)
名前付き<xref:System.Runtime.Caching.MemoryCache>インスタンスの構成設定のコレクションを指定します。 この<xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>プロパティは、構成ファイルの 1 つ以上`namedCaches`の要素から構成設定のコレクションを参照します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>のキャッシュ**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<メモリキャッシュ>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<名前付きキャッシュ>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|インスタンスの拡張可能な最大許容サイズを<xref:System.Runtime.Caching.MemoryCache>メガバイト単位で指定する整数値。 既定値は 0 で、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ設定ヒューリスティックが既定で使用されます。|  
|`name`|キャッシュの名前。|  
|`physicalMemoryLimitPercentage`|キャッシュで使用できる物理的にインストールされたコンピュータ メモリの最大パーセントを指定する 0 ~ 100 の整数値。 既定値は 0 で、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ設定ヒューリスティックが既定で使用されます。|  
|`pollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は"HH:MM:SS"形式で入力されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>を追加する](add-element-for-namedcaches.md)|名前付きキャッシュを、メモリ キャッシュの `namedCaches` コレクションに追加します。|  
|[\<クリア>](clear-element-for-namedcaches.md)|メモリ キャッシュの `namedCaches` コレクションを消去します。|  
|[\<>を削除する](remove-element-for-namedcaches.md)|名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<構成>](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。|  
|[\<メモリキャッシュ>](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。|  
|[\<>のキャッシュ](system-runtime-caching-element-cache-settings.md)|.NET Framework に組み込まれているアプリケーションに出力キャッシュを実装するための型が含まれています。|  
  
## <a name="remarks"></a>解説  
 Web.config ファイルのメモリ キャッシュ構成セクションには、`add`コレクション`remove`の`clear`属性 、、および 属性を`namedCaches`含めることができます。 各`namedCaches`エントリは、属性によって一意`name`に識別されます。  
  
 アプリケーション構成ファイルの情報を参照することにより、メモリ キャッシュ エントリのインスタンスを取得できます。 デフォルトでは、デフォルトのキャッシュ・インスタンスのみが構成ファイルにエントリーを持っています。 既定のキャッシュ インスタンスは、プロパティから返されるインスタンス<xref:System.Runtime.Caching.MemoryCache.Default%2A>です。  
  
 name 属性を "default" に設定すると、要素は既定のメモリ キャッシュ インスタンスを使用します。  
  
## <a name="example"></a>例  
 属性を "default" に設定して、キャッシュの名前を既定のキャッシュ エントリ名`name`に設定する方法を次の例に示します。  
  
 `cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。 これらの属性をゼロに設定すると、<xref:System.Runtime.Caching.MemoryCache>クラスの自動サイズ設定ヒューリスティックが使用されます。 キャッシュの実装では、現在のメモリ負荷と 2 分ごとの絶対および割合ベースのメモリ制限を比較します。  
  
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

- [\<メモリキャッシュ>要素 (キャッシュ設定)](memorycache-element-cache-settings.md)

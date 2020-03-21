---
title: <system.runtime.caching> 要素 (キャッシュ設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153855"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<要素の>キャッシュ (キャッシュ設定)

構成ファイル内の <xref:System.Runtime.Caching.ObjectCache> エントリを使用して既定のメモリ内の `memoryCache` の実装の構成を提供します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;**\<>のキャッシュ**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性

`None`  

### <a name="child-elements"></a>子要素

|要素|説明|  
|-------------|-----------------|  
|[\<メモリキャッシュ>](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<構成>](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。|  
  
## <a name="remarks"></a>解説

この名前空間のクラスは、ASP.NET のキャッシュ機能と同様のキャッシュ機能を使用する方法を提供しますが、 `System.Web` アセンブリに依存しません。 詳細については、「 [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.Runtime.Caching>名前空間の出力キャッシュ機能と型は、.NET Framework 4 で新たに追加されました。  
  
## <a name="example"></a>例

次の例では、 <xref:System.Runtime.Caching.MemoryCache> クラスを元にしたキャッシュの構成方法を紹介します。 この例では、メモリ キャッシュ用の `namedCaches` エントリのインスタンスの構成を方法を示します。 キャッシュの名前は、属性を 「Default」に設定することで、デフォルト`name`のキャッシュ・エントリー名に設定されます。  
  
`cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。 これらの属性をゼロに設定すると、 <xref:System.Runtime.Caching.MemoryCache> の自動サイズ調整ヒューリスティックが既定で使用されることになります。 キャッシュの実装では、現在のメモリ負荷と絶対およびパーセントのメモリ制限を 2 分ごとに比較する必要があります。  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
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

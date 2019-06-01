---
title: <CompatSortNLSVersion> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6aef46db47f881d6a15cc1e58d46219a80194b0
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456446"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > 要素
文字列比較の実行時に、ランタイムがレガシ並べ替え順序を使用するように指定します。  
  
 \<configuration>  
\<runtime>  
\<CompatSortNLSVersion > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 並べ替え順序が使用されるロケール ID を指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|4096|代替の並べ替え順序を表すロケール ID。 この場合、4096 は、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] およびそれ以前のバージョンの並べ替え順序を表します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
 によって文字列比較、並べ替え、および大文字と小文字の操作が実行されるため、<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>など、.NET Framework 4 内のクラスが、Unicode 5.1 規格、文字列比較メソッドの結果に準拠<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>と<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>異なる場合があります.NET Framework の以前のバージョン。 アプリケーションがレガシ動作に依存している場合は、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 要素をアプリケーションの構成ファイルに含めることで、`<CompatSortNLSVersion>` およびそれ以前のバージョンで使用されていた文字列の比較および並べ替えの規則を復元できます。  
  
> [!IMPORTANT]
>  文字列の比較および並べ替えのレガシ規則を復元する場合は、ローカル システムで sort00001000.dll ダイナミック リンク ライブラリも使用できるようにする必要があります。  
  
 アプリケーション ドメインを作成するときに、文字列 "NetFx40_Legacy20SortingBehavior" を <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> メソッドに渡すことで、文字列の比較および並べ替えのレガシ規則を特定のアプリケーション ドメインで使用することもできます。  
  
## <a name="example"></a>例  
 次の例では、2 つの <xref:System.String> オブジェクトをインスタンス化して、<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを呼び出し、現在のカルチャの規則を使用してそれらのオブジェクトを比較する方法を示します。  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 .NET Framework 4 の例を実行すると、次の出力が表示されます。  
  
```  
sta follows a in the sort order.  
```  
  
 これは、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] で例を実行したときに表示される出力とはまったく異なります。  
  
```  
sta equals a in the sort order.  
```  
  
 ただし、例のディレクトリに次の構成ファイルを追加し、.NET Framework 4 の例を実行すると、出力実行した場合、例によって生成されるのと同じ、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]します。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)

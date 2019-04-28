---
title: <TimeSpan_LegacyFormatMode> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38adde3cd51a96f0e15ed5a0c539e088f2d3b480
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701633"
---
# <a name="timespanlegacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > 要素
ランタイムが書式設定の操作で従来の動作を保持するかどうかを判断します<xref:System.TimeSpan?displayProperty=nameWithType>値。  
  
 \<configuration>  
\<runtime>  
<TimeSpan_LegacyFormatMode>  
  
## <a name="syntax"></a>構文  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがで従来の書式設定動作を使用しているかどうかを指定します。<xref:System.TimeSpan?displayProperty=nameWithType>値。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ランタイムは、従来の書式設定動作を復元できません。|  
|`true`|ランタイムは、従来の書式設定動作を復元します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
 以降では、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 <xref:System.TimeSpan?displayProperty=nameWithType> implements 構造体、<xref:System.IFormattable>インターフェイスと書式設定を標準とカスタム書式指定文字列の操作をサポートしています。 解析方法には、サポートされていない書式指定子または書式指定文字列が検出されると、スロー、<xref:System.FormatException>します。  
  
 .NET Framework の以前のバージョンで、<xref:System.TimeSpan>構造を実装しませんでした<xref:System.IFormattable>と書式指定文字列をサポートしていませんでした。 ただし、多くの開発者誤っていることを前提<xref:System.TimeSpan>書式指定文字列のセットをサポートして、それらを使用[複合書式設定操作](../../../../../docs/standard/base-types/composite-formatting.md)などのメソッドで<xref:System.String.Format%2A?displayProperty=nameWithType>します。 通常、型を実装する場合<xref:System.IFormattable>書式指定文字列、文字列は、通常はスローをサポートされていない形式で書式指定メソッドの呼び出しをサポートしていると、<xref:System.FormatException>します。 ただし、ため<xref:System.TimeSpan>を実装しませんでした<xref:System.IFormattable>、ランタイムは、書式指定文字列を無視し、代わりに呼び出されます、<xref:System.TimeSpan.ToString?displayProperty=nameWithType>メソッド。 これは、書式指定文字列に書式設定操作に影響はありません、その存在が発生しないことを意味する<xref:System.FormatException>します。  
  
 レガシ コードに渡します複合メソッドと、無効な形式の文字列の書式を指定し、そのコードを再コンパイルできない場合は、使用することができます、`<TimeSpan_LegacyFormatMode>`要素、従来の復元を<xref:System.TimeSpan>動作します。 設定すると、`enabled`をこの要素の属性`true`複合への呼び出しでメソッドの結果を書式設定、<xref:System.TimeSpan.ToString?displayProperty=nameWithType>なく<xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>、および<xref:System.FormatException>はスローされません。  
  
## <a name="example"></a>例  
 次の例では、インスタンス化、<xref:System.TimeSpan>オブジェクトとそれをフォーマットしよう、<xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType>サポートされていない標準書式指定文字列を使用してメソッド。  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 の例を実行すると、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]か以前のバージョンで、次の出力が表示されます。  
  
```  
12:30:45  
```  
  
 一方、著しく出力例を実行する場合、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]以降のバージョン。  
  
```  
Invalid Format  
```  
  
 ただし、例を次の構成ファイルを追加する場合のディレクトリで例を実行し、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]または以降のバージョンが、出力が実行した場合に、例によって生成されるのと同じ[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]します。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)

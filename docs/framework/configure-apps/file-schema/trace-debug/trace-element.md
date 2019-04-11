---
title: <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 5faf352dce2a459a999b3cf54209f6bd9793bde0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073794"
---
# <a name="trace-element"></a>\<トレース > 要素
トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
  
## <a name="syntax"></a>構文  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`autoflush`|省略可能な属性です。<br /><br /> トレース リスナーが、すべての書き込み操作の後に、出力バッファーを自動的にフラッシュするかどうかを指定します。|  
|`indentsize`|省略可能な属性です。<br /><br /> インデントを設定する空白の数を指定します。|  
|`useGlobalLock`|省略可能な属性です。<br /><br /> グローバル ロックを使用するかどうかを示します。|  
  
## <a name="autoflush-attribute"></a>autoflush 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`false`|出力バッファーを自動的にフラッシュしません。 既定値です。|  
|`true`|自動的に出力バッファーをフラッシュします。|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`false`|リスナーがスレッド セーフである場合は、グローバル ロックを使用しませんそれ以外の場合、グローバル ロックを使用します。|  
|`true`|リスナーは、スレッド セーフであるかどうかに関係なく、グローバル ロックを使用します。 既定値です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|収集、するリスナーをストアを指定し、メッセージをルーティングします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、`<trace>`リスナーを追加する要素`MyListener`を`Listeners`コレクション。 `MyListener` という名前のファイルを作成します。`MyListener.log`し、ファイルに出力を書き込みます。 `useGlobalLock`属性に設定されて`false`、それが原因で、グローバル ロック トレース リスナーがスレッド セーフである場合に使用することはできません。 `autoflush`属性に設定されて`true`、それが原因かどうかにかかわらず、ファイルに書き込むトレース リスナー、<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>メソッドが呼び出されます。 `indentsize`属性が 0 個のスペースのインデントを設定するリスナーと、0 (ゼロ) に設定と、<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>メソッドが呼び出されます。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)

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
ms.openlocfilehash: fd90d271591a47849b3f70aea50cbe909b6fd613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920410"
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
|`autoflush`|省略可能な属性です。<br /><br /> 書き込み操作が行われるたびに、トレースリスナーが出力バッファーを自動的にフラッシュするかどうかを指定します。|  
|`indentsize`|省略可能な属性です。<br /><br /> インデントするスペースの数を指定します。|  
|`useGlobalLock`|省略可能な属性です。<br /><br /> グローバルロックを使用する必要があるかどうかを示します。|  
  
## <a name="autoflush-attribute"></a>autoflush 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|では、出力バッファーは自動的にはフラッシュされません。 既定値です。|  
|`true`|出力バッファーを自動的にフラッシュします。|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|リスナーがスレッドセーフである場合、はグローバルロックを使用しません。それ以外の場合、はグローバルロックを使用します。|  
|`true`|は、リスナーがスレッドセーフかどうかに関係なく、グローバルロックを使用します。 既定値です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## <a name="example"></a>例  
 次の例では、 `<trace>`要素を使用して、リスナー `MyListener`を`Listeners`コレクションに追加する方法を示します。 `MyListener`という名前`MyListener.log`のファイルを作成し、出力をファイルに書き込みます。 属性がに`false`設定されています。これにより、トレースリスナーがスレッドセーフである場合は、グローバルロックが使用されません。 `useGlobalLock` 属性はに`true`設定されます。これにより、メソッドが呼び出されて<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>いるかどうかに関係なく、トレースリスナーはファイルに書き込みを行います。 `autoflush` 属性が 0 (ゼロ) に設定されている場合、メソッドの<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>呼び出し時にリスナーによって0個の空白がインデントされます。 `indentsize`  
  
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
- [トレースおよびデバッグ設定のスキーマ](index.md)

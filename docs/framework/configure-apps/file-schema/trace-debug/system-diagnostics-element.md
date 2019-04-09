---
title: < System.diagnostics > 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 026805ffb9b89aa55e84cf9a5c4afb8ed63cec09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142715"
---
# <a name="systemdiagnostics-element"></a>\<system.diagnostics > 要素
メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。  
  
 \<configuration>  
\<system.diagnostics>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<assert>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。|  
|[\<performanceCounters>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。|  
|[\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|任意の source 要素または trace 要素が参照できるリスナーを含みます。 共有リスナーとして識別されたリスナーは、名前によってソースまたはトレースに追加できます。|  
|[\<ソース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|トレース メッセージを開始するトレース ソースを指定します。|  
|[\<switches>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|トレース スイッチとトレース スイッチを設定するレベルが含まれています。|  
|[\<トレース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="example"></a>例  
 次の例では、トレース スイッチおよびトレース リスナーを埋め込む方法を示しています、  **\<system.diagnostics >** 要素。 `General`トレース スイッチに設定されている、<xref:System.Diagnostics.TraceLevel>レベル。 トレース リスナー`myListener`という名前のファイルを作成します。`MyListener.log`し、ファイルに出力を書き込みます。  
  
> [!NOTE]
>  .NET Framework バージョン 2.0 では、スイッチの値を指定するためにテキストを使用できます。 たとえば、指定`true`の<xref:System.Diagnostics.BooleanSwitch>などの列挙値を表すテキストを使用または`Error`の<xref:System.Diagnostics.TraceSwitch>します。 `<add name="myTraceSwitch" value="Error" />` という行は、`<add name="myTraceSwitch" value="1" />` と同じです。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)

---
title: < diagnostics > 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: f3b4238a8d7028d47122a420526b38ee4f327332
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926945"
---
# <a name="systemdiagnostics-element"></a>\<system. diagnostics > 要素
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
|[\<assert>](assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。|  
|[\<performanceCounters>](performancecounters-element.md)|パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。|  
|[\<sharedListeners>](sharedlisteners-element.md)|任意の source 要素または trace 要素が参照できるリスナーを含みます。 共有リスナーとして識別されるリスナーは、名前を指定してソースまたはトレースに追加できます。|  
|[\<sources>](sources-element.md)|トレースメッセージを開始するトレースソースを指定します。|  
|[\<switches>](switches-element.md)|トレーススイッチと、トレーススイッチが設定されているレベルを格納します。|  
|[\<trace>](trace-element.md)|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="example"></a>例  
 次の例は、トレーススイッチとトレースリスナーを、  **\<システムの診断 >** 要素内に埋め込む方法を示しています。 トレース`General`スイッチが<xref:System.Diagnostics.TraceLevel>レベルに設定されています。 トレースリスナー `myListener`は、という`MyListener.log`ファイルを作成し、ファイルに出力を書き込みます。  
  
> [!NOTE]
> .NET Framework バージョン 2.0 では、スイッチの値を指定するためにテキストを使用できます。 たとえば、 `true` `Error`に対してを指定<xref:System.Diagnostics.TraceSwitch>したり、のような列挙値を表すテキストを使用したりできます。<xref:System.Diagnostics.BooleanSwitch> `<add name="myTraceSwitch" value="Error" />` という行は、`<add name="myTraceSwitch" value="1" />` と同じです。  
  
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
- [トレースおよびデバッグ設定のスキーマ](index.md)

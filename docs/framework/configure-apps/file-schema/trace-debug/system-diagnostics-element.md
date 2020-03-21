---
title: <システム診断>要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153208"
---
# <a name="systemdiagnostics-element"></a>\<要素>診断
メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;**\<診断>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>をアサートする](assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。|  
|[\<パフォーマンス カウンタ>](performancecounters-element.md)|パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。|  
|[\<共有リスナー>](sharedlisteners-element.md)|任意の source 要素または trace 要素が参照できるリスナーを含みます。 共有リスナーとして識別されたリスナーは、ソースまたはトレースに名前で追加できます。|  
|[\<ソース>](sources-element.md)|トレース メッセージを開始するトレース ソースを指定します。|  
|[\<スイッチ>](switches-element.md)|トレース スイッチとトレース スイッチが設定されているレベルが含まれます。|  
|[\<トレース>](trace-element.md)|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="example"></a>例  
 次の例は**\<、system.diagnostics>** 要素内にトレース スイッチとトレース リスナーを埋め込む方法を示しています。 `General`トレース スイッチはレベルに設定<xref:System.Diagnostics.TraceLevel>されます。 トレース リスナー`myListener`は、呼び`MyListener.log`出されたファイルを作成し、出力をファイルに書き込みます。  
  
> [!NOTE]
> .NET Framework バージョン 2.0 では、スイッチの値を指定するためにテキストを使用できます。 `true`たとえば、 に指定<xref:System.Diagnostics.BooleanSwitch>したり、 などの列挙値を表すテキスト`Error`を<xref:System.Diagnostics.TraceSwitch>使用したりできます。 `<add name="myTraceSwitch" value="Error" />` という行は、`<add name="myTraceSwitch" value="1" />` と同じです。  
  
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

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
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153167"
---
# <a name="trace-element"></a>\<要素>トレース
トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<トレース>**  
  
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
|`autoflush`|省略可能な属性です。<br /><br /> トレース リスナーが書き込み操作のたびに出力バッファーを自動的にフラッシュするかどうかを指定します。|  
|`indentsize`|省略可能な属性です。<br /><br /> インデントするスペースの数を指定します。|  
|`useGlobalLock`|省略可能な属性です。<br /><br /> グローバル ロックを使用するかどうかを示します。|  
  
## <a name="autoflush-attribute"></a>属性の自動フラッシュ  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|出力バッファーを自動的にフラッシュしません。 これは既定値です。|  
|`true`|出力バッファーを自動的にフラッシュします。|  
  
## <a name="usegloballock-attribute"></a>使用グローバルロック属性  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|リスナーがスレッド セーフである場合は、グローバル ロックを使用しません。それ以外の場合は、グローバル ロックを使用します。|  
|`true`|リスナーがスレッド セーフかどうかに関係なく、グローバル ロックを使用します。 これは既定値です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<リスナー>](listeners-element-for-trace.md)|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## <a name="example"></a>例  
 要素を使用してリスナー`<trace>``MyListener`をコレクションに追加する方法を次の例`Listeners`に示します。 `MyListener`という名前`MyListener.log`のファイルを作成し、そのファイルに出力を書き込みます。 この`useGlobalLock`属性は に`false`設定され、トレース リスナーがスレッド セーフである場合にグローバル ロックが使用されません。 属性`autoflush`が に`true`設定され、メソッドが呼び出されるかどうかに関係なく、トレース<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>リスナーがファイルに書き込まれます。 属性`indentsize`が 0 (ゼロ) に設定され、<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>メソッドが呼び出されるとリスナーのインデントが 0 になります。  
  
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

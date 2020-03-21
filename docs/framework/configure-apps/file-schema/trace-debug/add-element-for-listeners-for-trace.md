---
title: <add>の<listeners>要素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153673"
---
# <a name="add-element-for-listeners-for-trace"></a>\<トレース>に>\<リスナーの>要素\<を追加します。
**リスナー**をリスナー コレクションに追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<トレース>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<リスナー>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を追加する**

## <a name="syntax"></a>構文  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**型**|必須の属性です。<br /><br /> リスナーの種類を指定します。 [「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。|  
|**初期化データ**|省略可能な属性です。<br /><br /> 指定したクラスのコンストラクターに渡される文字列。|  
|**name**|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<フィルター>](filter-element-for-add-for-listeners-for-trace.md)|`Listeners`コレクション内のトレースのリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。 リスナーは、トレース出力を適切なターゲットに送ります。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="remarks"></a>解説  
 と<xref:System.Diagnostics.Debug><xref:System.Diagnostics.Trace>クラスは同じ**Listeners**コレクションを共有します。 これらのクラスの 1 つでリスナー オブジェクトをコレクションに追加すると、もう一方のクラスは同じリスナーを使用します。 リスナー クラスは から<xref:System.Diagnostics.TraceListener>派生します。  
  
 トレース リスナーの属性を`name`指定しない場合、トレース リスナー<xref:System.Diagnostics.TraceListener.Name%2A>の既定のは空の文字列 ("") になります。 アプリケーションにリスナーが 1 つしかない場合は、名前を指定せずにリスナーを追加し、名前に空の文字列を指定して削除できます。 ただし、アプリケーションに複数のリスナーがある場合は、トレース リスナーごとに一意の名前を<xref:System.Diagnostics.Debug.Listeners%2A><xref:System.Diagnostics.Trace.Listeners%2A>指定する必要があります。  
  
> [!NOTE]
> 同じタイプの複数のトレース リスナーを同じ名前で追加すると、その型と名前のトレース リスナーが 1 つだけ`Listeners`コレクションに追加されます。 ただし、プログラムによって複数の同一のリスナーをコレクション`Listeners`に追加できます。  
  
 **initializeData**属性の値は、作成するリスナーのタイプによって異なります。 すべてのトレース リスナーで**initializeData**を指定する必要があるわけではありません。  
  
> [!NOTE]
> 属性を`initializeData`使用すると、コンパイラが "'initializeData' 属性が宣言されていません。 この警告は、属性を認識しない抽象基本クラス<xref:System.Diagnostics.TraceListener>に対して構成設定が検証されるために発生`initializeData`します。 通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。  
  
 次の表は、.NET Framework に含まれるトレース リスナーと **、initializeData**属性の値を示しています。  
  
|トレース リスナー クラス|初期化データ属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|コンストラクター`useErrorStream`の<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>値。  この属性`initializeData`を "`true`" に設定して、トレース<xref:System.Console.Error%2A?displayProperty=nameWithType>出力とデバッグ出力をに書き込みます。"`false`" に<xref:System.Console.Out%2A?displayProperty=nameWithType>書き込むには、|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.EventSchemaTraceListener>名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.TextWriterTraceListener>名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.XmlWriterTraceListener>名前。|  
  
## <a name="example"></a>例  
 次の例では**\<、>** 要素を追加してリスナーと`MyListener``MyEventListener` **Listeners**コレクションに追加する方法を示します。 `MyListener`と呼ばれる`MyListener.log`ファイルを作成し、そのファイルに出力を書き込みます。 `MyEventListener`は、イベント ログにエントリを作成します。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)

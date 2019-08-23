---
title: <add> の <listeners> の <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920567"
---
# <a name="add-element-for-listeners-for-trace"></a>\<トレース > の\<リスナー \<> の > 要素を追加します
リスナーを**リスナー**コレクションに追加します。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
\<リスナー >  
\<add>  
  
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
|**type**|必須の属性です。<br /><br /> リスナーの種類を指定します。 [「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。|  
|**initializeData**|省略可能な属性です。<br /><br /> 指定したクラスのコンストラクターに渡される文字列。|  
|**name**|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|トレースの`Listeners`コレクションのリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。 リスナーは、適切なターゲットにトレース出力を送信します。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="remarks"></a>Remarks  
 クラス<xref:System.Diagnostics.Debug>と<xref:System.Diagnostics.Trace>クラスは、同じ**Listeners**コレクションを共有します。 これらのクラスのいずれかのコレクションにリスナーオブジェクトを追加すると、他のクラスは同じリスナーを使用します。 リスナークラスはから<xref:System.Diagnostics.TraceListener>派生します。  
  
 トレースリスナーの`name`属性を指定しない場合、トレースリスナーの<xref:System.Diagnostics.TraceListener.Name%2A>は既定で空の文字列 ("") になります。 アプリケーションにリスナーが1つしかない場合は、名前を指定せずにリスナーを追加し、名前に空の文字列を指定することで削除できます。 ただし、アプリケーションに複数のリスナーがある場合は、各トレースリスナーに一意の名前を指定する必要があります。これにより、コレクション<xref:System.Diagnostics.Debug.Listeners%2A>と<xref:System.Diagnostics.Trace.Listeners%2A>コレクション内の個々のトレースリスナーを識別して管理できます。  
  
> [!NOTE]
> 同じ種類の複数のトレースリスナーを同じ名前で追加すると、その型と名前のトレースリスナーは1つだけになり、 `Listeners`コレクションに追加されます。 ただし、プログラムを使用して`Listeners`複数の同じリスナーをコレクションに追加することはできます。  
  
 **Initializedata**属性の値は、作成するリスナーの種類によって異なります。 すべてのトレースリスナーで**Initializedata**を指定する必要はありません。  
  
> [!NOTE]
> `initializeData`属性を使用すると、"initializedata" 属性が宣言されていないことを示すコンパイラの警告が表示されることがあります。 この警告は、 <xref:System.Diagnostics.TraceListener> `initializeData`属性を認識しない抽象基本クラスに対して構成設定が検証されるために発生します。 通常、パラメーターを受け取るコンストラクターを持つトレースリスナーの実装では、この警告を無視できます。  
  
 次の表に、.NET Framework に含まれるトレースリスナーと、 **Initializedata**属性の値について説明します。  
  
|トレースリスナークラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|コンストラクターの値`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。  属性を "`true`" に設定し、トレース出力とデバッグ出力<xref:System.Console.Error%2A?displayProperty=nameWithType>をに設定します。 `initializeData`書き込み先となる "`false`"。 <xref:System.Console.Out%2A?displayProperty=nameWithType>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|が<xref:System.Diagnostics.DelimitedListTraceListener>書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベントログソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|が<xref:System.Diagnostics.EventSchemaTraceListener>書き込み先となるファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|が<xref:System.Diagnostics.TextWriterTraceListener>書き込み先となるファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|が<xref:System.Diagnostics.XmlWriterTraceListener>書き込み先となるファイルの名前。|  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します **\<追加 >** リスナーを追加する要素`MyListener`と`MyEventListener`を**リスナー**コレクション。 `MyListener`という名前`MyListener.log`のファイルを作成し、その出力をファイルに書き込みます。 `MyEventListener`イベントログにエントリを作成します。  
  
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

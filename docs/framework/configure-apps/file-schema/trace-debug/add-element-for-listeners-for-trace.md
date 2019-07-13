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
ms.openlocfilehash: ba0ffc4f95b9af7fcd319068501ce0bb9714c2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673974"
---
# <a name="add-element-for-listeners-for-trace"></a>\<追加 > 要素の\<リスナー > の\<トレース >
リスナーを追加、**リスナー**コレクション。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
\<listeners>  
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
|**type**|必須の属性です。<br /><br /> リスナーの種類を指定します。 指定された条件に一致する文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)します。|  
|**initializeData**|省略可能な属性です。<br /><br /> 指定したクラスのコンス トラクターに渡された文字列。|  
|**name**|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|内のリスナーにフィルターを追加、`Listeners`トレースのコレクション。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|収集、するリスナーをストアを指定し、メッセージをルーティングします。 リスナーでは、適切なターゲットのトレースを出力します。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="remarks"></a>Remarks  
 <xref:System.Diagnostics.Debug>と<xref:System.Diagnostics.Trace>クラスが同じ共有**リスナー**コレクション。 これらのクラスのいずれかで、コレクションにリスナー オブジェクトを追加する場合、その他のクラスは、同一のリスナーを使用します。 リスナー クラスから派生、<xref:System.Diagnostics.TraceListener>します。  
  
 指定しない場合、 `name` 、トレース リスナーの属性、<xref:System.Diagnostics.TraceListener.Name%2A>トレース リスナーの既定値を空の文字列 ("")。 アプリケーションに 1 つだけのリスナーは、名を指定せずに追加し、名前の空の文字列を指定して、削除します。 ただし、アプリケーションには、複数のリスナーがある場合は、識別し、内の個別のトレース リスナーを管理することができますトレース リスナーごとに一意の名前を指定する必要があります、<xref:System.Diagnostics.Debug.Listeners%2A>と<xref:System.Diagnostics.Trace.Listeners%2A>コレクション。  
  
> [!NOTE]
>  同じ種類のと同じでは、複数のトレース リスナーを追加する結果を型の 1 つだけのトレース リスナーにという名前に追加される、`Listeners`コレクション。 、に複数の同一のリスナーがプログラムで追加することができます、`Listeners`コレクション。  
  
 値、 **initializeData**属性を作成するリスナーの種類によって異なります。 指定する必要はないすべてのトレース リスナー **initializeData**します。  
  
> [!NOTE]
>  使用すると、`initializeData`属性、コンパイラの警告「、'initializeData' 属性は宣言されていません」. を取得する可能性があります この警告は、構成設定は、抽象基本クラスに対しても検証するために発生します。 <xref:System.Diagnostics.TraceListener>、これを認識しません、`initializeData`属性。 通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視できます。  
  
 次の表は、.NET Framework に含まれているトレース リスナーの表示し、の値を記述、 **initializeData**属性。  
  
|トレース リスナー クラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`値、<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクター。  設定、`initializeData`属性を"`true`"トレースとデバッグを書き込む出力を<xref:System.Console.Error%2A?displayProperty=nameWithType>;"`false`"に書き込めません<xref:System.Console.Out%2A?displayProperty=nameWithType>します。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>に書き込みます。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前の名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>に書き込みます。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>に書き込みます。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>に書き込みます。|  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します **\<追加 >** リスナーを追加する要素`MyListener`と`MyEventListener`を**リスナー**コレクション。 `MyListener` という名前のファイルを作成します。`MyListener.log`し、ファイルに出力を書き込みます。 `MyEventListener` イベント ログにエントリを作成します。  
  
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
- [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [トレース リスナー](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)

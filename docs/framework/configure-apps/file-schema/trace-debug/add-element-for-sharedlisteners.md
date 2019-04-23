---
title: <sharedListeners> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: e7934ed5e71005cfd28271298ff6ce1eb8829a0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095634"
---
# <a name="add-element-for-sharedlisteners"></a>\<追加 > 要素の\<上 sharedListeners >
`sharedListeners` コレクションにリスナーを追加します。 `sharedListeners` リスナーのコレクションは、 [\<ソース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)または[\<トレース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)を参照できます。  既定でリスナーに、`sharedListeners`でコレクションが配置されていない、`Listeners`コレクション。 名前で追加する必要があります、 [\<ソース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)または[\<トレース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)します。 リスナーを取得することはできません、`sharedListeners`実行時にコード内のコレクション。  
  
 \<configuration>  
&nbsp;&nbsp;\<system.diagnostics>  
&nbsp;&nbsp;&nbsp;&nbsp;\<上の sharedListeners > 要素  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<追加 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須の属性です。<br /><br /> 共有リスナーを追加するために使用するリスナーの名前を指定します、`Listeners`コレクション。|  
|`type`|必須の属性です。<br /><br /> リスナーの種類を指定します。 指定された条件に一致する文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)します。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したクラスのコンス トラクターに渡された文字列。|  
|`traceOutputOptions`|省略可能な属性です。<br/><br/>1 つ以上の文字列表現<xref:System.Diagnostics.TraceOptions>トレース出力に書き込まれるデータを示す列挙型メンバー。 複数の項目は、コンマで区切られます。 既定値は、"None"です。|

### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` コレクションのリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意のソースまたは trace 要素を参照できるリスナーのコレクション。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework に付属するリスナー クラスから派生、<xref:System.Diagnostics.TraceListener>クラス。 値、`name`属性を使用する共有リスナーを追加して、`Listeners`トレースまたはトレース ソースのいずれかのコレクション。 値、`initializeData`属性を作成するリスナーの種類によって異なります。 指定する必要はないすべてのトレース リスナー`initializeData`します。  
  
> [!NOTE]
>  使用すると、`initializeData`属性、コンパイラの警告「、'initializeData' 属性は宣言されていません」. を取得する可能性があります この警告は、構成設定は、抽象基本クラスに対しても検証するために発生します。 <xref:System.Diagnostics.TraceListener>、これを認識しません、`initializeData`属性。 通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視できます。  
  
 次の表は、.NET Framework に含まれているトレース リスナーの表示し、の値を記述、`initializeData`属性。  
  
|トレース リスナー クラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream`値、<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクター。  設定、`initializeData`属性を"`true`「書き込むトレースとデバッグの出力を標準エラー ストリームに設定」`false`"標準出力ストリームに書き込む。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>に書き込みます。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>に書き込みます。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>に書き込みます。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>に書き込みます。|  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します`<add>`要素を追加する、 <xref:System.Diagnostics.TextWriterTraceListener> `textListener`を`sharedListeners`コレクション。   `textListener` 名前で追加、`Listeners`トレース ソースのコレクション`TraceSourceApp`します。 `textListener`ファイル myListener.log にリスナーがトレース出力を書き込みます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [トレース リスナー](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)

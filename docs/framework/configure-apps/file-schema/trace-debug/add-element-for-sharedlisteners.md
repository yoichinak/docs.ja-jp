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
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927215"
---
# <a name="add-element-for-sharedlisteners"></a>\<sharedListeners > の > \<要素の追加
`sharedListeners` コレクションにリスナーを追加します。 `sharedListeners`[任意\<のソース >](source-element.md)または[ \<トレース >](trace-element.md)が参照できるリスナーのコレクションです。  既定では、 `sharedListeners`コレクション内のリスナーは`Listeners`コレクション内に配置されません。 これらのファイルは、 [ \<ソース >](source-element.md)または[ \<トレース >](trace-element.md)に名前で追加する必要があります。 実行時にコードで`sharedListeners`コレクション内のリスナーを取得することはできません。  
  
 \<configuration>  
&nbsp;&nbsp;\<システム診断 >  
&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > 要素  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<> の追加  
  
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
|`name`|必須の属性です。<br /><br /> 共有リスナーを`Listeners`コレクションに追加するために使用されるリスナーの名前を指定します。|  
|`type`|必須の属性です。<br /><br /> リスナーの種類を指定します。 [「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したクラスのコンストラクターに渡される文字列。|  
|`traceOutputOptions`|省略可能な属性です。<br/><br/>トレース出力に書き込まれるデータ<xref:System.Diagnostics.TraceOptions>を示す1つ以上の列挙メンバーの文字列形式。 複数の項目は、コンマで区切られます。 既定値は "None" です。|

### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` コレクションのリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意のソースまたはトレース要素が参照できるリスナーのコレクション。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework に付属しているリスナークラスは、 <xref:System.Diagnostics.TraceListener>クラスから派生します。 `name`属性の値は、トレースまたはトレースソースの`Listeners`コレクションに共有リスナーを追加するために使用されます。 `initializeData`属性の値は、作成するリスナーの種類によって異なります。 すべてのトレースリスナーでを指定`initializeData`する必要はありません。  
  
> [!NOTE]
> `initializeData`属性を使用すると、"initializedata" 属性が宣言されていないことを示すコンパイラの警告が表示されることがあります。 この警告は、 <xref:System.Diagnostics.TraceListener> `initializeData`属性を認識しない抽象基本クラスに対して構成設定が検証されるために発生します。 通常、パラメーターを受け取るコンストラクターを持つトレースリスナーの実装では、この警告を無視できます。  
  
 次の表に、.NET Framework に含まれているトレースリスナーとその`initializeData`属性の値を示します。  
  
|トレースリスナークラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|コンストラクターの値`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。  トレース出力`initializeData`およびデバッグ出力`true`を標準エラーストリームに書き込むには、属性を "" に設定します`false`。標準出力ストリームに書き込むには、"" に設定します。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|が<xref:System.Diagnostics.DelimitedListTraceListener>書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベントログソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|が<xref:System.Diagnostics.EventSchemaTraceListener>書き込み先となるファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|が<xref:System.Diagnostics.TextWriterTraceListener>書き込み先となるファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|が<xref:System.Diagnostics.XmlWriterTraceListener>書き込み先となるファイルの名前。|  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、要素を`<add>`使用して<xref:System.Diagnostics.TextWriterTraceListener> `textListener`を`sharedListeners`コレクションに追加する方法を示しています。   `textListener`は、トレースソース`Listeners` `TraceSourceApp`のコレクションに名前によって追加されます。 リスナー `textListener`は、トレース出力をファイル mylistener .log に書き込みます。  
  
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
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)

---
title: <add>の<listeners>要素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153686"
---
# <a name="add-element-for-listeners-for-source"></a>\<\<ソース>の\<リスナー>の要素>追加
トレース ソースの `Listeners` コレクションにリスナーを追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<ソース>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ソース>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<リスナー>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を追加する**

## <a name="syntax"></a>構文  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|コレクション内`sharedListeners`のリスナーを参照する場合を除き、必須属性は名前で参照するだけで済みます ([例](#example)を参照)。<br /><br /> リスナーの種類を指定します。 [「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したクラスのコンストラクターに渡される文字列。 クラス<xref:System.Configuration.ConfigurationException>に文字列を受け取るコンストラクタがない場合は、A がスローされます。|  
|`name`|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
|`traceOutputOptions`|省略可能な属性です。<br /><br /> トレース<xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>リスナーのプロパティ値を指定します。|  
|[カスタム属性]|省略可能な属性。<br /><br /> そのリスナーのメソッドによって識別されるリスナー固有の<xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A>属性の値を指定します。 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>は、クラスに固有の追加属性の例<xref:System.Diagnostics.DelimitedListTraceListener>です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<フィルター>](filter-element-for-add-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
## <a name="remarks"></a>解説  
 .NET Framework に付属のリスナー クラスは、<xref:System.Diagnostics.TraceListener>クラスから派生します。  
  
 トレース リスナーの属性を`name`指定しない場合、トレース リスナー<xref:System.Diagnostics.TraceListener.Name%2A>のプロパティは既定で空の文字列 ("") になります。 アプリケーションにリスナーが 1 つしかない場合は、名前を指定せずにリスナーを追加できます。 ただし、アプリケーションに複数のリスナーがある場合は、トレース リスナーごとに一意の名前を<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>指定する必要があります。  
  
> [!NOTE]
> 同じタイプの複数のトレース リスナーを同じ名前で追加すると、その型と名前のトレース リスナーが 1 つだけ`Listeners`コレクションに追加されます。 ただし、プログラムによって複数の同一のリスナーをコレクション`Listeners`に追加できます。  
  
 属性の値は`initializeData`、作成するリスナーのタイプによって異なります。 すべてのトレース リスナーで を指定`initializeData`する必要があるわけではありません。  
  
> [!NOTE]
> 属性を`initializeData`使用すると、コンパイラが "'initializeData' 属性が宣言されていません。 この警告は、属性を認識しない抽象基本クラス<xref:System.Diagnostics.TraceListener>に対して構成設定が検証されるために発生`initializeData`します。 通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。  
  
 次の表は、.NET Framework に含まれるトレース リスナーとその属性の値を`initializeData`示しています。  
  
|トレース リスナー クラス|初期化データ属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|コンストラクター`useErrorStream`の<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>値。  この属性`initializeData`を "`true`" に設定すると、トレース出力とデバッグ出力が標準のエラー ストリームに書き込まれます。標準出力ストリームに`false`書き込むには、"" に設定します。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.EventSchemaTraceListener>名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.TextWriterTraceListener>名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.XmlWriterTraceListener>名前。|  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、要素を`<add>`使用して、トレース ソース`console``TraceSourceApp`の`textListener`リスナーと`Listeners`コレクションを追加する方法を示しています。 リスナー`textListener`は、myListener.log ファイルにトレース出力を書き込みます。  
  
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

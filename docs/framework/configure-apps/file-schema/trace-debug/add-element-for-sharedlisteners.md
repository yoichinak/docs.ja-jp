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
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153608"
---
# <a name="add-element-for-sharedlisteners"></a>\<共有リスナー>>\<要素を追加します
`sharedListeners` コレクションにリスナーを追加します。 `sharedListeners`は、[\<ソース>](source-element.md)または[\<トレース>](trace-element.md)が参照できるリスナーのコレクションです。  既定では、コレクション内の`sharedListeners`リスナーはコレクションに`Listeners`配置されません。 ソース[\<>](source-element.md)または[\<トレース>](trace-element.md)に名前で追加する必要があります。 実行時に、コレクション内のリスナーを`sharedListeners`コードで取得することはできません。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<共有リスナー>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>を追加する**

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
|`name`|必須の属性です。<br /><br /> 共有リスナーをコレクションに追加するために使用されるリスナーの名前を`Listeners`指定します。|  
|`type`|必須の属性です。<br /><br /> リスナーの種類を指定します。 [「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したクラスのコンストラクターに渡される文字列。|  
|`traceOutputOptions`|省略可能な属性です。<br/><br/>トレース出力に書き込む<xref:System.Diagnostics.TraceOptions>データを示す 1 つ以上の列挙型メンバーの文字列表現。 複数の項目はコンマで区切られます。 デフォルト値は「なし」です。|

### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<フィルター>](filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` コレクションのリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意のソースまたはトレース要素が参照できるリスナーのコレクション。|  
  
## <a name="remarks"></a>解説  
 .NET Framework に付属のリスナー クラスは、<xref:System.Diagnostics.TraceListener>クラスから派生します。 この属性の`name`値は、共有リスナーをトレースまたはトレース・ソース`Listeners`のコレクションに追加するために使用されます。 属性の値は`initializeData`、作成するリスナーのタイプによって異なります。 すべてのトレース リスナーで を指定`initializeData`する必要があるわけではありません。  
  
> [!NOTE]
> 属性を`initializeData`使用すると、コンパイラが "'initializeData' 属性が宣言されていません。 この警告は、属性を認識しない抽象基本クラス<xref:System.Diagnostics.TraceListener>に対して構成設定が検証されるために発生`initializeData`します。 通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。  
  
 次の表は、.NET Framework に含まれるトレース リスナーとその属性の値を`initializeData`示しています。  
  
|トレース リスナー クラス|初期化データ属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|コンストラクター`useErrorStream`の<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>値。  この属性`initializeData`を "`true`" に設定すると、トレース出力とデバッグ出力が標準のエラー ストリームに書き込まれます。標準出力ストリームに`false`書き込むには、"" に設定します。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.EventSchemaTraceListener>名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|書き込みするファイルの<xref:System.Diagnostics.TextWriterTraceListener>名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|書き込みするファイルの<xref:System.Diagnostics.XmlWriterTraceListener>名前。|  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 要素`<add>`を使用して コレクションに追加する方法を<xref:System.Diagnostics.TextWriterTraceListener>`textListener`次の`sharedListeners`例に示します。   `textListener`は、トレース ソースの`Listeners`コレクションに名前で追加`TraceSourceApp`されます。 リスナー`textListener`は、myListener.log ファイルにトレース出力を書き込みます。  
  
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

---
ms.openlocfilehash: 0642b184d85306a453d429f247dad95a259cb012
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236511"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer による制御文字のシリアル化が ECMAScript V6 および V8 対応に

|   |   |
|---|---|
|説明|.NET framework 4.6.2 以前のバージョンでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> で、ECMAScript V6 および V8 標準と互換性がある方法で \b、\f、\t などの一部の特殊制御文字がシリアル化されませんでした。 .NET Framework 4.7 以降、これらの制御文字のシリアル化は ECMAScript V6 および V8 と互換性があります。|
|提案される解決策|.NET Framework 4.7 を対象とするアプリの場合、この機能は既定で有効になっています。 この動作が望ましくない場合は、app.config または web.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加して、この機能を無効にすることができます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

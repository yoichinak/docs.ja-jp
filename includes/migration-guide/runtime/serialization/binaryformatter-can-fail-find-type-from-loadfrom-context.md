---
ms.openlocfilehash: ac929a8b3e9a7d56122f5699c51819ad483d1f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804416"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter による LoadFrom コンテキストからの型の検索が失敗する場合がある

|   |   |
|---|---|
|説明|.NET Framework 4.5 の時点で、<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> の複数の変更により、LoadFrom コンテキストに読み込まれた型の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> を使った逆シリアル化に違いが発生する場合があります。 これらの変更は <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> が型を読み込む新しい方法によるものであり、後で <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> がその型に逆シリアル化しようとするときに異なる動作が発生します。 既定のシリアル化バインダーは LoadFrom コンテキストを自動的に検索しませんが、状況によっては XmlSerializer の以前の動作に基づいて機能する可能性があります。 変更のため、異なるコンテキストで読み込まれたアセンブリから型が読み込まれるときに、<xref:System.IO.FileNotFoundException?displayProperty=name> がスローされる可能性があります。|
|提案される解決策|この例外が発生する場合は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> の <code>Binder</code> プロパティを、正しい型を検索するカスタム バインダーに設定することができます。<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>そして、カスタム バインダーで次のようにします。<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

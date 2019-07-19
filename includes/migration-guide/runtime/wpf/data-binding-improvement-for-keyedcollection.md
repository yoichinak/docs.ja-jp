---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802573"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection のデータ バインディングの機能強化

|   |   |
|---|---|
|説明|ソース オブジェクトが同じシグネチャを持つカスタム インデクサーを宣言するときの<xref:System.Windows.Data.Binding>による IList インデクサーの不適切な使用を修正しました (例: KeyedCollection&lt;int,TItem&gt;)。|
|提案される解決策|アプリケーションがこの変更の恩恵を受けるには、.NET Framework 4.7.2 以降上で実行する必要があります。また、次の [AppContext スイッチ](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)をアプリ構成ファイルの <code>&lt;runtime&gt;</code> セクションに追加し、それを <code>false</code> に設定することで、変更を選択する必要があります。<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|Major|
|Version|4.8|
|型|ランタイム|


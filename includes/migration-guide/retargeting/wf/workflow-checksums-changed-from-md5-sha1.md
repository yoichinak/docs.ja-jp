---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236485"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>ワークフローのチェックサムが MD5 から SHA1 に変更

|   |   |
|---|---|
|説明|Visual Studio によるデバッグをサポートするために、ワークフロー ランタイムによって、ハッシュ アルゴリズムを使用してワークフロー インスタンスのチェックサムが生成されます。 .NET Framework 4.6.2 以前のバージョンでは、ワークフロー チェックサムのハッシュで MD5 アルゴリズムが使用され、FIPS 対応システムで問題が発生していました。 .NET Framework 4.7 以降、アルゴリズムは SHA1 になります。 コードによってチェックサムが永続化されている場合、互換性がありません。|
|提案される解決策|チェックサム エラーに起因してコードでワークフロー インスタンスを読み込めない場合、<code>AppContext</code> スイッチ &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; を true に設定してみてください。下のコードをご覧ください。<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>または、次のように構成します。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7|
|型|再ターゲット中|

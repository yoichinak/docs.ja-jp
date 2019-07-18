---
ms.openlocfilehash: 47aa67096f8dcd250521d9c34dde97cb2eb368d7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803494"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>ワークフロー XOML 定義および SqlTrackingService キャッシュ キーの MD5 から SHA256 への変更

|   |   |
|---|---|
|説明|ワークフロー ランタイムでは、XOML で定義されているワークフロー定義のキャッシュが保持されます。 また、SqlTrackingService では、文字列によってキー指定されるキャッシュが保持されます。 これらのキャッシュは、チェックサム ハッシュ値を含む値によってキー指定されます。 .NET Framework 4.7.2 以前のバージョンでは、このチェックサムのハッシュで MD5 アルゴリズムが使用され、FIPS 対応システムで問題が発生していました。 .NET Framework 4.8 以降で使用されるアルゴリズムは SHA256 です。ワークフロー ランタイムと SqlTrackingService が開始されるたびに値が再計算されるため、この変更に関する互換性の問題は発生しないはずです。 しかし、後方互換が提供されるため、お客様は必要に応じて、従来のハッシュ アルゴリズムの使用に戻すことができます。|
|提案される解決策|この変更により、ワークフローの実行時に問題が生じる場合は、次のように、<code>AppContext</code> スイッチのいずれか、または両方を設定してみてください。<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; を true にする。</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; を true にする。</li></ul>コードは次のとおりです。<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>または、構成ファイルで次のようにします (<xref:System.Workflow.Runtime.WorkflowRuntime> オブジェクトを作成しているアプリケーションの構成ファイルで、このようにする必要があります)。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.8|
|型|再ターゲット中|


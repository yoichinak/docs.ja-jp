---
ms.openlocfilehash: 384f8c7fa08b69c13d05edb3404787d428dad837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774075"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>ポータブル PDB の使用時に取得されるスタック トレースに、必要に応じてソース ファイルと行情報が含まれるようになった

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以降では、ポータブル PDB の使用時に取得されるスタック トレースに、要求に応じてソース ファイルと行情報が含まれます。 .NET Framework 4.7.2 より前のバージョンでは、明示的に要求された場合でもポータブル PDB の使用時にソース ファイルと行情報は利用できません。|
|提案される解決策|.NET Framework 4.7.2 を対象とするアプリケーションでは、望ましくない場合、<code>app.config</code> ファイルの <code>&lt;runtime&gt;</code> セクションに以下を追加することで、ポータブル PDB の使用時にソース ファイルと行情報の選択を解除できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以前のバージョンの .NET Framework を対象とするが、.NET Framework 4.7.2 以降で実行するアプリケーションの場合は、<code>app.config</code> ファイルの <code>&lt;runtime&gt;</code> セクションに以下を追加することで、ポータブル PDB の使用時にソース ファイルと行情報を選択できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

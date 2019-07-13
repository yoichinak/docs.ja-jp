---
ms.openlocfilehash: c44971dfd65ee31657279daec2d34b8cfa8d4860
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410402"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>ワークフロー XOML ファイルのチェックサムが MD5 から SHA256 に変更

|   |   |
|---|---|
|説明|Visual Studio を使用した XOML ベースのワークフローのデバッグをサポートするため、XOML ファイルが含まれているワークフロー プロジェクトをビルドするときに、XOML ファイルのコンテンツのチェックサムが <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> 値として生成されたコードに含まれます。 .NET Framework 4.7.2 以前のバージョンでは、このチェックサムのハッシュで MD5 アルゴリズムが使用され、FIPS 対応システムで問題が発生していました。 .NET Framework 4.8 以降、使用されるアルゴリズムは SHA256 になります。 WorkflowMarkupSourceAttribute.MD5Digest との互換性を確保するため、生成されたチェックサムの最初の 16 バイトのみが使用されます。これにより、デバッグ中に問題が発生する可能性があります。 プロジェクトの再ビルドが必要になる場合があります。|
|提案される解決策|プロジェクトを再ビルドしても問題が解決しない場合は、<code>AppContext</code> スイッチ &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; を true に設定してみてください。コードでは次のようになります。<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>構成ファイルでは次のようになります (使用している MSBuild.exe の MSBuild.exe.config で行う必要があります)。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.8|
|型|再ターゲット中|

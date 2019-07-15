---
ms.openlocfilehash: f672645fb98f511f7e1326c9c584b287a0fae7dc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859366"
---
### <a name="long-path-support"></a>長いパスのサポート

|   |   |
|---|---|
|説明|以降とするアプリをターゲットとする .NET Framework 4.6.2、長いパス (最大 32 K の文字) がサポートされている、および 260 文字 (または<code>MAX_PATH</code>) パスの長さの制限がなくなりました。 .NET Framework 4.6.2 を対象として再コンパイルされたアプリの場合は、コードをスローした以前のパス、 <xref:System.IO.PathTooLongException?displayProperty=name> 260 文字をスローがパスを超えたため、<xref:System.IO.PathTooLongException?displayProperty=name>次の条件下でのみ。<ul><li>パスの長さが <xref:System.Int16.MaxValue> (32,767) 文字を超えている。</li><li>オペレーティング システムが <code>COR_E_PATHTOOLONG</code> またはそれと同等のものを返す。</li></ul>.NET Framework 4.6.1 以前を対象とするアプリの場合、パスが 260 文字を超えるたびにランタイムで自動的に <xref:System.IO.PathTooLongException?displayProperty=name> がスローされます。|
|提案される解決策|.NET Framework 4.6.2 を対象とするアプリケーションの場合、長いパスが望ましくないときは、<code>app.config</code> ファイルの <code>&lt;runtime&gt;</code> セクションに次を追加することで長いパスのサポートを無効にできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以前のバージョンの .NET Framework を対象とするが、.NET Framework 4.6.2 以降で実行するアプリの場合、<code>app.config</code> ファイルの <code>&lt;runtime&gt;</code> セクションに次を追加することで長いパスのサポートを選択できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.6.2|
|型|再ターゲット中|


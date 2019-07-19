---
ms.openlocfilehash: a786ce0908552547f996d0c299db2a9e9e14a757
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804384"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>ZipArchiveEntry オブジェクトの FullName プロパティのパス区切り文字の変更

|   |   |
|---|---|
|説明|.NET Framework 4.6.1 以降のバージョンを対象とするアプリの場合、<xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> メソッドのオーバーロードによって作成された <xref:System.IO.Compression.ZipArchiveEntry> オブジェクトの <xref:System.IO.Compression.ZipArchiveEntry.FullName> プロパティで、パスの区切り文字が円記号 (&quot;\&quot;) からスラッシュ (&quot;/&quot;) に変更されました。 この変更によって、.NET の実装が [.ZIP ファイル形式の仕様](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)のセクション 4.4.17.1 に準拠するようになったほか、Windows 以外のシステムで ZIP アーカイブを圧縮解除できるようになりました。<br />Macintosh などの Windows 以外のオペレーティング システムで以前のバージョンの .NET Framework を対象とするアプリで作成された zip ファイルを圧縮解除すると、ディレクトリ構造を保持できません。 たとえば、Macintosh で、ディレクトリ パスとファイル名が円記号 (&quot;&quot;) 文字で連結された名前を持つ一連のファイルを作成するとします。 その場合、圧縮解除されたファイルのディレクトリ構造は保持されません。|
|提案される解決策|.NET Framework <xref:System.IO?displayProperty=nameWithType> 名前空間の API によって、Windows オペレーティング システムで展開される .zip ファイルでは、この変更の影響は最小限になるはずです。これらの API では、スラッシュ (&quot;/&quot;) または円記号 (&quot;\&quot;) をパスの区切り文字としてシームレスに処理できるためです。<br />この変更が望ましくない場合、アプリケーション構成ファイルの [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、無効にすることができます。 次の例では、<code>&lt;runtime&gt;</code> セクションと無効に切り替える処理 <code>Switch.System.IO.Compression.ZipFile.UseBackslash</code> の両方を確認できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>また、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.6.1 以降のバージョンで実行されているアプリでは、アプリケーション構成ファイルの [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。 次では、<code>&lt;runtime&gt;</code> セクションと有効に切り替える処理 <code>Switch.System.IO.Compression.ZipFile.UseBackslash</code> の両方を確認できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.6.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType></li></ul>|


---
ms.openlocfilehash: ed0dde302e30ae0cf3c7a8d0985f2314d91cab66
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760902"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream で圧縮解除のためにネイティブ API が使用される

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以降では、<code>T:System.IO.Compression.DeflateStream</code> クラスの圧縮解除の実装の際に、既定でネイティブの Windows API を使用するように変更されました。 通常は、これによりパフォーマンスが大幅に改善されます。 .NET Framework バージョン 4.7.2 以降を対象とするすべての .NET アプリケーションでは、ネイティブ実装が使用されます。この変更により、次のように動作にいくつか違いが生じる場合があります。<ul><li>例外メッセージが異なる場合があります。 ただし、スローされる例外の種類は変わりません。</li><li>操作を完了するのに十分なメモリがないなど、いくつかの特殊な状況が異なる方法で処理される場合があります。</li><li>gzip ヘッダーの解析には、次のような違いが確認されています (注: 圧縮解除のために設定されている <code>GZipStream</code> のみが影響します)。</li><li>無効なヘッダーの解析時の例外がさまざまなタイミングでスローされる場合があります。</li><li>ネイティブ実装では、gzip ヘッダー内で予約されているいくつかのフラグの値 (つまり、[FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) が、仕様に基づいて設定されるように強制されます。これにより、以前は無効な値が無視されていた例外がスローされる可能性があります。</li></ul>|
|提案される解決策|ネイティブ API での圧縮解除がアプリの動作に悪影響を与えている場合は、app.config ファイルの <code>runtime</code> セクションに <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> スイッチを追加して <code>true</code> に設定することで、この機能の選択を解除できます。<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|


---
ms.openlocfilehash: 14b8930044381d1d86ec7984d36a5c3588eebd81
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233998"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>WPF のマークアップ コンパイラの既定のハッシュ アルゴリズムが SHA256 になった

|   |   |
|---|---|
|説明|WPF マークアップ コンパイラでは、XAML マークアップ ファイルのコンパイル サービスが提供されます。  .NET Framework 4.7.1 以前のバージョンでは、チェックサムで使用される既定のハッシュ アルゴリズムは SHA1 でした。 最近明らかになった SHA1 のセキュリティに関する懸念事項により、.NET Framework 4.7.2 以降では、この既定値は SHA256 に変更されています。  この変更は、コンパイル中のマークアップ ファイルのすべてのチェックサム生成に影響します。|
|提案される解決策|.NET Framework 4.7.2 以降を対象とし、SHA1 ハッシュの動作に戻す開発者は、以下の AppContext フラグを設定する必要があります。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET 4.7.2 より前のバージョンのフレームワークを対象とするときに SHA256 ハッシュを利用する開発者は、以下の AppContext フラグを設定する必要があります。  インストールされている .NET Framework のバージョンは 4.7.2 以降である必要があることに注意してください。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|透明|
|Version|4.7.2|
|型|再ターゲット中|

---
ms.openlocfilehash: d3d336b9626437d8fb597de421005763afd5f021
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859319"
---
### <a name="changes-in-path-normalization"></a>パスの正規化の変更

|   |   |
|---|---|
|説明|.NET Framework 4.6.2 を対象とするアプリより、ランタイムによってパスを正規化する方法が変わりました。パスの正規化では、パスまたはファイルを識別する文字列を変更し、対象のオペレーティング システムの有効なパスに準拠するようにします。 通常、正規化では次のことを行います。<ul><li>コンポーネントとディレクトリの区切り記号を正規化する。</li><li>現在のディレクトリを相対パスに適用する。</li><li>パスの相対ディレクトリ (.) または親ディレクトリ (..) を評価する。</li><li>指定した文字をトリミングする。</li></ul>.NET Framework 4.6.2 を対象とするアプリより、パス正規化の次の変更が既定で有効になっています。<ul><li>ランタイムはオペレーティング システムの [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) 関数に従って、パスを正規化します。</li><li>正規化では、ディレクトリ セグメントの末尾 (ディレクトリ名の末尾のスペースなど) がトリミングされなくなりました。</li><li><code>\\.\</code> and, for file I/O APIs in mscorlib.dll, <code>\\?\</code>. も含め、デバイスのパス構文が完全に信頼されます。</li><li>The runtime does not validate device syntax paths.</li><li>The use of device syntax to access alternate data streams is supported.</li></ul>These changes improve performance while allowing methods to access previously inaccessible paths. Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.|
|提案される解決策|.NET Framework 4.6.2 以降を対象とするアプリの場合、アプリケーション構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加することでこの変更を無効にし、従来の正規化を使用できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.6.1 以前を対象とするが、.NET Framework 4.6.2 以降で実行されるアプリの場合、アプリケーション構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加することで、パス正規化の変更を有効にできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.6.2|
|型|再ターゲット中|


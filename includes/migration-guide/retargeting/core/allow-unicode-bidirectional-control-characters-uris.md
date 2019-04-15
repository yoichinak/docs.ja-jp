---
ms.openlocfilehash: 3e9a1009167d8a765bc401d64a574bd123736ccd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234023"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>URI での Unicode の双方向制御文字の許可

|   |   |
|---|---|
|説明|Unicode では、テキストの方向を指定するために使用される特殊な制御文字をいくつか指定します。 以前のバージョンの .NET Framework では、これらの文字は、パーセントでエンコードされたフォームに存在する場合でも、すべての URI から正しく削除されませんでした。 [RFC 3987](https://tools.ietf.org/html/rfc3987) により適切に従うために、これらの文字を URI で使用できるようにしました。 これらの文字は、URI でエンコードされていないことがわかった場合、パーセントでエンコードされます。 パーセントでエンコードされていることがわかった場合は、そのままです。|
|提案される解決策|4.7.2 以降のバージョンの .NET Framework を対象とするアプリケーションの場合は、Unicode の双方向文字のサポートが既定で有効になります。 この変更が望ましくない場合、アプリケーションの構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) スイッチを追加することで無効にできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以前のバージョンの .NET Framework を対象とするが、.NET Framework 4.7.2 以降のバージョンで実行するアプリケーションの場合、Unicode の双方向文字のサポートが既定で無効になります。 アプリケーションの構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) スイッチを追加することで有効にできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

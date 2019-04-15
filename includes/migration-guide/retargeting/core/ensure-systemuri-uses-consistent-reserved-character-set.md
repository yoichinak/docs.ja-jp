---
ms.openlocfilehash: 2ec5224b1ab16c05f6f942f6084f1ab105b71b0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233987"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>System.Uri で一貫した予約文字セットが確実に使用されるようになった

|   |   |
|---|---|
|説明|<xref:System.Uri?displayProperty=fullName> では、場合によってはデコードされていたパーセントでエンコードされた特定の文字の状態が常に保たれるようになりました。 これは、URI のパス、クエリ、フラグメント、ユーザー情報コンポーネントにアクセスするプロパティやメソッド全体に適用されます。 以下の両方に該当する場合にのみ、動作が変わります。<ul><li><code>:</code>、<code>'</code>、<code>(</code>、<code>)</code>、<code>!</code>、<code>*</code> のいずれかの予約文字のエンコードされたフォームが URI に含まれている。</li><li>Unicode またはエンコードの予約されていない文字が URI に含まれている。 上記の両方に該当する場合、エンコードの予約文字はエンコードされたままです。 以前のバージョンの .NET Framework では、デコードされます。</li></ul>|
|提案される解決策|4.7.2 以降のバージョンの .NET Framework を対象とするアプリケーションの場合は、新しいデコード動作が既定で有効になります。 この変更が望ましくない場合、アプリケーションの構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) スイッチを追加することで無効にできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以前のバージョンの .NET Framework を対象とするが、.NET Framework 4.7.2 以降のバージョンで実行するアプリケーションの場合、新しいデコード動作が既定で無効になります。 アプリケーションの構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) スイッチを追加することで有効にできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

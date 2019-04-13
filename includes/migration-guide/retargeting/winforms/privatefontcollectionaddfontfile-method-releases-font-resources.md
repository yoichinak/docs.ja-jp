---
ms.openlocfilehash: c923d9b341bbf0a21d73ac75cc6cb1a037f37826
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760863"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>PrivateFontCollection.AddFontFile メソッドが Font リソースを解放する

|   |   |
|---|---|
|説明|.NET Framework 4.7.1 およびそれより前のバージョンの <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> クラスは、<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> メソッドを使用してこのコレクションに追加された <xref:System.Drawing.Font> オブジェクトの <xref:System.Drawing.Text.PrivateFontCollection> が破棄された後も、GDI+ フォント リソースを解放しません。 .NET Framework 4.7.2 およびそれより降の <xref:System.Drawing.Text.FontCollection.Dispose%2A> は、ファイルとしてコレクションに追加された GDI+ フォントを解放します。|
|提案される解決策|<strong>以上の変更を選択する方法と選択しない方法</strong> アプリケーションでこれらの変更を利用するには、.NET Framework 4.7.2 以降で実行する必要があります。 アプリケーションは、次のいずれかの方法でこれらの変更を利用できます。<ul><li>.NET Framework 4.7.2 を対象にして再コンパイルします。 .NET Framework 4.7.2 以降を対象とする Windows フォーム アプリケーションでは、この変更が既定で有効になります。</li><li>.NET Framework 4.7.1 以前を対象にして、下の例のように、app.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContext スイッチ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)を追加し、それを <code>false</code> に設定することで、以前のアクセシビリティ動作を無効にします。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7.2 以降を対象とするアプリケーションで以前の動作を残す場合、この AppContext スイッチを明示的に <code>true</code> に設定することで、フォント リソースを解放しないようにすることができます。|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|


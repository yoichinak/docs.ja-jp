---
ms.openlocfilehash: 7344fddbc61d47d4ca735808f0b92f63e33e15a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760864"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm の Domain upbutton アクションと downbutton アクションが同期するようになった

|   |   |
|---|---|
|説明|.NET Framework 4.7.1 およびそれより前のバージョンでは、コントロールにテキストが存在すると <xref:System.Windows.Forms.DomainUpDown> コントロールの <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> アクションが無視され、開発者は <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> アクションを使用する前にコントロールで <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> アクションを使用する必要があります。 .NET Framework 4.7.2 以降では、このシナリオで <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> アクションと <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> アクションの両方が独立して動作し、同期を維持します。|
|提案される解決策|アプリケーションでこれらの変更を利用するには、.NET Framework 4.7.2 以降で実行する必要があります。 アプリケーションは、次のいずれかの方法でこれらの変更を利用できます。<ul><li>.NET Framework 4.7.2 を対象にして再コンパイルします。 .NET Framework 4.7.2 以降を対象とする Windows フォーム アプリケーションでは、この変更が既定で有効になります。</li><li>下の例のように、app.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContext スイッチ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)を追加し、それを <code>false</code> に設定することで、以前のスクロール動作を無効にします。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|


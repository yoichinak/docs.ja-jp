---
ms.openlocfilehash: 3bde64b80e5dcfe98bbf598700b6d7004e3c3c9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234051"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>キーボード フォーカスが WinForms/WPF ホストの複数層の間で正しく移動するようになった

|   |   |
|---|---|
|説明|WinForms コントロールをホストし、さらに WPF コントロールをホストする WPF アプリケーションがあるとします。 WinForms 層の最初または最後のコントロールが WPF <code>System.Windows.Forms.Integration.ElementHost</code> である場合、ユーザーはこの層を Tab キーで移動できないことがあります。 今回の変更でこの問題が修正され、ユーザーは WinForms 層を Tab キーで移動できるようになりました。WinForms 層をエスケープしないフォーカスに依存する自動アプリケーションは、期待どおりに動作しなくなる可能性があります。|
|提案される解決策|.NET 4.7.2 より前のバージョンのフレームワークを対象とするときに、この変更を利用する開発者は、次の一連の AppContext フラグを false に設定することで変更を有効にできます。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>WPF アプリケーションでより新しい改善を得るには、アクセシビリティに関する以前の改善をすべてオプトインする必要があります。 つまり、<code>Switch.UseLegacyAccessibilityFeatures</code> および <code>Switch.UseLegacyAccessibilityFeatures.2</code> スイッチの両方が設定されている必要があります。 .NET 4.7.2 以降を対象とするときに、前の機能を必要とする開発者は、次の AppContext フラグを true に設定することで変更を無効にできます。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|

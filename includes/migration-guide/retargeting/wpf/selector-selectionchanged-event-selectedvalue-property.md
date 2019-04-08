---
ms.openlocfilehash: a4054ee893ba8b8c290a447689d3aa58dcc84cbe
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "52742283"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>セレクター SelectionChanged イベントおよび SelectedValue プロパティ

|   |   |
|---|---|
|説明|NET Framework 4.7.1 以降、<xref:System.Windows.Controls.Primitives.Selector> は選択の変更が発生すると必ず、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> イベントが発生する前に <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> プロパティの値を更新します。 これにより、SelectedValue プロパティと、イベント発生前に更新されるその他の選択プロパティ (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> および <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>) との整合性が確保されます。<p/>.NET Framework 4.7 以前のバージョンでは、ほとんどの場合、イベントの前に SelectedValue に対する更新が行われました。しかし、選択の変更が <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> プロパティの変更に起因している場合、SelectedValue に対する更新はイベントの後に行われていました。|
|提案される解決策|.NET Framework 4.7.1 以降を対象とするアプリでこの変更を無効にし、従来の動作を使用することができます。その場合、アプリケーション構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加します。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7 以前を対象とするものの、.NET Framework 4.7.1 以降で実行されているアプリでは、新しい動作を有効にすることができます。その場合、アプリケーション構成ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加します。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|


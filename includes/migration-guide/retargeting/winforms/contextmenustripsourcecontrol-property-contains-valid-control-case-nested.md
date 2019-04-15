---
ms.openlocfilehash: f1a1eab471d46f018a8e0d0cf787d487cf67c11e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234022"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>入れ子になった ToolStripMenuItems の場合、ContextMenuStrip.SourceControl プロパティには有効なコントロールが含まれる

|   |   |
|---|---|
|説明|.NET Framework 4.7.1 およびそれより前のバージョンの <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> プロパティは、ユーザーが入れ子になった <xref:System.Windows.Forms.ToolStripMenuItem> コントロールからメニューを開いたとき、正しくない null を返します。 .NET Framework 4.7.2 およびそれ以降では、<xref:System.Windows.Forms.ContextMenuStrip.SourceControl> プロパティには常に実際のソース コントロールが設定されます。|
|提案される解決策|<strong>以上の変更を選択する方法と選択しない方法</strong> アプリケーションでこれらの変更を利用するには、.NET Framework 4.7.2 以降で実行する必要があります。 アプリケーションは、次のいずれかの方法でこれらの変更を利用できます。<ul><li>.NET Framework 4.7.2 を対象にします。 .NET Framework 4.7.2 以降を対象とする Windows フォーム アプリケーションでは、この変更が既定で有効になります。</li><li>.NET Framework 4.7.1 以前を対象にして、下の例のように、app.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContext スイッチ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)を追加し、それを <code>false</code> に設定することで、以前のアクセシビリティ動作を無効にします。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7.2 以降を対象とするアプリケーションで以前の動作を残す場合、この AppContext スイッチを明示的に <code>true</code> に設定することで、以前のソース コントロール値を選択できます。|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|

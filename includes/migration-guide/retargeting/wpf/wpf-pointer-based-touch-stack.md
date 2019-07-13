---
ms.openlocfilehash: bb3d7c1afa9e506ffc7c6d068c48428d1e66ccb6
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379439"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF ポインター ベースのタッチ スタック

|   |   |
|---|---|
|説明|この変更で、オプションの WM_POINTER ベースの WPF タッチ/スタイラス スタックを有効にする機能が追加されます。  これを明示的に有効にしていない開発者は、WPF タッチ/スタイラス動作の変更を確認できません。オプションの WM_POINTER ベースのタッチ/スタイラス スタックに関する現在の既知の問題を以下に示します。<ul><li>リアルタイム インクがサポートされない。</li><li>インクと StylusPlugins がまだ機能している間は、UI スレッドで処理されますが、パフォーマンスの低下につながる可能性があります。</li><li>プロモーションの変更により、タッチ/スタイラス イベントからマウス イベントに動作が変更される。</li><li>操作の動作が異なる場合があります。</li><li>ドラッグ/ドロップでは、タッチ入力の適切なフィードバックが表示されません。</li><li>これはスタイラス入力には影響しません。</li><li>ドラッグ/ドロップは、タッチ/スタイラス イベントで開始できなくなりました。</li><li>そのため、マウス入力が検出されるまで、アプリケーションが応答を停止する可能性があります。</li><li>代わりに、開発者はマウス イベントからドラッグ アンド ドロップを開始する必要があります。</li></ul>|
|提案される解決策|このスタックを有効にする開発者は、アプリケーションの App.config ファイルに次の行を追加/マージできます。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>これを削除するか、値を false に設定すると、このオプションのスタックがオフになります。このスタックは Windows 10 Creators Update 以降でのみ使用できることに注意してください。|
|スコープ|エッジ|
|Version|4.7|
|型|再ターゲット中|

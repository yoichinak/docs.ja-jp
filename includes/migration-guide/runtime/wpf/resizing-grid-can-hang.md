---
ms.openlocfilehash: 2e870b8d7b8ed986863632f947223946a6604f89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802442"
---
### <a name="resizing-a-grid-can-hang"></a>グリッドのサイズを変更すると、ハングする可能性がある

|   |   |
|---|---|
|説明|次の状況では、<code>T:System.Windows.Controls.Grid</code> のレイアウト中に無限ループが発生する可能性があります。<ul><li>行の定義に、MinHeight と MaxHeight の両方を宣言する、2 つの * 行が含まれている。</li><li>\* 行のコンテンツが対応する MaxHeight を超えていない。</li><li>最初の MinHeight (その他の固定または自動の行を含む) がグリッドの利用可能な高さを超えている。</li><li>アプリの対象を .NET Framework 4.7 とする、または <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> を設定して、4.7 割り当てアルゴリズムを利用することを選択する。</li></ul>また、3 つ以上の行または列でループが発生します。 .NET Framework 4.7.1 でこの問題が解決されます。|
|提案される解決策|.NET Framework 4.7.1 にアップグレードします。  4\.7 割り当てアルゴリズムが必要でない場合は、次の構成設定を使用することもできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7|
|型|ランタイム|


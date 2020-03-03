---
ms.openlocfilehash: 88e00454894c8404fd48e92404e35ae27fa056f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235424"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>WPF TreeViewItem は TreeView 内で使用する必要がある

|   |   |
|---|---|
|説明|<xref:System.Windows.Controls.TreeView?displayProperty=name> の外部での <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> 要素の使用を制限する変更が 4.5 で導入されました。 これは、次のような条件で発生します。<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> のビジュアルの親がパネルではありません。 (<xref:System.Windows.Controls.TreeView?displayProperty=name> に対して生成された <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> は、親としてパネルを持ちます)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> は、リスト コントロール (ListBox、DataGrid、ListView など) の &quot;項目ホスト&quot; として機能する <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> の子孫です。 仮想化を有効にする必要はありません。</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> は、項目のスクロールです (<code>ScrollUnit=&quot;Item&quot;</code>)。</li><li>誰かが要素 <code>v</code> をスクロールして表示させるために <code>VirtualizingStackPanel.MakeVisible(v)</code> を呼び出します。 これは、明示的に行うか、さまざまな方法で暗黙的に行うことができます。おそらく、最も一般的な方法は、<code>v</code> をクリックして、キーボードのフォーカスを与えることです。</li><li><code>v</code> から <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> までのビジュアル親チェーンが <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> を通過します。</li></ul>言い換えると、これは、<xref:System.Windows.Controls.TreeViewItem?displayProperty=name> が <xref:System.Windows.Controls.TreeView?displayProperty=name> の外部で使用されるときに見られ、ユーザーは <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> の子孫をクリックして表示させます。 <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> にフォーカスを取得できる子孫がない場合、この問題は見られません。 これが該当する状況の例は、<xref:System.Windows.Controls.TreeViewItem?displayProperty=name> が DataTemplate のルートであるときです。 この問題に遭遇したときには、WPF フレームワーク内で InvalidCastException が発生しています。|
|提案される解決策|このための修正プログラムが使用可能になります。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|

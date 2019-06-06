---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379235"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a>VirtualizingStackPanel 内の WPF TreeView またはグループ化された ListBox をスクロールすると、アプリケーションが応答しなくなることがある

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、仮想化されたスタック パネル内の WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> をスクロールすると、ビューポートに余白があった場合 (たとえば、<xref:System.Windows.Controls.TreeView?displayProperty=name> 内の項目間や、ItemsPresenter 要素上)、アプリケーションが応答しなくなることがあります。 さらに、場合によっては、ビュー内にサイズの異なる項目があると、余白がない場合でも、不安定になることがあります。|
|提案される解決策|このバグは、.NET Framework 4.5.1 にアップグレードすることによって回避できます。 または、含まれているすべての項目が同じサイズである場合は、仮想化されたスタック パネル内のビュー コレクション (<xref:System.Windows.Controls.TreeView?displayProperty=name> など) から余白を削除できます。|
|スコープ|Major|
|バージョン|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

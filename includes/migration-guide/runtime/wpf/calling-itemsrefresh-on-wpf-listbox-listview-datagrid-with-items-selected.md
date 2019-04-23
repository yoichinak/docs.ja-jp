---
ms.openlocfilehash: de73145273ad5aa5c19de55525417cfc3305b86d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804381"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>項目が選択されている WPF ListBox、ListView、または DataGrid に対して Items.Refresh を呼び出すと、重複した項目が要素に表示されることがある

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、<xref:System.Windows.Controls.ListBox?displayProperty=name> で項目が選択されているときにコードから ListBox.Items.Refresh を呼び出すと、選択された項目がリストに複製されることがあります。 同様の問題が <xref:System.Windows.Controls.ListView?displayProperty=name> と <xref:System.Windows.Controls.DataGrid?displayProperty=name> で発生します。 これは、.NET Framework 4.6 で修正されます。|
|提案される解決策|この問題は、<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> が呼び出される前に、プログラムで項目を選択解除して、呼び出しの完了後に再び選択することによって回避できます。 または、この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

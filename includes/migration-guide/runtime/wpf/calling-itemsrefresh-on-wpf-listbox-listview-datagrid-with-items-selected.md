---
ms.openlocfilehash: 22c67c687f5581c181acc4aeab8910c4467fd424
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858427"
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


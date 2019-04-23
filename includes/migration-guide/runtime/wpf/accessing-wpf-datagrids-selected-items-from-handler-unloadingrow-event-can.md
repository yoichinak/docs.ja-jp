---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804376"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>DataGrid の UnloadingRow イベントのハンドラーから WPF DataGrid の選択された項目にアクセスすると、NullReferenceException が発生する可能性がある

|   |   |
|---|---|
|説明|.NET Framework 4.5 のバグが原因で、行の削除に関連する <xref:System.Windows.Controls.DataGrid> イベントのイベント ハンドラーにより、<xref:System.Windows.Controls.DataGrid> の <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> または <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> プロパティにアクセスする場合に <xref:System.NullReferenceException?displayProperty=name> がスローされる可能性があります。|
|提案される解決策|この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

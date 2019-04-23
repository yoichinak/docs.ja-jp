---
ms.openlocfilehash: b761cb699c4677f815835cdab9c6aa3039f5bb38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804345"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectiontmove"></a>ObservableCollection\<T>.Move に対する ListBoxItem IsSelected のバインディングの問題

|   |   |
|---|---|
|説明|項目が選択された <xref:System.Windows.Controls.ListBox?displayProperty=name> にバインドされるコレクションで <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> または <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> を呼び出すと、<xref:System.Windows.Controls.ListBox?displayProperty=name> 項目の今後の選択または選択解除で不規則な動作が発生する可能性があります。|
|提案される解決策|<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ではなく <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> と <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> を呼び出すことで、この問題は解決されます。 または、この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

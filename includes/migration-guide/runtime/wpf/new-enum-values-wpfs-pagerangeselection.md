---
ms.openlocfilehash: edd194fef27d97976f1ff45daec1cd56382bbb55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804406"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a>WPF の PageRangeSelection の新しい列挙値

|   |   |
|---|---|
|説明|新しい 2 つのメンバー (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=name> および <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=name>) が <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> 列挙型に追加されました。|
|提案される解決策|ほとんどの場合、これらの変更はユーザー コードに影響しません。 ただし、<xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> 型に対する <xref:System.Enum.GetNames(System.Type)> または <xref:System.Enum.GetValues(System.Type)> 呼び出しに特定の数の要素が存在することに依存するコードは、修正する必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|

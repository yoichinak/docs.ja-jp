---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804400"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>TextBlock コントロールの親の IsEnabled プロパティの変更がすべての子コントロールに影響する

|   |   |
|---|---|
|説明|.NET Framework 4.6.2、変更以降の<xref:System.Windows.UIElement.IsEnabled?displayProperty=name>の親のプロパティ、<xref:System.Windows.Controls.TextBlock?displayProperty=name>コントロール (ハイパーリンクやボタンなど) などの子コントロールに影響を与える、<xref:System.Windows.Controls.TextBlock?displayProperty=name>コントロール。 .NET Framework 4.6.1 以前のバージョンで、内部コントロール、<xref:System.Windows.Controls.TextBlock?displayProperty=name>の状態を常に反映されませんでした、<xref:System.Windows.UIElement.IsEnabled?displayProperty=name>のプロパティ、<xref:System.Windows.Controls.TextBlock?displayProperty=name>親。|
|提案される解決策|なし。 この変更は、<xref:System.Windows.Controls.TextBlock?displayProperty=name> コントロール内部のコントロールに期待される動作に準拠しています。|
|スコープ|マイナー|
|Version|4.6.2|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

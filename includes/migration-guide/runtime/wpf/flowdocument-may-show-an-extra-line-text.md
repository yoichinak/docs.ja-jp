---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379634"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument でテキストの余分な行が表示される場合がある

|   |   |
|---|---|
|説明|.NET Framework 4.0 での実行時の表示と比べて、.NET Framework 4.5 での実行時に <xref:System.Windows.Documents.FlowDocument> 要素でテキストの余分な行が表示されることがあります。 変更によってテキストが正しく表示されなくなったり、読みにくくなったりするようなことはありませんが、以前は <xref:System.Windows.Documents.FlowDocument> のビューから除外されていたテキストが表示される可能性があります。|
|提案される解決策|場合によっては、表示要素の PageHeight プロパティを 1 ずつ減らすことで、表示行の以前の数を復元できます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

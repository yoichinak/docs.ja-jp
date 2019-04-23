---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804359"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException で行位置が正しく設定されるようになった

|   |   |
|---|---|
|説明|<xref:System.Xml.Linq.LoadOptions.SetLineInfo> 値が Load メソッドに渡されたときに検証エラーが発生すると、<xref:System.Xml.Schema.XmlSchemaException.LineNumber> プロパティと <xref:System.Xml.Schema.XmlSchemaException.LinePosition> プロパティに行情報が含まれるようになりました。|
|提案される解決策|XML の読み込み中に SetLineInfo が使用されるとき、<xref:System.Xml.Schema.XmlSchemaException.LineNumber> と <xref:System.Xml.Schema.XmlSchemaException.LinePosition> は正しく設定されるようになったので、これらのプロパティが設定されないことを想定している例外処理コードは、更新する必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

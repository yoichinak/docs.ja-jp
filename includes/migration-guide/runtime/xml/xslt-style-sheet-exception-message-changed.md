---
ms.openlocfilehash: be9933e177954dc0aced81a550ef92f2c2ca08f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804357"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT スタイル シートの例外メッセージが変更された

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、XSLT ファイルが複雑すぎるときのエラー メッセージのテキストが &quot;スタイル シートが複雑すぎます&quot; になります。以前のバージョンのエラー メッセージは &quot;XSLT コンパイル エラー&quot; でした。エラー メッセージのテキストに依存するアプリケーション コードは機能しなくなります。 ただし、例外の種類は同じなので、この変更による実質的な影響はありません。|
|提案される解決策|このエラー条件からの例外メッセージに依存しているアプリケーション コードを、新しいメッセージを予期するように更新するか、(さらに望ましくは) 変更されていない例外の種類 (<xref:System.Xml.Xsl.XsltException?displayProperty=name>) のみに依存するようにコードを更新します。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

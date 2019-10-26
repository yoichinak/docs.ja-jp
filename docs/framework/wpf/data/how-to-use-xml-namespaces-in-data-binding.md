---
title: '方法 : データ バインドで XML 名前空間を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919668"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>方法 : データ バインドで XML 名前空間を使用する
## <a name="example"></a>例
 この例では、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] のバインディング ソースに指定された名前空間の処理方法を示します。

 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データに次の [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間定義がある場合:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 次の例に示すように、<xref:System.Windows.Data.XmlNamespaceMapping> 要素を使用して、名前空間を <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>にマップできます。 その後、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> を使用して、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間を参照できます。 この例の <xref:System.Windows.Controls.ListBox> では、各*項目*の*タイトル*と*dc: date*が表示されます。

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 指定した <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> は、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ソースで使用されているものと一致する必要がないことに注意してください。[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ソースでプレフィックスが変更された場合、マッピングは引き続き機能します。

 この例では、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データは web サービスから取得されますが、<xref:System.Windows.Data.XmlNamespaceMapping> 要素はインライン [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] または埋め込みファイル内のデータの [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] でも機能します。

## <a name="see-also"></a>関連項目

- [XMLDataProvider と XPath クエリを使用して XML データにバインドする](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

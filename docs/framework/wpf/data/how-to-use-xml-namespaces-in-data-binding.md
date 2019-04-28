---
title: '方法: データ バインドで XML 名前空間を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 38bf6e8f88b0325193d49148cd6c33031f7b0a6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931912"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>方法: データ バインドで XML 名前空間を使用する
## <a name="example"></a>例  
 この例では、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] のバインディング ソースに指定された名前空間の処理方法を示します。  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データに次の [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間定義がある場合:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 使用することができます、<xref:System.Windows.Data.XmlNamespaceMapping>要素に名前空間にマップを<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>次の例のようにします。 使用することができますし、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>を参照する、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間。 <xref:System.Windows.Controls.ListBox>この例では、表示、*タイトル*と*dc:date*それぞれの*項目*します。  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 なお、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>指定で使用されるものと一致する必要はありません、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ソース; でプレフィックスが変更された場合、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ソース マッピングが正常に動作します。  
  
 この例では、 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] web サービスでは、基になるが、<xref:System.Windows.Data.XmlNamespaceMapping>要素はインラインでも動作[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]または[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]埋め込みファイル内のデータ。  
  
## <a name="see-also"></a>関連項目

- [XMLDataProvider と XPath クエリを使用して XML データにバインドする](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

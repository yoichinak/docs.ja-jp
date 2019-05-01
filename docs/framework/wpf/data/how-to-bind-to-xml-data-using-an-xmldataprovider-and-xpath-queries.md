---
title: '方法: XMLDataProvider と XPath クエリを使用して XML データにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 3a3df65f0c20cff49f9bd2a8790e8d9ae0032391
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809580"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>方法: XMLDataProvider と XPath クエリを使用して XML データにバインドする
この例にバインドする方法を示しています。[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]を使用してデータを<xref:System.Windows.Data.XmlDataProvider>します。  
  
 <xref:System.Windows.Data.XmlDataProvider>、基になるアプリケーションでデータ バインディングを介してアクセスできるデータの任意のツリー、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ノード。 つまり、<xref:System.Windows.Data.XmlDataProvider>の任意のツリーを使用する便利な手段を提供します。[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]バインディング ソースとしてのノード。  
  
## <a name="example"></a>例  
 次の例では、データとして直接埋め込まれて、 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *データ アイランド*内、<xref:System.Windows.FrameworkElement.Resources%2A>セクション。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ アイランドは、`<x:XData>` タグ内にラップされていることと、常にルート ノードを 1 つだけ (この例では *Inventory*) 持つことが必要です。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データのルート ノードには、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間を空の文字列に設定する **xmlns** 属性があります。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページ内にインラインで配置されるデータ アイランドに XPath クエリを適用する場合に必須です。 このインラインの場合は、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、データ アイランドの継承、<xref:System.Windows>名前空間。 このため、名前空間によって修飾されることから XPath クエリを保持する場合は空白を設定する必要があります、<xref:System.Windows>名前空間は、クエリの送信先を誤るとします。  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 この例に示すように、同じバインディング宣言を属性構文で作成するには、特殊文字を適切にエスケープする必要があります。 詳しくは、「[XML Character Entities and XAML](../../xaml-services/xml-character-entities-and-xaml.md)」(XML 文字エンティティと XAML) をご覧ください。  
  
 <xref:System.Windows.Controls.ListBox>この例の実行時に次の項目が表示されます。 これらは、*Books* の下のすべての要素のうち、*Stock* の値が "*out*" か、*Number* の値が 3 に等しいか 8 以上のものの *Title* です。 注意していない*CD*ために、項目が返されます、<xref:System.Windows.Data.XmlDataProvider.XPath%2A>で一連の値を<xref:System.Windows.Data.XmlDataProvider>だけであることを示します、*ブックの「* (基本的にフィルターを設定する) 要素を公開する必要があります。  
  
 ![次の 4 つの書籍のタイトルを表示する XPath の例のスクリーン ショット。](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 ため、この例で書籍のタイトルが表示される、<xref:System.Windows.Data.Binding.XPath%2A>の<xref:System.Windows.Controls.TextBlock>バインド、<xref:System.Windows.DataTemplate>に設定されている"*タイトル*"。 属性の値を表示するかどうか、 *ISBN*を設定する<xref:System.Windows.Data.Binding.XPath%2A>値を"`@ISBN`"。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内の **XPath** プロパティは、XmlNode.SelectNodes メソッドによって処理されます。 別の結果を得るために、**XPath** クエリを変更できます。 いくつかの例を次のとおり、<xref:System.Windows.Data.Binding.XPath%2A>にバインドされているクエリを<xref:System.Windows.Controls.ListBox>前の例。  
  
- `XPath="Book[1]"` は、最初の書籍要素 ("XML in Action") を返します。 **XPath** のインデックスが 0 ではなく 1 から開始することにご注意ください。  
  
- `XPath="Book[@*]"` は、任意の属性を持つすべての書籍要素を返します。  
  
- `XPath="Book[last()-1]"` は、最後から 2 番目の書籍要素 ("Introducing Microsoft .NET") を返します。  
  
- `XPath="*[position()>3]"` は、最初の 3 つを除くすべての書籍要素を返します。  
  
 実行すると、 **XPath**クエリを返します、<xref:System.Xml.XmlNode>または Xmlnode のリスト。 <xref:System.Xml.XmlNode> [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクトは、使用できる、<xref:System.Windows.Data.Binding.Path%2A>プロパティにバインドする、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]プロパティ。 前の例をもう一度考えてみます。 この例の残りの部分は同じままで変更した場合、 <xref:System.Windows.Controls.TextBlock> 、次のバインド、返された Xmlnode の名前が表示されます、 <xref:System.Windows.Controls.ListBox>。 この場合、返されたノードの名前はすべて "*Book*" です。  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページのソースに [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] をデータ アイランドとして埋め込む方法では、コンパイル時に正確なデータ コンテンツが必要となるので、アプリケーションによっては不都合が生じます。 したがって、次の例のように、外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ファイルからのデータの取得もサポートされています。  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 場合、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データをリモートに存在する[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイルのアクセスを定義、データを適切な割り当てによって[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]を<xref:System.Windows.Data.XmlDataProvider.Source%2A>次のように属性します。  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.ObjectDataProvider>
- [XDocument、XElement、または LINQ for XML クエリの結果にバインドする](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [階層 XML データでマスター詳細パターンを使用する](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [バインディング ソースの概要](binding-sources-overview.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

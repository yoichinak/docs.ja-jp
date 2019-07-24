---
title: '方法: XAML でデータをバインディング可能にする'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401494"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>方法: XAML でデータをバインディング可能にする
このトピックでは、アプリケーションのニーズに応じて、で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]データをバインドできるようにするさまざまな方法について説明します。  
  
## <a name="example"></a>例  
 バインド[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]先の共通言語ランタイム (CLR) オブジェクトがある場合は、そのオブジェクトをリソースとして定義し、 `x:Key`それをに設定する方法の1つです。 次の例では、という`Person`名前`PersonName`の文字列プロパティを持つオブジェクトがあります。 オブジェクト (要素を`<src>`含む強調表示されている行) は、という`SDKSample`名前空間で定義されています。 `Person`  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 次に、 <xref:System.Windows.Controls.TextBlock> `<TextBlock>`要素を含む強調表示され[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]た行に示されているように、コントロールをのオブジェクトにバインドできます。 
  
 または、次の例<xref:System.Windows.Data.ObjectDataProvider>のように、クラスを使用することもできます。  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 バインドは、 `<TextBlock>`要素を含む強調表示された行が示すように、同じ方法で定義します。  
  
 この例では、結果は同じです。テキストコンテンツ<xref:System.Windows.Controls.TextBlock> `Joe`を含むがあります。 ただし、クラス<xref:System.Windows.Data.ObjectDataProvider>には、メソッドの結果にバインドする機能などの機能が用意されています。 提供される機能が必要<xref:System.Windows.Data.ObjectDataProvider>な場合は、クラスを使用することを選択できます。  
  
 ただし、既に作成されているオブジェクトにバインドする場合は、次の例に`DataContext`示すように、コードでを設定する必要があります。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 クラスを使用してバインドするデータにアクセス[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]するには、「 [xmldataprovider と XPath クエリを使用して XML データにバインド](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)する」を参照してください。 <xref:System.Windows.Data.XmlDataProvider> クラスを使用してバインドするデータにアクセス[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]するには、「 [XDocument、XElement、または LINQ for XML のクエリ結果へのバインド](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)」を参照してください。 <xref:System.Windows.Data.ObjectDataProvider>  
  
 バインド先のデータを指定するさまざまな方法の詳細については、「[バインディングソースを指定](how-to-specify-the-binding-source.md)する」を参照してください。 バインドできるデータの種類や、独自の共通言語ランタイム (CLR) オブジェクトをバインド用に実装する方法の詳細については、「[バインディングソースの概要](binding-sources-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

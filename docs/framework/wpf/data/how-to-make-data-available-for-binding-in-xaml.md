---
title: '方法 : XAML でデータをバインディング可能にする'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174187"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>方法 : XAML でデータをバインディング可能にする
このトピックでは、アプリケーションのニーズに応じて、 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]データをバインドできるようにするさまざまな方法について説明します。  
  
## <a name="example"></a>例  
 にバインド[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]する共通言語ランタイム (CLR) オブジェクトがある場合は、バインドに使用できるオブジェクトをリソースとして定義し、それを与える方法の`x:Key`1 つです。 次の例では、という名前`Person``PersonName`の文字列プロパティを持つオブジェクトがあります。 `Person`オブジェクト (`<src>`要素を含む強調表示された行) は、名前空間で定義されます`SDKSample`。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 要素を<xref:System.Windows.Controls.TextBlock>含む強調表示された行に[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]示すように、 のオブジェクトにコントロールを`<TextBlock>`バインドできます。
  
 または、次の<xref:System.Windows.Data.ObjectDataProvider>例のように、クラスを使用できます。  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 バインドは、要素を含む強調表示された行が示すように、同じ`<TextBlock>`方法で定義します。  
  
 この特定の例では、結果は同じです: テキストコンテンツ<xref:System.Windows.Controls.TextBlock>`Joe`を持つ を持っています。 ただし、この<xref:System.Windows.Data.ObjectDataProvider>クラスには、メソッドの結果にバインドする機能などの機能が用意されています。 クラスが提供する機能が<xref:System.Windows.Data.ObjectDataProvider>必要な場合は、このクラスを使用できます。  
  
 ただし、既に作成されているオブジェクトにバインドする場合は、次`DataContext`の例のように in コードを設定する必要があります。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 クラスを使用してバインドする XML<xref:System.Windows.Data.XmlDataProvider>データにアクセスするには[、「XMLDataProvider および XPath クエリを使用した XML データへのバインド](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。 クラスを使用してバインドする XML<xref:System.Windows.Data.ObjectDataProvider>データにアクセスするには、「 [XDocument、XElement、または LINQ for XML クエリの結果へのバインド](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)」を参照してください。  
  
 バインドするデータを指定するさまざまな方法については、「[バインディング ソースの指定](how-to-specify-the-binding-source.md)」を参照してください。 バインドできるデータの種類や、バインド用の独自の共通言語ランタイム (CLR) オブジェクトの実装方法については、「 バインディング[ソースの概要](binding-sources-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [データバインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)
- [ハウツートピック](data-binding-how-to-topics.md)

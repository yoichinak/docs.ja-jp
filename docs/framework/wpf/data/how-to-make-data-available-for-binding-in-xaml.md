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
ms.openlocfilehash: 1f024ddd0be023f77408e3106bc0a4465d068074
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358289"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>方法: XAML でデータをバインディング可能にする
このトピックでは、利用できるデータのバインドでさまざまな方法を説明[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]アプリケーションのニーズに応じて、します。  
  
## <a name="example"></a>例  
 ある場合、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクトにバインドしたい[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、使用できるように、オブジェクトは、バインドをリソースとして定義され、1 つの方法、`x:Key`します。 次の例がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`します。 `Person`オブジェクト (強調表示の行を含む、`<src>`要素) と呼ばれる名前空間で定義されて`SDKSample`します。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 バインドすることができますし、<xref:System.Windows.Controls.TextBlock>コントロール内のオブジェクトを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を強調表示された行が含まれています、`<TextBlock>`要素の表示。 
  
 また、使用することができます、<xref:System.Windows.Data.ObjectDataProvider>クラスは、次の例のように。  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 バインドを定義すると、強調表示された行を含む、同じ方法、`<TextBlock>`要素を示します。  
  
 結果では、この例では、同じ: がある、<xref:System.Windows.Controls.TextBlock>テキスト コンテンツを含む`Joe`します。 ただし、<xref:System.Windows.Data.ObjectDataProvider>クラス、メソッドの結果にバインドする機能などの機能を提供します。 使用することができます、<xref:System.Windows.Data.ObjectDataProvider>クラスを提供する機能が必要な場合。  
  
 ただし、既に作成されているオブジェクトにバインドする場合は、設定する必要、`DataContext`コードでは、次の例に示すようにします。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.XmlDataProvider>クラスを参照してください[XMLDataProvider と XPath クエリを使用して XML データにバインド](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)します。 アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.ObjectDataProvider>クラスを参照してください[XDocument、XElement、または LINQ for XML クエリの結果にバインド](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)します。  
  
 バインドするデータを指定するさまざまな方法については、[バインディング ソースを指定](how-to-specify-the-binding-source.md)を参照してください。 どのような種類のデータにバインドすることができますか、独自に実装する方法については[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、バインディングのオブジェクトを参照してください[バインディング ソースの概要](binding-sources-overview.md)します。  
  
## <a name="see-also"></a>関連項目
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)

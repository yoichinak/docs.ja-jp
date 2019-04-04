---
title: ListView の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 33f4cc55a52a67381c1fbf0d0a92bfad5e50b1ec
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186118"
---
# <a name="listview-overview"></a>ListView の概要
<xref:System.Windows.Controls.ListView>コントロールには、さまざまなレイアウトやビューにデータ項目のセットを表示するインフラストラクチャが用意されています。 たとえば、ユーザーは、テーブルにデータ項目を表示し、その列を並べ替えできます。  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>ListView とは  
 <xref:System.Windows.Controls.ListView>コントロールが、<xref:System.Windows.Controls.ItemsControl>から派生する<xref:System.Windows.Controls.ListBox>します。 通常、その項目のデータ コレクションのメンバーであるし、として表される<xref:System.Windows.Controls.ListViewItem>オブジェクト。 A<xref:System.Windows.Controls.ListViewItem>は、 <xref:System.Windows.Controls.ContentControl> 1 つの子要素のみを含めることができます。 ただし、その子要素は、任意のビジュアル要素にできます。  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>ListView の表示モードの定義  
 コンテンツの表示モードを指定する、<xref:System.Windows.Controls.ListView>コントロールを設定する、<xref:System.Windows.Controls.ListView.View%2A>プロパティ。 1 つのビュー モードを[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供は<xref:System.Windows.Controls.GridView>、カスタマイズ可能な列を持つテーブルのデータ項目のコレクションが表示されます。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.GridView>の<xref:System.Windows.Controls.ListView>従業員情報を表示するコントロール。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例でのデータの表示方法を示しています。  
  
 ![GridView 出力を含むの ListView を示すスクリーン ショット。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 継承するクラスを定義することでカスタム表示モードを作成することができます、<xref:System.Windows.Controls.ViewBase>クラス。 <xref:System.Windows.Controls.ViewBase>クラスには、カスタム ビューを作成する必要のあるインフラストラクチャが用意されています。 カスタム ビューを作成する方法の詳細については、[を ListView のカスタム表示モードを作成する](how-to-create-a-custom-view-mode-for-a-listview.md)を参照してください。  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>ListView へのデータ バインディング  
 使用して、<xref:System.Windows.Controls.ItemsControl.Items%2A>と<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の項目を指定するプロパティを<xref:System.Windows.Controls.ListView>コントロール。 次の例のセット、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティが呼び出されるデータの収集を`EmployeeInfoDataSource`します。  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 <xref:System.Windows.Controls.GridView>、<xref:System.Windows.Controls.GridViewColumn>オブジェクトは、指定したデータ フィールドにバインドします。 次の例では、バインド、<xref:System.Windows.Controls.GridViewColumn>オブジェクトを指定して、データ フィールドに、<xref:System.Windows.Data.Binding>の<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティ。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 指定することも、<xref:System.Windows.Data.Binding>の一部として、<xref:System.Windows.DataTemplate>列のセルのスタイルを使用して定義します。 次の例では、<xref:System.Windows.DataTemplate>で識別される、<xref:System.Windows.ResourceKey>設定、<xref:System.Windows.Data.Binding>の<xref:System.Windows.Controls.GridViewColumn>します。 この例で定義されていませんが、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>によって指定されるバインドをよりも優先されますので<xref:System.Windows.DataTemplate>します。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView を実装する ListView のスタイル設定  
 <xref:System.Windows.Controls.ListView>コントロールが含まれる<xref:System.Windows.Controls.ListViewItem>表示されるデータ項目を表すオブジェクト。 次のプロパティを使用して、データ項目の内容とスタイルを定義できます。  
  
-   <xref:System.Windows.Controls.ListView>コントロールを使用して、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>、および<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>プロパティ。  
  
-   <xref:System.Windows.Controls.ListViewItem>コントロールを使用して、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>と<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>プロパティ。  
  
 内のセル間のアライメントの問題を回避するために、 <xref:System.Windows.Controls.GridView>、使用しないでください、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>プロパティを設定したり、アイテムの幅に影響するコンテンツを追加する、<xref:System.Windows.Controls.ListView>します。 設定すると、アライメントの問題が発生することなど、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティ、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>します。 プロパティを指定するか、項目の幅に影響するコンテンツを定義する、<xref:System.Windows.Controls.GridView>のプロパティを使用して、<xref:System.Windows.Controls.GridView>クラスとその関連のクラスなど<xref:System.Windows.Controls.GridViewColumn>します。  
  
 使用する方法の詳細についての<xref:System.Windows.Controls.GridView>とそのサポート クラスを参照してください[GridView の概要](gridview-overview.md)します。  
  
 定義する場合、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>の<xref:System.Windows.Controls.ListView>制御し、定義することも、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、含める必要があります、<xref:System.Windows.Controls.ContentPresenter>の順序でスタイルで、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>正常に動作します。  
  
 使用しないでください、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>と<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>プロパティ<xref:System.Windows.Controls.ListView>を使用して表示されるコンテンツ、<xref:System.Windows.Controls.GridView>します。 列のコンテンツの配置を指定する、 <xref:System.Windows.Controls.GridView>、定義、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>します。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>同じ表示モードの共有  
 2 つ<xref:System.Windows.Controls.ListView>コントロールは同時に同じ表示モードを共有することはできません。 1 つ以上に同じ表示モードを使用しようとする場合<xref:System.Windows.Controls.ListView>制御、例外が発生します。  
  
 1 つ以上同時に使用できるビュー モードを指定する<xref:System.Windows.Controls.ListView>、テンプレートまたはスタイルを使用します。
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>カスタム表示モードの作成  
 ようにビューをカスタマイズ<xref:System.Windows.Controls.GridView>から派生、<xref:System.Windows.Controls.ViewBase>として表されるデータ項目を表示するためのツールを提供するクラスを抽象化<xref:System.Windows.Controls.ListViewItem>オブジェクト。    
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView の概要](gridview-overview.md)
- [方法トピック](listview-how-to-topics.md)
- [コントロール](../advanced/optimizing-performance-controls.md)

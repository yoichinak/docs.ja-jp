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
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187513"
---
# <a name="listview-overview"></a>ListView の概要
コントロール<xref:System.Windows.Controls.ListView>は、さまざまなレイアウトまたはビューでデータ項目のセットを表示するインフラストラクチャを提供します。 たとえば、ユーザーは、テーブルにデータ項目を表示し、その列を並べ替えできます。  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>ListView とは  
 コントロール<xref:System.Windows.Controls.ListView>は から<xref:System.Windows.Controls.ItemsControl>派生した<xref:System.Windows.Controls.ListBox>コントロールです。 通常、そのアイテムはデータ コレクションのメンバーであり、オブジェクトとして<xref:System.Windows.Controls.ListViewItem>表されます。 A<xref:System.Windows.Controls.ListViewItem>は<xref:System.Windows.Controls.ContentControl>a で、1 つの子要素のみを含むことができます。 ただし、その子要素は、任意のビジュアル要素にできます。  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>ListView の表示モードの定義  
 コントロールのコンテンツの表示モードを<xref:System.Windows.Controls.ListView>指定するには、プロパティを設定します。 <xref:System.Windows.Controls.ListView.View%2A> 提供される[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ビュー モードの<xref:System.Windows.Controls.GridView>1 つは、 カスタマイズ可能な列を持つテーブル内のデータ項目のコレクションを表示します。  
  
 次の例は、従業員情報を<xref:System.Windows.Controls.GridView>表示する<xref:System.Windows.Controls.ListView>コントロールの を定義する方法を示しています。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例でのデータの表示方法を示しています。  
  
 ![グリッドビュー出力を含むリストビューを示すスクリーンショット。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 クラスから継承するクラスを定義することで、カスタム ビュー モードを<xref:System.Windows.Controls.ViewBase>作成できます。 クラス<xref:System.Windows.Controls.ViewBase>は、カスタム ビューを作成するために必要なインフラストラクチャを提供します。 カスタム ビューを作成する方法の詳細については、[ Create a Custom View Mode for a ListView ](how-to-create-a-custom-view-mode-for-a-listview.md)を参照してください。  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>ListView へのデータ バインディング  
 コントロールの<xref:System.Windows.Controls.ItemsControl.Items%2A>項目<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>を指定するには、 および<xref:System.Windows.Controls.ListView>プロパティを使用します。 次の例では、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティを 、`EmployeeInfoDataSource`というデータ コレクションに設定します。  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 では、<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.GridViewColumn>オブジェクトは指定されたデータ フィールドにバインドされます。 プロパティに a を<xref:System.Windows.Controls.GridViewColumn>指定して、オブジェクトをデータ フィールドに<xref:System.Windows.Data.Binding>バインドする<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>例を次に示します。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 列のセルのスタイル<xref:System.Windows.Data.Binding>設定に<xref:System.Windows.DataTemplate>使用する定義の一部として を指定することもできます。 次の例では、<xref:System.Windows.DataTemplate>で識別される を<xref:System.Windows.ResourceKey>設定<xref:System.Windows.Data.Binding>します<xref:System.Windows.Controls.GridViewColumn>。 この例では、 で<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A><xref:System.Windows.DataTemplate>指定されたバインディングがオーバーライドされるため、 は定義されません。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView を実装する ListView のスタイル設定  
 コントロール<xref:System.Windows.Controls.ListView>には、<xref:System.Windows.Controls.ListViewItem>表示されるデータ項目を表すオブジェクトが含まれています。 次のプロパティを使用して、データ項目の内容とスタイルを定義できます。  
  
- コントロールで<xref:System.Windows.Controls.ListView>、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>および プロパティを<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>使用します。  
  
- コントロールで<xref:System.Windows.Controls.ListViewItem>、 および<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティ<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>を使用します。  
  
 のセル間の位置合わせの<xref:System.Windows.Controls.GridView>問題を回避するには、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>を使用して プロパティを設定したり、アイテムの幅に影響<xref:System.Windows.Controls.ListView>を与えるコンテンツを追加したりしないでください。 たとえば、 でプロパティを設定すると、配置の<xref:System.Windows.FrameworkElement.Margin%2A>問題が発生する<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>可能性があります。 のアイテムの幅に影響するプロパティを指定したり、コンテンツを<xref:System.Windows.Controls.GridView>定義したりするには、<xref:System.Windows.Controls.GridView>クラスのプロパティと関連クラス (など<xref:System.Windows.Controls.GridViewColumn>) を使用します。  
  
 使用方法<xref:System.Windows.Controls.GridView>とサポート クラスの詳細については、「 [GridView の概要](gridview-overview.md)」を参照してください。  
  
 <xref:System.Windows.Controls.ListView>コントロール<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A><xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>の を定義し、 も定義する場合は、 が正しく動作するために、スタイルに を含める必要があります。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>  
  
 を使用して表示<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>される<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>コンテンツには<xref:System.Windows.Controls.ListView>、 プロパティと プロパティを<xref:System.Windows.Controls.GridView>使用しないでください。 <xref:System.Windows.Controls.GridView>の列の内容の配置を指定するには、 を定義します<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>同じ表示モードの共有  
 2<xref:System.Windows.Controls.ListView>つのコントロールが同時に同じビュー モードを共有することはできません。 複数の<xref:System.Windows.Controls.ListView>コントロールで同じビュー モードを使用しようとすると、例外が発生します。  
  
 複数の<xref:System.Windows.Controls.ListView>で同時に使用できるビュー モードを指定するには、テンプレートまたはスタイルを使用します。
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>カスタム表示モードの作成  
 カスタマイズされたビューは<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ViewBase>抽象クラスから派生し、オブジェクトとして<xref:System.Windows.Controls.ListViewItem>表されるデータ項目を表示するツールを提供します。
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView の概要](gridview-overview.md)
- [ハウツートピック](listview-how-to-topics.md)
- [コントロール](../advanced/optimizing-performance-controls.md)

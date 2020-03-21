---
title: TreeView の概要
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187380"
---
# <a name="treeview-overview"></a>TreeView の概要
この<xref:System.Windows.Controls.TreeView>コントロールは、折りたたみ可能なノードを使用して階層構造の情報を表示する方法を提供します。 このトピックでは、<xref:System.Windows.Controls.TreeView>コントロール<xref:System.Windows.Controls.TreeViewItem>とコントロールを紹介し、その使用方法の簡単な例を示します。  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>TreeViewとは  
 <xref:System.Windows.Controls.TreeView>は、<xref:System.Windows.Controls.ItemsControl>コントロールを使用<xref:System.Windows.Controls.TreeViewItem>して項目を入れ子にします。 次の例では、<xref:System.Windows.Controls.TreeView>を作成します。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>TreeView の作成  
 コントロール<xref:System.Windows.Controls.TreeView>には、コントロールの階層<xref:System.Windows.Controls.TreeViewItem>が含まれています。 コントロール<xref:System.Windows.Controls.TreeViewItem>は、<xref:System.Windows.Controls.HeaderedItemsControl>および コレクション<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>を持<xref:System.Windows.Controls.ItemsControl.Items%2A>つ コントロールです。  
  
 <xref:System.Windows.Controls.TreeView>を使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]して を定義する場合は、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A><xref:System.Windows.Controls.TreeViewItem>コントロールの内容と、そのコレクションを構成する項目を明示的に定義できます。 前の図では、この方法を示しています。  
  
 また<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>、 をデータ ソースとして指定し、コンテンツを<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>定義<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A><xref:System.Windows.Controls.TreeViewItem>して を指定することもできます。  
  
 コントロールのレイアウトを<xref:System.Windows.Controls.TreeViewItem>定義するには、オブジェクトを使用<xref:System.Windows.HierarchicalDataTemplate>することもできます。 詳細と例については、「[Use SelectedValue, SelectedValuePath, and SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 項目が<xref:System.Windows.Controls.TreeViewItem>コントロールでない場合、コントロールが表示されるときに、<xref:System.Windows.Controls.TreeViewItem>その項目は自動的に<xref:System.Windows.Controls.TreeView>コントロールによって囲まれます。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>TreeViewItem の展開と折りたたみ  
 ユーザーが を展開すると<xref:System.Windows.Controls.TreeViewItem>、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>プロパティは`true`に設定されます。 <xref:System.Windows.Controls.TreeViewItem>また、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>プロパティを (展開) または (折りたたみ) に`true`設定することで、直接`false`ユーザー操作なしで を展開または折りたたみることもできます。 このプロパティが変更されると、<xref:System.Windows.Controls.TreeViewItem.Expanded>または<xref:System.Windows.Controls.TreeViewItem.Collapsed>イベントが発生します。  
  
 メソッドが<xref:System.Windows.FrameworkElement.BringIntoView%2A>コントロールで呼び出されると、<xref:System.Windows.Controls.TreeViewItem>およびその親<xref:System.Windows.Controls.TreeViewItem>コントロールが展開されます。 <xref:System.Windows.Controls.TreeViewItem> が<xref:System.Windows.Controls.TreeViewItem>表示されていない場合、または部分的に表示されていない<xref:System.Windows.Controls.TreeView>場合は、スクロールして表示します。  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem の選択  
 ユーザーがコントロール<xref:System.Windows.Controls.TreeViewItem>をクリックして選択すると、イベントが<xref:System.Windows.Controls.TreeViewItem.Selected>発生し、その<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティが に`true`設定されます。 また<xref:System.Windows.Controls.TreeViewItem>、コントロール<xref:System.Windows.Controls.TreeView.SelectedItem%2A>のもとなります<xref:System.Windows.Controls.TreeView>。 逆<xref:System.Windows.Controls.TreeViewItem>に、コントロールから選択内容が変更されると、その<xref:System.Windows.Controls.TreeViewItem.Unselected>コントロールのイベントが発生<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>し、プロパティが`false`に設定されます。  
  
 コントロール<xref:System.Windows.Controls.TreeView.SelectedItem%2A>の<xref:System.Windows.Controls.TreeView>プロパティは読み取り専用プロパティです。したがって、明示的に設定することはできません。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>ユーザーが<xref:System.Windows.Controls.TreeViewItem>コントロールをクリックした場合、またはコントロールで<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティがに`true`設定されている場合に、プロパティが<xref:System.Windows.Controls.TreeViewItem>設定されます。  
  
 プロパティを<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>使用して、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>の<xref:System.Windows.Controls.TreeView.SelectedItem%2A>を指定します。 詳細については、「[SelectedValue、SelectedValuePath、および SelectedItem を使用する](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 イベントにイベント ハンドラを登録して<xref:System.Windows.Controls.TreeView.SelectedItemChanged>、選択した<xref:System.Windows.Controls.TreeViewItem>変更のタイミングを確認できます。 イベント<xref:System.Windows.RoutedPropertyChangedEventArgs%601>ハンドラに提供される は、前<xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>の選択である 、 と現在の<xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>選択である を指定します。 アプリケーションまたはユーザーが以前または現在の選択を行っていない場合、どちらの値も `null` にできます。  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView のスタイル  
 コントロールの既定のスタイル<xref:System.Windows.Controls.TreeView>は、コントロールを含<xref:System.Windows.Controls.StackPanel>むオブジェクト内に<xref:System.Windows.Controls.ScrollViewer>配置されます。 の<xref:System.Windows.FrameworkElement.Width%2A>プロパティと<xref:System.Windows.FrameworkElement.Height%2A>プロパティを設定すると<xref:System.Windows.Controls.TreeView>、これらの値を使用して、<xref:System.Windows.Controls.StackPanel>を表示するオブジェクト<xref:System.Windows.Controls.TreeView>のサイズが変更されます。 表示するコンテンツが表示領域より大きい場合は、<xref:System.Windows.Controls.ScrollViewer>自動的に表示され、ユーザーがコンテンツを<xref:System.Windows.Controls.TreeView>スクロールできるようになります。  
  
 コントロールの外観を<xref:System.Windows.Controls.TreeViewItem>カスタマイズするには、プロパティを<xref:System.Windows.FrameworkElement.Style%2A>カスタム<xref:System.Windows.Style>に設定します。  
  
 を使用してコントロール<xref:System.Windows.Controls.Control.Foreground%2A>の プロパティ値と<xref:System.Windows.Controls.Control.FontSize%2A>プロパティ値を設定<xref:System.Windows.Controls.TreeViewItem>する方法を次<xref:System.Windows.FrameworkElement.Style%2A>の例に示します。  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>TreeView 項目へのイメージとその他のコンテンツの追加  
 のコンテンツに複数のオブジェクトを<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A><xref:System.Windows.Controls.TreeViewItem>含めることができます。 コンテンツに複数の<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>オブジェクトを含めるには、レイアウト コントロール内でオブジェクトを<xref:System.Windows.Controls.Panel>囲みます。 <xref:System.Windows.Controls.StackPanel>  
  
 a<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のを a<xref:System.Windows.Controls.TreeViewItem>として定義し、<xref:System.Windows.Controls.CheckBox><xref:System.Windows.Controls.TextBlock>両方をコントロールに囲む方法を<xref:System.Windows.Controls.DockPanel>次の例に示します。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 コントロールで囲<xref:System.Windows.DataTemplate>まれている、<xref:System.Windows.Controls.Image>と を含む を<xref:System.Windows.Controls.TextBlock>定義する方法を次<xref:System.Windows.Controls.DockPanel>の例に示します。 を<xref:System.Windows.DataTemplate>使用して、 または<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A><xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>を設定できます<xref:System.Windows.Controls.TreeViewItem>。  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [ハウツートピック](treeview-how-to-topics.md)
- [WPF のコンテンツ モデル](wpf-content-model.md)

---
title: TreeView の概要
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: c0967aa506b087120c776389c2891ec9e0b0b64d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761404"
---
# <a name="treeview-overview"></a>TreeView の概要
<xref:System.Windows.Controls.TreeView>コントロールは、折りたたみ可能なノードを使用して、階層構造で情報を表示する方法を提供します。 このトピックでは、<xref:System.Windows.Controls.TreeView>と<xref:System.Windows.Controls.TreeViewItem>コントロール、およびその使用の単純な例を示します。  

<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>TreeViewとは  
 <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.ItemsControl>を使用して、項目をネストする<xref:System.Windows.Controls.TreeViewItem>コントロール。 次の例では、作成、<xref:System.Windows.Controls.TreeView>します。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>TreeView の作成  
 <xref:System.Windows.Controls.TreeView>コントロールの階層に含まれる<xref:System.Windows.Controls.TreeViewItem>コントロール。 A<xref:System.Windows.Controls.TreeViewItem>コントロールが、<xref:System.Windows.Controls.HeaderedItemsControl>を持つ、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>と<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクション。  
  
 定義する場合、<xref:System.Windows.Controls.TreeView>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、明示的に定義することができます、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のコンテンツを<xref:System.Windows.Controls.TreeViewItem>コントロールとそのコレクションを構成する項目。 前の図では、この方法を示しています。  
  
 指定することも、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>データとしてソースを指定し、<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>と<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>を定義する、<xref:System.Windows.Controls.TreeViewItem>コンテンツ。  
  
 レイアウトを定義する、<xref:System.Windows.Controls.TreeViewItem>コントロールを使用することも<xref:System.Windows.HierarchicalDataTemplate>オブジェクト。 詳細と例については、「[Use SelectedValue, SelectedValuePath, and SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 項目がない場合、<xref:System.Windows.Controls.TreeViewItem>コントロールを自動的に囲まれているが、<xref:System.Windows.Controls.TreeViewItem>タイミングを制御、<xref:System.Windows.Controls.TreeView>コントロールが表示されます。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>TreeViewItem の展開と折りたたみ  
 展開すると、 <xref:System.Windows.Controls.TreeViewItem>、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>プロパティに設定されて`true`します。 展開したり折りたたんだりすることも、<xref:System.Windows.Controls.TreeViewItem>を設定して、ユーザーが直接操作せず、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>プロパティを`true`(展開) または`false`(折りたたみ)。 このプロパティが変更されたときに、<xref:System.Windows.Controls.TreeViewItem.Expanded>または<xref:System.Windows.Controls.TreeViewItem.Collapsed>イベントが発生します。  
  
 ときに、<xref:System.Windows.FrameworkElement.BringIntoView%2A>でメソッドが呼び出される、<xref:System.Windows.Controls.TreeViewItem>コントロール、<xref:System.Windows.Controls.TreeViewItem>とその親<xref:System.Windows.Controls.TreeViewItem>コントロールを展開します。 場合、<xref:System.Windows.Controls.TreeViewItem>が非表示または部分的に表示される、<xref:System.Windows.Controls.TreeView>スクロールして表示します。  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>TreeViewItem の選択  
 ユーザーがクリックすると、<xref:System.Windows.Controls.TreeViewItem>コントロールを選択し、<xref:System.Windows.Controls.TreeViewItem.Selected>イベントが発生し、その<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティに設定されて`true`します。 <xref:System.Windows.Controls.TreeViewItem>にもなります、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>の<xref:System.Windows.Controls.TreeView>コントロール。 選択が変更されたときに逆に、<xref:System.Windows.Controls.TreeViewItem>コントロール、その<xref:System.Windows.Controls.TreeViewItem.Unselected>イベントが発生し、その<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティに設定されて`false`。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティを<xref:System.Windows.Controls.TreeView>コントロールが読み取り専用プロパティ。 そのため、明示的にその設定できません。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティが設定されて、ユーザーがクリックした場合、<xref:System.Windows.Controls.TreeViewItem>コントロール場合や、<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティに設定されて`true`上、<xref:System.Windows.Controls.TreeViewItem>コントロール。  
  
 使用して、<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティを指定する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>の<xref:System.Windows.Controls.TreeView.SelectedItem%2A>します。 詳細については、「[SelectedValue、SelectedValuePath、および SelectedItem を使用する](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 イベント ハンドラーを登録することができます、<xref:System.Windows.Controls.TreeView.SelectedItemChanged>イベントを選択するかを判断するために<xref:System.Windows.Controls.TreeViewItem>変更します。 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>イベントにハンドラーを指定します提供される、 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>、これは、前の選択と<xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>、現在の選択範囲であります。 アプリケーションまたはユーザーが以前または現在の選択を行っていない場合、どちらの値も `null` にできます。  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView のスタイル  
 既定のスタイルを<xref:System.Windows.Controls.TreeView>コントロールの配置内で、<xref:System.Windows.Controls.StackPanel>を含むオブジェクトを<xref:System.Windows.Controls.ScrollViewer>コントロール。 設定すると、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>のプロパティを<xref:System.Windows.Controls.TreeView>、これらの値のサイズを使用して、<xref:System.Windows.Controls.StackPanel>を表示するオブジェクト、 <xref:System.Windows.Controls.TreeView>。 表示するコンテンツが、表示領域より大きい場合、 <xref:System.Windows.Controls.ScrollViewer> 、ユーザーがスクロールするために自動的に表示されます、<xref:System.Windows.Controls.TreeView>コンテンツ。  
  
 外観をカスタマイズする、<xref:System.Windows.Controls.TreeViewItem>設定、制御、<xref:System.Windows.FrameworkElement.Style%2A>プロパティをカスタム<xref:System.Windows.Style>します。  
  
 次の例は、設定する方法を示します、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.FontSize%2A>プロパティの値を<xref:System.Windows.Controls.TreeViewItem>コントロールを使用して、<xref:System.Windows.FrameworkElement.Style%2A>します。  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>TreeView 項目へのイメージとその他のコンテンツの追加  
 内の 1 つ以上のオブジェクトを含めることができます、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のコンテンツを<xref:System.Windows.Controls.TreeViewItem>します。 複数のオブジェクトを含める<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>など、レイアウト コントロール内のオブジェクトを囲む、コンテンツ、<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.StackPanel>します。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>の<xref:System.Windows.Controls.TreeViewItem>として、<xref:System.Windows.Controls.CheckBox>と<xref:System.Windows.Controls.TextBlock>ことの両方がで囲まれた、<xref:System.Windows.Controls.DockPanel>コントロール。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 次の例は、定義する方法を示します、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.Image>と<xref:System.Windows.Controls.TextBlock>で囲まれた、<xref:System.Windows.Controls.DockPanel>コントロール。 使用することができます、<xref:System.Windows.DataTemplate>を設定する、<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>または<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>の<xref:System.Windows.Controls.TreeViewItem>します。  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [方法トピック](treeview-how-to-topics.md)
- [WPF のコンテンツ モデル](wpf-content-model.md)

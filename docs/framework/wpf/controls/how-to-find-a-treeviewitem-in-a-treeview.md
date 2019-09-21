---
title: '方法: TreeView での TreeViewItem の検索'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962090"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>方法: TreeView での TreeViewItem の検索
コントロール<xref:System.Windows.Controls.TreeView>は、階層データを表示する便利な方法を提供します。 がデータソースにバインドされている場合<xref:System.Windows.Controls.TreeView.SelectedItem%2A> 、プロパティは、選択したデータオブジェクトを迅速に取得するための便利な方法を提供します。 <xref:System.Windows.Controls.TreeView> 通常は、基になるデータオブジェクトを操作することをお勧めします。ただし、を含む<xref:System.Windows.Controls.TreeViewItem>データをプログラムで操作することが必要になる場合があります。 たとえば、プログラムを使用して<xref:System.Windows.Controls.TreeViewItem>を展開したり、 <xref:System.Windows.Controls.TreeView>で別の項目を選択したりする必要がある場合があります。  
  
 特定のデータ<xref:System.Windows.Controls.TreeViewItem>オブジェクトを含むを検索するには、 <xref:System.Windows.Controls.TreeView>の各レベルを走査する必要があります。 の項目を仮想<xref:System.Windows.Controls.TreeView>化して、パフォーマンスを向上させることもできます。 項目が仮想化される可能性がある場合は、を<xref:System.Windows.Controls.TreeViewItem>認識してデータオブジェクトが含まれているかどうかを確認する必要もあります。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
 次の例では<xref:System.Windows.Controls.TreeView> 、特定のオブジェクトを検索し、それを<xref:System.Windows.Controls.TreeViewItem>含むオブジェクトを返します。 この例では、 <xref:System.Windows.Controls.TreeViewItem>子項目を検索できるように、各がインスタンス化されていることを確認します。 この例は、が仮想<xref:System.Windows.Controls.TreeView>化された項目を使用しない場合にも機能します。  
  
> [!NOTE]
> 次の例では、 <xref:System.Windows.Controls.TreeView>基になるデータモデルに関係なく、すべての<xref:System.Windows.Controls.TreeViewItem>に対して機能し、オブジェクトが見つかるまではすべて検索します。 パフォーマンスが向上するもう1つの方法は、指定されたオブジェクトのデータモデルを検索し、データ階層内での位置を追跡し<xref:System.Windows.Controls.TreeViewItem> 、 <xref:System.Windows.Controls.TreeView>で対応するを見つけることです。 ただし、パフォーマンスが優れている手法では、データモデルに関する知識が必要であり、 <xref:System.Windows.Controls.TreeView>特定のに対して一般化することはできません。  
  
## <a name="code"></a>コード  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 前のコードは、という<xref:System.Windows.Controls.VirtualizingStackPanel>名前`BringIntoView`のメソッドを公開するカスタムに依存しています。 次のコードは、カスタム<xref:System.Windows.Controls.VirtualizingStackPanel>を定義します。  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 次の XAML は、カスタム<xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.VirtualizingStackPanel>を使用するを作成する方法を示しています。  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>関連項目

- [TreeView のパフォーマンスを改善する](how-to-improve-the-performance-of-a-treeview.md)

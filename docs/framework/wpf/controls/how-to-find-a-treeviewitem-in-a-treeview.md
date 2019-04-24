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
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219045"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>方法: TreeView での TreeViewItem の検索
<xref:System.Windows.Controls.TreeView>コントロールには、階層データを表示する便利な方法が用意されています。 場合、 <xref:System.Windows.Controls.TreeView> 、データ ソースにバインドされて、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティは、選択したデータ オブジェクトを迅速に取得するための便利な方法を提供します。 通常、基になるデータ オブジェクトを使用することをお勧めがデータを格納しているプログラムで操作する必要がありますも<xref:System.Windows.Controls.TreeViewItem>します。 など、プログラムで展開する必要があります、<xref:System.Windows.Controls.TreeViewItem>でさまざまな項目を選択します。 または、<xref:System.Windows.Controls.TreeView>します。  
  
 検索する、<xref:System.Windows.Controls.TreeViewItem>特定のデータ オブジェクトを格納しているの各レベルを走査する必要があります、<xref:System.Windows.Controls.TreeView>します。 内の項目を<xref:System.Windows.Controls.TreeView>パフォーマンスを向上させるために仮想化することもできます。 項目が仮想化の場合、する必要がありますまた、<xref:System.Windows.Controls.TreeViewItem>データ オブジェクトが含まれるかどうかを確認します。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
 次の例で、<xref:System.Windows.Controls.TreeView>の特定のオブジェクトを返しますが、オブジェクトを含む<xref:System.Windows.Controls.TreeViewItem>します。 によって、各例では、<xref:System.Windows.Controls.TreeViewItem>がインスタンス化されるは、その子項目を検索できるようにします。 この例は、場合にも動作、<xref:System.Windows.Controls.TreeView>仮想化された項目を使用しません。  
  
> [!NOTE]
>  次の例のいずれかの動作<xref:System.Windows.Controls.TreeView>、基になるデータ モデルと検索に関係なくすべて<xref:System.Windows.Controls.TreeViewItem>オブジェクトが見つかるまでです。 パフォーマンスが向上するもう 1 つの手法では、指定したオブジェクトのデータ モデルを検索のデータの階層内の場所を追跡し、対応する、検索を<xref:System.Windows.Controls.TreeViewItem>で、<xref:System.Windows.Controls.TreeView>します。 パフォーマンスが向上する手法がデータ モデルの知識が必要ですし、特定の一般化することはできませんただし、<xref:System.Windows.Controls.TreeView>します。  
  
## <a name="code"></a>コード  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 前のコードが依存するカスタム<xref:System.Windows.Controls.VirtualizingStackPanel>という名前のメソッドを公開する`BringIntoView`します。 次のコード定義のカスタム<xref:System.Windows.Controls.VirtualizingStackPanel>します。  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 次の XAML を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>カスタムを使用する<xref:System.Windows.Controls.VirtualizingStackPanel>します。  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>関連項目

- [TreeView のパフォーマンスを改善する](how-to-improve-the-performance-of-a-treeview.md)

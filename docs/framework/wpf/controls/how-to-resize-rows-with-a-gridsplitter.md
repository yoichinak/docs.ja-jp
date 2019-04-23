---
title: '方法: GridSplitter を使用して行のサイズを変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 6760a7a691af4f666294556cae3bc95a4299730a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074275"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>方法: GridSplitter を使用して行のサイズを変更する
この例は、水平方向を使用する方法を示します<xref:System.Windows.Controls.GridSplitter>の 2 つの行の間のスペースを再配分を<xref:System.Windows.Controls.Grid>の寸法を変更せず、<xref:System.Windows.Controls.Grid>します。  
  
## <a name="example"></a>例  
 **行の端に重なって表示される GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>で隣接する行のサイズを変更する、<xref:System.Windows.Controls.Grid>設定、<xref:System.Windows.Controls.Grid.Row%2A>添付プロパティのサイズを変更する行の 1 つをします。 場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の列は、設定、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>添付プロパティを列の数を指定します。 設定し、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に<xref:System.Windows.VerticalAlignment.Top>または<xref:System.Windows.VerticalAlignment.Bottom>(どちらの配置を設定する依存する 2 つの行のサイズを変更する)。 最後に、設定、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Stretch>します。  
  
 次の例は、水平方向を定義する方法を示します<xref:System.Windows.Controls.GridSplitter>隣接する行のサイズを変更します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>独自の行を占有しない他のコントロールに隠される可能性があります、<xref:System.Windows.Controls.Grid>します。 この問題の詳しい回避方法については、[GridSplitter を表示されるようにする](how-to-make-sure-that-a-gridsplitter-is-visible.md)を参照してください。  
  
 **行を占有する GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>内の行を占有する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Row%2A>添付プロパティのサイズを変更する行の 1 つをします。 場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の列は、設定、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>添付プロパティを列の数。 設定し、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に<xref:System.Windows.VerticalAlignment.Center>、設定、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Stretch>、設定と、<xref:System.Windows.Controls.RowDefinition.Height%2A>を含む行の<xref:System.Windows.Controls.GridSplitter>に<xref:System.Windows.GridLength.Auto%2A>。  
  
 次の例は、水平方向を定義する方法を示します<xref:System.Windows.Controls.GridSplitter>を行を占有しのどちら側に行のサイズを変更します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.GridSplitter>
- [方法トピック](gridsplitter-how-to-topics.md)

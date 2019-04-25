---
title: '方法: GridSplitter を使用して列のサイズを変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: f743e9ccf8a984a646a4b8f05ee99162e5bc73ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210439"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>方法: GridSplitter を使用して列のサイズを変更する
この例は、垂直線を作成する方法を示します<xref:System.Windows.Controls.GridSplitter>で 2 つの列間のスペースを再配布するために、<xref:System.Windows.Controls.Grid>の大きさを変更することがなく、<xref:System.Windows.Controls.Grid>します。  
  
## <a name="example"></a>例  
 **列の端に重なって表示される GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>で隣接する列のサイズを変更する、<xref:System.Windows.Controls.Grid>設定、<xref:System.Windows.Controls.Grid.Column%2A>添付プロパティのサイズを変更する列の 1 つをします。 場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の行では、設定、<xref:System.Windows.Controls.Grid.RowSpan%2A>添付プロパティを行の数。 設定し、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Left>または<xref:System.Windows.HorizontalAlignment.Right>(どちらの配置を設定する依存する 2 つの列のサイズを変更する)。 最後に、設定、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.VerticalAlignment.Stretch>します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>独自の列を持たない他のコントロールに隠される可能性があります、<xref:System.Windows.Controls.Grid>します。 この問題の詳しい回避方法については、[GridSplitter を表示されるようにする](how-to-make-sure-that-a-gridsplitter-is-visible.md)を参照してください。  
  
 **列を占有する GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>で列を占有する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Column%2A>添付プロパティのサイズを変更する列の 1 つをします。 グリッドには、複数の行がある場合は、設定、<xref:System.Windows.Controls.Grid.RowSpan%2A>添付プロパティを行の数。 設定し、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>に<xref:System.Windows.HorizontalAlignment.Center>、設定、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.VerticalAlignment.Stretch>、設定と、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>を含む列の<xref:System.Windows.Controls.GridSplitter>に<xref:System.Windows.GridLength.Auto%2A>。  
  
 次の例は、垂直方向を定義する方法を示します<xref:System.Windows.Controls.GridSplitter>列を占有してのいずれかの側の列のサイズを変更します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.GridSplitter>
- [方法トピック](gridsplitter-how-to-topics.md)

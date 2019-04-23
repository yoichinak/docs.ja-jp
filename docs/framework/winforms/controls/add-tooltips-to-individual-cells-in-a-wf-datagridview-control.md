---
title: '方法: Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: 3307c92a13e5730de6dce0fe45b924e44b7af554
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119640"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する
既定では、ツールヒントを使用しての値を表示する<xref:System.Windows.Forms.DataGridView>は小さすぎて全体の内容を表示するセル。 ただし、この動作をオーバーライドする個々 のセルのツールヒントのテキスト値を設定します。 これは、セルに関する追加情報をユーザーに表示する、または他のセルの内容の説明をユーザーに提供するには便利です。 たとえば、状態アイコンを表示する行がある場合は、場合、ツールヒントを使用した説明を提供します。  
  
 セル レベルのツールヒントの表示を無効にすることもできます、<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>プロパティを`false`します。  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>セルにツールヒントを追加するには  
  
-   <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> プロパティを設定します。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   この例で必要な要素は次のとおりです。  
  
-   A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`dataGridView1`という名前の列を格納している`Rating`4 つのアスタリスクを 1 つの文字列値を表示する ("*") 記号です。 <xref:System.Windows.Forms.DataGridView.CellFormatting>例に示すようにイベント ハンドラー メソッドを使用して、コントロールのイベントを関連付ける必要があります。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 バインドすると、<xref:System.Windows.Forms.DataGridView>外部データ ソースへの制御または仮想モードを実装して、独自のデータ ソースを提供する、パフォーマンスの問題が発生する可能性があります。 パフォーマンスの低下を避けるためには、大量のデータを使用する場合、処理、<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>設定ではなく、イベント、<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>複数のセルのプロパティ。 処理するとき、このイベントはセルの値を取得する<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>プロパティは、イベントを発生させるしの値を返します、<xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>プロパティとして指定されたイベントのハンドラー。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](programming-with-cells-rows-and-columns-in-the-datagrid.md)

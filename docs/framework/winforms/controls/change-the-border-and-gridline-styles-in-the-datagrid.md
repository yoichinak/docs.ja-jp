---
title: '方法: Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917672"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する
<xref:System.Windows.Forms.DataGridView>コントロールを使用すると、コントロールの境界線とグリッド線の外観をカスタマイズして、ユーザーエクスペリエンスを向上させることができます。 コントロール内のセルの境界線スタイルに加えて、グリッド線の色とコントロールの境界線スタイルを変更できます。 また、通常のセル、行ヘッダーセル、および列ヘッダーセルに対して異なるセル境界線スタイルを適用することもできます。  
  
> [!NOTE]
> グリッド線の色は<xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>、 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>列挙体<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal> <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>の、、の各値と列挙体の値でのみ使用されます。<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> これらの列挙値の他の値は、オペレーティングシステムによって指定された色を使用します。 さらに、windows XP と windows Server 2003 ファミリ<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>で visual スタイルがメソッド<xref:System.Windows.Forms.DataGridView.GridColor%2A>を使用して有効になっている場合、プロパティ値は使用されません。  
  
### <a name="to-change-the-gridline-color-programmatically"></a>プログラムによってグリッド線の色を変更するには  
  
- <xref:System.Windows.Forms.DataGridView.GridColor%2A> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>DataGridView コントロール全体の境界線スタイルをプログラムで変更するには  
  
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> プロパティを <xref:System.Windows.Forms.BorderStyle> 列挙値のいずれかに設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>DataGridView セルの罫線のスタイルをプログラムで変更するには  
  
- 、 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A> 、<xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>およびの各プロパティを<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、および <xref:System.Drawing?displayProperty=nameWithType> の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)

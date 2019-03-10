---
title: '方法: 罫線と、Windows フォーム DataGridView コントロールでグリッド線のスタイルを変更します。'
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
ms.openlocfilehash: b4984dca6fb7dc8575b00758f0d61d9ff011e1ca
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703369"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>方法: 罫線と、Windows フォーム DataGridView コントロールでグリッド線のスタイルを変更します。
<xref:System.Windows.Forms.DataGridView>コントロール、コントロールの境界線と、ユーザー エクスペリエンスを向上させるためにグリッド線の外観をカスタマイズすることができます。 グリッド線の色とだけでなく、コントロール内のセルの境界線スタイル コントロールの境界線のスタイルを変更することができます。 通常のセル、行のヘッダー セルと列ヘッダー セルの別のセルの境界線スタイルを適用することもできます。  
  
> [!NOTE]
>  グリッド線の色でのみ使用、 <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>、<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>と<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical>の値、<xref:System.Windows.Forms.DataGridViewCellBorderStyle>列挙と<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single>の値、<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>列挙体。 これらの列挙体の他の値は、オペレーティング システムによって指定された色を使用します。 さらに、visual スタイルが有効な場合に、Windows XP およびを通じて Windows Server 2003 ファミリ、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>メソッド、<xref:System.Windows.Forms.DataGridView.GridColor%2A>プロパティの値は使用されません。  
  
### <a name="to-change-the-gridline-color-programmatically"></a>プログラムで枠線の色を変更するには  
  
-   
  <xref:System.Windows.Forms.DataGridView.GridColor%2A> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>全体の DataGridView コントロールの境界線スタイルをプログラムで変更するには  
  
-   
  <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> プロパティを <xref:System.Windows.Forms.BorderStyle> 列挙値のいずれかに設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>DataGridView セルの境界線スタイルをプログラムで変更するには  
  
-   設定、 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>、 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>、および<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>プロパティ。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   
  <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、および <xref:System.Drawing?displayProperty=nameWithType> の各アセンブリへの参照。  
  
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

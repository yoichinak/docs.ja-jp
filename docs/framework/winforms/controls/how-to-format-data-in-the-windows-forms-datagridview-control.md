---
title: '方法: Windows フォーム DataGridView コントロールのデータの書式を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 0f295b44bf1dfffc7f4b6c52b54705bba1d82a81
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609767"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールのデータの書式を設定する
次の手順の説明を使用してセル値の基本的な書式設定、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>のプロパティを<xref:System.Windows.Forms.DataGridView>コントロールとコントロールの特定の列。 高度なデータの書式設定方法の詳細については、次を参照してください。[方法。Windows フォーム DataGridView コントロールでデータの書式設定をカスタマイズ](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)します。  
  
### <a name="to-format-currency-and-date-values"></a>通貨の書式設定および日付値を  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> プロパティを設定します。 次のコード例を使用して特定の列の形式を設定する、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>列のプロパティ。 値、`UnitPrice`列が負の値をかっこで囲まれた現在のカルチャに固有の通貨形式で表示されます。 値、`ShipDate`列が現在のカルチャに固有の短い日付形式で表示されます。 詳細については<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>値を参照してください[型の書式設定](../../../standard/base-types/formatting-types.md)します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>データベースの null 値の表示をカスタマイズするには  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> プロパティを設定します。 次のコード例では、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>プロパティと同じ値を格納しているすべてのセルに「エントリ」を表示する<xref:System.DBNull.Value?displayProperty=nameWithType>します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>セルのテキスト ベースのワード ラップを有効にするには  
  
- 設定、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>のプロパティを<xref:System.Windows.Forms.DataGridViewCellStyle>のいずれかに、<xref:System.Windows.Forms.DataGridViewTriState>列挙値。 次のコード例では、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>コントロール全体のラップ モードを設定するプロパティ。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>DataGridView セルのテキストの配置を指定するには  
  
- 設定、<xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>のプロパティを<xref:System.Windows.Forms.DataGridViewCellStyle>のいずれかに、<xref:System.Windows.Forms.DataGridViewContentAlignment>列挙値。 次のコード例を使用して、特定の列の配置の設定、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>列のプロパティ。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これらの例には次の項目が必要です。  
  
- A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`dataGridView1`という名前の列を格納している`UnitPrice`、という名前の列`ShipDate`、という名前の列と`CustomerName`します。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType>、および <xref:System.Windows.Forms?displayProperty=nameWithType> の各アセンブリへの参照。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 スケーラビリティを最大にするには、共有する必要があります<xref:System.Windows.Forms.DataGridViewCellStyle>全体で複数の行、列、または個別に各要素のスタイル プロパティを設定するのではなく、同じスタイルを使用するセルのオブジェクト。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールを拡張するためのベスト プラクティス](best-practices-for-scaling-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータの書式設定](data-formatting-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでデータの書式設定をカスタマイズします。](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [型の書式設定](../../../standard/base-types/formatting-types.md)

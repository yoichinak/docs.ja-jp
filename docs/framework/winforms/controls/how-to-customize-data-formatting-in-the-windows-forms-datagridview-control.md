---
title: '方法: Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 948e9bf485b42b445491a4da9f8de7ae7974075c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592829"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする
次のコード例は、列と値に応じてセルの表示方法を変更する<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> イベントのハンドラーを実装する方法について説明します。  
  
 負の数値が含まれている `Balance` 列のセルは、赤の背景が指定されます。 これらのセルを通貨として書式設定し、負の値をかっこで囲んで表示することもできます。 詳細については、「[方法 :書式設定データの Windows フォーム DataGridView コントロール](how-to-format-data-in-the-windows-forms-datagridview-control.md)します。  
  
 `Priority` 列のセルは、対応するテキスト セル値の代わりにイメージを表示します。 
  <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> の<xref:System.Windows.Forms.ConvertEventArgs.Value%2A> プロパティはテキストのセル値を取得して、対応するイメージの表示値に設定する場合に使用されます。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
- `highPri.bmp`、`mediumPri.bmp`、および `lowPri.bmp` という名前の <xref:System.Drawing.Bitmap> イメージは、実行可能ファイルと同じディレクトリにあります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [方法: 書式設定データの Windows フォーム DataGridView コントロール](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータの書式設定](data-formatting-in-the-windows-forms-datagridview-control.md)

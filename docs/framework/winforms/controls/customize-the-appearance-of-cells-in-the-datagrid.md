---
title: '方法: Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 415cf18aa4cf01b151a414dbc26609af638a7af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011466"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>方法: Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする
任意のセルの外観をカスタマイズするには処理することによって、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellPainting>イベント。 抽出することができます、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Drawing.Graphics>から、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>します。 この<xref:System.Drawing.Graphics>、全体の外観に影響を及ぼすことができます<xref:System.Windows.Forms.DataGridView>コントロールは通常するには描画されるセルの外観だけに影響します。 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>描画されるセルに、描画操作を制限することができます。  
  
 次のコード例では、すべてのセルを描画します、`ContactName`列を使用して、<xref:System.Windows.Forms.DataGridView>コントロールの色のスキーム。 各セルのテキスト コンテンツが描画される<xref:System.Drawing.Color.Crimson%2A>と同じ色に埋め込みの四角形が描画されると、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.GridColor%2A>プロパティ。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`dataGridView1`で、`ContactName`など、Northwind サンプル データベースの Customers テーブルの列。  
  
- System、System.Windows.Forms、および System.Drawing の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Windows フォーム DataGridView コントロールのカスタマイズ](customizing-the-windows-forms-datagridview-control.md)

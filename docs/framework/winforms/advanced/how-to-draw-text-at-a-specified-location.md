---
title: '方法: テキストを指定の位置に描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: f7834ea45db8dd6e971defd9c3b2b152ffddf512
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336409"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>方法: テキストを指定の位置に描画する
カスタム描画を実行するときに、指定された位置から始まる 1 つの水平方向にテキストを描画できます。 使用して、この方法でテキストを描画することができます、<xref:System.Drawing.Graphics.DrawString%2A>のメソッドをオーバー ロード、<xref:System.Drawing.Graphics>を受け取るクラス、<xref:System.Drawing.Point>または<xref:System.Drawing.PointF>パラメーター。 <xref:System.Drawing.Graphics.DrawString%2A>メソッドも必要になります、<xref:System.Drawing.Brush>と <xref:System.Drawing.Font>  
  
 使用することも、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>のメソッドをオーバー ロード、<xref:System.Windows.Forms.TextRenderer>を受け取る、<xref:System.Drawing.Point>します。 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 必要です、<xref:System.Drawing.Color>と<xref:System.Drawing.Font>します。  
  
 次の図は、使用すると、特定の時点で描画されるテキストの出力、<xref:System.Drawing.Graphics.DrawString%2A>オーバー ロードされたメソッド。  
  
 ![指定した時点でのテキストの出力を示すスクリーン ショット。](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI + でのテキストの線を描画するには  
  
1. 使用して、 <xref:System.Drawing.Graphics.DrawString%2A> 、テキストを渡すメソッド<xref:System.Drawing.Point>または<xref:System.Drawing.PointF>、 <xref:System.Drawing.Font>、および<xref:System.Drawing.Brush>します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI を使用してテキストの線を描画するには  
  
1. 使用して、 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 、テキストを渡すメソッド<xref:System.Drawing.Point>、 <xref:System.Drawing.Font>、および<xref:System.Drawing.Color>します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例が必要です。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`でのパラメーターである<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)
- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: フォント ファミリとフォントを作成します。](how-to-construct-font-families-and-fonts.md)
- [方法: 四角形内にテキストを折り返して描画](how-to-draw-wrapped-text-in-a-rectangle.md)

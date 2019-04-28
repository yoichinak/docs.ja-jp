---
title: '方法: 四角形内にテキストを折り返して描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 8e5c7cab1f977bef0570b2e540d7bf3a630aceb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781405"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>方法: 四角形内にテキストを折り返して描画する
使用して四角形でラップされたテキストを描画することができます、<xref:System.Drawing.Graphics.DrawString%2A>のメソッドをオーバー ロード、<xref:System.Drawing.Graphics>を受け取るクラス、<xref:System.Drawing.Rectangle>または<xref:System.Drawing.RectangleF>パラメーター。 使用することも、<xref:System.Drawing.Brush>と<xref:System.Drawing.Font>します。  
  
 使用して、四角形でラップされたテキストを描画することも、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>のメソッドをオーバー ロード、<xref:System.Windows.Forms.TextRenderer>を受け取る、<xref:System.Drawing.Rectangle>と<xref:System.Windows.Forms.TextFormatFlags>パラメーター。 使用することも、<xref:System.Drawing.Color>と<xref:System.Drawing.Font>します。  
  
 次の図は、使用すると、四角形の描画されるテキストの出力、<xref:System.Drawing.Graphics.DrawString%2A>メソッド。
  
 ![DrawString メソッドを使用する場合は、出力を示すスクリーン ショット。](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>GDI + を使用して四角形内にテキストを折り返して描画するには  
  
1. 使用して、 <xref:System.Drawing.Graphics.DrawString%2A> 、テキストを渡すメソッドをオーバー ロードされた<xref:System.Drawing.Rectangle>または<xref:System.Drawing.RectangleF>、<xref:System.Drawing.Font>と<xref:System.Drawing.Brush>します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>GDI を使用して四角形内にテキストを折り返して描画するには  
  
1. 使用して、<xref:System.Windows.Forms.TextFormatFlags>でテキストを指定する列挙値をラップする必要があります、 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 、テキストを渡すメソッドをオーバー ロードされた<xref:System.Drawing.Rectangle>、<xref:System.Drawing.Font>と<xref:System.Drawing.Color>します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例が必要です。  
  
- <xref:System.Windows.Forms.PaintEventArgs> `e`でのパラメーターである<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)
- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: フォント ファミリとフォントを作成します。](how-to-construct-font-families-and-fonts.md)
- [方法: 指定した位置のテキストの描画](how-to-draw-text-at-a-specified-location.md)

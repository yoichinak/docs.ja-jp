---
title: '方法: 四角形内にテキストを折り返して描画'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 5c4e76cda37527d0167b21c0d206749ba6dab4a9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708861"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>方法: 四角形内にテキストを折り返して描画
使用して四角形でラップされたテキストを描画することができます、<xref:System.Drawing.Graphics.DrawString%2A>のメソッドをオーバー ロード、<xref:System.Drawing.Graphics>を受け取るクラス、<xref:System.Drawing.Rectangle>または<xref:System.Drawing.RectangleF>パラメーター。 使用することも、<xref:System.Drawing.Brush>と<xref:System.Drawing.Font>します。  
  
 使用して、四角形でラップされたテキストを描画することも、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>のメソッドをオーバー ロード、<xref:System.Windows.Forms.TextRenderer>を受け取る、<xref:System.Drawing.Rectangle>と<xref:System.Windows.Forms.TextFormatFlags>パラメーター。 使用することも、<xref:System.Drawing.Color>と<xref:System.Drawing.Font>します。  
  
 次の図は、使用すると、四角形の描画されるテキストの出力、<xref:System.Drawing.Graphics.DrawString%2A>メソッド。  
  
 ![フォント テキスト](./media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>GDI + を使用して四角形内にテキストを折り返して描画するには  
  
1.  使用して、 <xref:System.Drawing.Graphics.DrawString%2A> 、テキストを渡すメソッドをオーバー ロードされた<xref:System.Drawing.Rectangle>または<xref:System.Drawing.RectangleF>、<xref:System.Drawing.Font>と<xref:System.Drawing.Brush>します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>GDI を使用して四角形内にテキストを折り返して描画するには  
  
1.  使用して、<xref:System.Windows.Forms.TextFormatFlags>でテキストを指定する列挙値をラップする必要があります、 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 、テキストを渡すメソッドをオーバー ロードされた<xref:System.Drawing.Rectangle>、<xref:System.Drawing.Font>と<xref:System.Drawing.Color>します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例が必要です。  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`でのパラメーターである<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目
- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)
- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: フォント ファミリとフォントを作成します。](how-to-construct-font-families-and-fonts.md)
- [方法: 指定した位置のテキストの描画](how-to-draw-text-at-a-specified-location.md)

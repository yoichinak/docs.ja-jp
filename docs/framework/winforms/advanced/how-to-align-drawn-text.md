---
title: '方法: 描画するテキストを揃える'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: ab97ab713067af26455fa4261bbddaf900ec91b8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725260"
---
# <a name="how-to-align-drawn-text"></a>方法: 描画するテキストを揃える
カスタム描画を実行するときに、フォームやコントロールを描画するテキストを中央揃えにすることがあります多くの場合。 描画されるテキストを簡単に合わせることができます、<xref:System.Drawing.Graphics.DrawString%2A>または<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドを正しく書式設定オブジェクトを作成し、適切な書式指定フラグを設定します。  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>描画するために、GDI + (DrawString) を使用してテキストを中央揃え  
  
1.  使用して、<xref:System.Drawing.StringFormat>と適切な<xref:System.Drawing.Graphics.DrawString%2A>中央揃えのテキストを指定します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>描画するために、GDI (DrawText) を使用してテキストを中央揃え  
  
1.  使用して、<xref:System.Windows.Forms.TextFormatFlags>列挙体の垂直方向および水平方向には、適切なテキストを中央揃えするほかの折り返し<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッド。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例は、Windows フォームで使用するために設計されていて、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目
- [方法: GDI を使用してテキストを描画します。](how-to-draw-text-with-gdi.md)
- [フォントとテキストの使用](using-fonts-and-text.md)
- [方法: フォント ファミリとフォントを作成します。](how-to-construct-font-families-and-fonts.md)

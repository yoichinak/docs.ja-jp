---
title: '方法: GDI を使用してテキストを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956541"
---
# <a name="how-to-draw-text-with-gdi"></a>方法: GDI を使用してテキストを描画する
<xref:System.Windows.Forms.TextRenderer>クラスの<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドを使用すると、フォームまたはコントロールにテキストを描画するための GDI 機能にアクセスできます。 GDI テキストレンダリングでは、通常、GDI + よりもパフォーマンスが向上し、より正確なテキスト測定が提供されます。  
  
> [!NOTE]
> クラスのメソッドは印刷がサポートされていません。 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> <xref:System.Windows.Forms.TextRenderer> 印刷時には、常<xref:System.Drawing.Graphics.DrawString%2A>に<xref:System.Drawing.Graphics>クラスのメソッドを使用します。  
  
## <a name="example"></a>例  
 次のコード例は、 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドを使用して、四角形内の複数の行にテキストを描画する方法を示しています。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <xref:System.Windows.Forms.TextRenderer>クラスを使用してテキストを表示するに<xref:System.Drawing.IDeviceContext>は、 <xref:System.Drawing.Graphics>と<xref:System.Drawing.Font>などの、テキストを描画する場所、および描画する色を必要とします。 必要に応じて、 <xref:System.Windows.Forms.TextFormatFlags>列挙を使用してテキストの書式を指定することもできます。  
  
 の<xref:System.Drawing.Graphics>取得の詳細については[、「方法:描画](how-to-create-graphics-objects-for-drawing.md)用のグラフィックスオブジェクトを作成します。 の<xref:System.Drawing.Font>構築の詳細については[、「」を参照してください。フォントファミリとフォントを](how-to-construct-font-families-and-fonts.md)構築します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例は、Windows フォームで使用するように設計され<xref:System.Windows.Forms.PaintEventArgs>ており、の<xref:System.Windows.Forms.PaintEventHandler>パラメーターである`e`を必要とします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [フォントとテキストの使用](using-fonts-and-text.md)

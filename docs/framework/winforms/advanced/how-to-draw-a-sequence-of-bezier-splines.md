---
title: '方法: B のシーケンスを描画&#233;ベジエ スプライン'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711793"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>方法: B のシーケンスを描画&#233;ベジエ スプライン
使用することができます、<xref:System.Drawing.Graphics.DrawBeziers%2A>のメソッド、<xref:System.Drawing.Graphics>クラスのシーケンスを描画するためには、ベジエ スプラインを接続します。  
  
## <a name="example"></a>例  
 次の例では、接続された 2 つのベジエ スプラインから成る曲線を描画します。 最初の本のベジエ スプラインのエンドポイントは、2 つ目の本のベジエ スプラインの開始点です。  
  
 次の図は、7 つの点と接続されているスプラインを示します。  
  
 ![ベジエ スプライン](./media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [GDI+ でのベジエ スプライン](bezier-splines-in-gdi.md)
- [曲線の作成と描画](constructing-and-drawing-curves.md)

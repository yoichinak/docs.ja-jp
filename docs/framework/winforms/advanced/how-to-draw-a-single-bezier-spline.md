---
title: '方法: 1 つの B を描画&#233;ベジエ スプライン'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 6fc4e12bb7532019a0571095263b5447e4b0d1ed
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702517"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>方法: 1 つの B を描画&#233;ベジエ スプライン
ベジエ スプラインは、4 つの点によって定義されます。 開始点、2 つの制御点、およびエンドポイント。  
  
## <a name="example"></a>例  
 次の例では、(10, 100) の開始点と終点 (200, 100) を持つベジエ スプラインを描画します。 コントロールは (100, 10) と (150, 150) をポイントします。  
  
 次の図は、その開始点、コントロール ポイント、およびエンドポイントと共に結果として得られる本のベジエ スプラインを示します。 図には、4 つの点を直線で接続することで形成される多角形は、スプラインの凸包も示します。  
  
 ![ベジエ スプライン](./media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [GDI+ でのベジエ スプライン](bezier-splines-in-gdi.md)
- [方法: 一連のベジエ スプラインを描画します。](how-to-draw-a-sequence-of-bezier-splines.md)

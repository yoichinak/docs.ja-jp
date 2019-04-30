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
ms.openlocfilehash: 976787f5830282a581d05a9c24d1f83dceca4b25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004264"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>方法: B のシーケンスを描画&#233;ベジエ スプライン
使用することができます、<xref:System.Drawing.Graphics.DrawBeziers%2A>のメソッド、<xref:System.Drawing.Graphics>クラスのシーケンスを描画するためには、ベジエ スプラインを接続します。  
  
## <a name="example"></a>例  
 次の例では、接続された 2 つのベジエ スプラインから成る曲線を描画します。 最初の本のベジエ スプラインのエンドポイントは、2 つ目の本のベジエ スプラインの開始点です。  
  
 次の図は、7 つの点と接続されているスプラインを示しています。  
  
 ![7 つの点と接続されているスプラインを示しますグラフィック。](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [GDI+ でのベジエ スプライン](bezier-splines-in-gdi.md)
- [曲線の作成と描画](constructing-and-drawing-curves.md)

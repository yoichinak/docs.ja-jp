---
title: '方法: カーディナル スプラインを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 2f03177bf97936a2ca9558972d4d82fa3e07463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703732"
---
# <a name="how-to-draw-cardinal-splines"></a>方法: カーディナル スプラインを描画する
カーディナル スプラインは、指定した点のセットをスムーズに通過する曲線です。 カーディナル スプラインを描画するために作成、<xref:System.Drawing.Graphics>オブジェクトし、へのポインターの配列のアドレスを渡す、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッド。  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>鐘状のカーディナル スプラインを描画  
  
- 次の例では、5 つの指定されたポイントを鐘状のカーディナル スプラインを描画します。 次の図は、曲線と 5 つの点を示します。  
  
     ![鐘状のカーディナル スプラインを示す図。](./media/how-to-draw-cardinal-splines/bell-shaped-cardinal-spline.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>閉じたカーディナル スプラインを描画  
  
- 使用して、<xref:System.Drawing.Graphics.DrawClosedCurve%2A>のメソッド、<xref:System.Drawing.Graphics>閉じたカーディナル スプラインを描画するクラス。 閉じたカーディナル スプラインでは、曲線は配列の最後の点まで続行し、配列内の最初のポイントに接続します。 次の例では、6 つの指定した点、閉じたカーディナル スプラインを描画します。 次の図は、6 つのポイントと共に閉じたスプラインを示しています。  
  
 ![閉じたカーディナル スプラインを示す図。](./media/how-to-draw-cardinal-splines/closed-cardinal-spine.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>カーディナル スプラインの変更  
  
- カーディナル スプラインの湾曲にテンション引数を渡すことによって変える、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッド。 次の例では、同じ点のセットを通過する 3 つのカーディナル スプラインを描画します。 次の図は、3 つのスプラインと張力値を示します。 テンションが 0 の場合は、ポイントが直線でつながれてに注意してください。  
  
 ![次の 3 つのカーディナル スプラインを示す図。](./media/how-to-draw-cardinal-splines/three-cardinal-splines.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記の例は、Windows フォームで使用するために設計されていて、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーター、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目

- [直線、曲線、および図形](lines-curves-and-shapes.md)
- [曲線の作成と描画](constructing-and-drawing-curves.md)

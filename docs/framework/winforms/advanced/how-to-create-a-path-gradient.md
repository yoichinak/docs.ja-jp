---
title: '方法: パス グラデーションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964403"
---
# <a name="how-to-create-a-path-gradient"></a>方法: パス グラデーションを作成する
クラス<xref:System.Drawing.Drawing2D.PathGradientBrush>を使用すると、徐々に変化する色で図形を塗りつぶす方法をカスタマイズできます。 たとえば、パスの中心に色を1つ、パスの境界に別の色を指定できます。 パスの境界に沿って複数のポイントごとに個別の色を指定することもできます。  
  
> [!NOTE]
> Gdi + では、パスは、 <xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトによって維持される直線と曲線のシーケンスです。 GDI + パスの詳細については、「 [GDI + でのグラフィックスのパス](graphics-paths-in-gdi.md)」と「[パスの構築と描画](constructing-and-drawing-paths.md)」を参照してください。  

この記事の例は、コントロールの<xref:System.Windows.Forms.Control.Paint>イベントハンドラーから呼び出されるメソッドです。  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>楕円にパスグラデーションを入力するには  
  
- 次の例では、楕円にパスグラデーションブラシを設定します。 中央の色は青に、境界の色は水色に設定されています。 次の図は、塗りつぶされた楕円を示しています。  
  
     ![グラデーションパスは楕円を塗りつぶします。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     既定では、パスグラデーションブラシはパスの境界の外側では拡張されません。 パスグラデーションブラシを使用して、パスの境界を越える図形を塗りつぶす場合、パスの外側にある画面の領域は塗りつぶされません。  
  
     次の図は、次のコードの<xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType>呼び出しをに変更した場合の動作を`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`示しています。  
  
     ![パスの境界を超えて拡張されたグラデーションパス。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     上記のコード例は、Windows フォームで使用するように設計され<xref:System.Windows.Forms.PaintEventArgs>ています。これは、 <xref:System.Windows.Forms.PaintEventHandler>のパラメーターである e を必要とします。  
  
### <a name="to-specify-points-on-the-boundary"></a>境界上にポイントを指定するには  
  
- 次の例では、星形のパスからパスグラデーションブラシを構築します。 このコードは、 <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>星の重心の色を赤に設定するプロパティを設定します。 次に、コードは<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>プロパティを設定して、 `points`配列内の`colors`個々の点に (配列に格納されている) さまざまな色を指定します。 最後のコードステートメントは、星形のパスをパスグラデーションブラシで塗りつぶします。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- 次の例では、コードにオブジェクト<xref:System.Drawing.Drawing2D.GraphicsPath>を含まないパスグラデーションを描画します。 この例<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>の特定のコンストラクターは、ポイントの配列を受け取りますが、 <xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトは必要ありません。 また、 <xref:System.Drawing.Drawing2D.PathGradientBrush>はパスではなく四角形を塗りつぶすために使用されることに注意してください。 四角形は、ブラシを定義するために使用される閉じたパスよりも大きいため、四角形の一部がブラシによって描画されません。 次の図は、四角形 (点線) と、パスグラデーションブラシによって描画される四角形の部分を示しています。 
  
     ![パスグラデーションブラシで塗りつぶされたグラデーション部分。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>パスのグラデーションをカスタマイズするには  
  
- パスグラデーションブラシをカスタマイズする方法の1つは、 <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>そのプロパティを設定することです。 フォーカススケールは、メインパス内にある内部パスを指定します。 中心の色は、中心点だけではなく、内部パス内のすべての場所に表示されます。  
  
     次の例では、楕円のパスに基づいてパスグラデーションブラシを作成します。 このコードでは、境界の色を青に設定し、中心の色を水色に設定して、パスグラデーションブラシを使用して楕円のパスを塗りつぶします。  
  
     次に、コードはパスグラデーションブラシのフォーカススケールを設定します。 X フォーカススケールが0.3 に設定され、y フォーカススケールが0.8 に設定されています。 このコードは、 <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics>オブジェクトのメソッドを呼び出します。これにより<xref:System.Drawing.Graphics.FillPath%2A> 、への後続の呼び出しによって、最初の楕円の右側にある楕円が塗りつぶされます。  
  
     フォーカススケールの効果を確認するには、中心をメイン楕円と共有する小さな楕円を想像してください。 小さい (内側の) 楕円は、メインの楕円 (中心の中心) を0.3 の係数で水平方向に0.8 の係数で水平方向にスケーリングしたものです。 外側の楕円の境界から内側の楕円の境界に移動すると、色が青から水色に徐々に変化します。 内側の楕円の境界から共有センターに移動すると、色は水色のままになります。  
  
     以下のコードの出力を次の図に示します。 左側の楕円は、中心点でのみ水色です。 右側の楕円は、内側のパスのどこでも水色です。  
  
 ![フォーカススケールのグラデーション効果](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>補間を使用してカスタマイズするには  
  
- パスグラデーションブラシをカスタマイズするもう1つの方法は、補間の色の配列と補間の位置の配列を指定することです。  
  
     次の例では、三角形に基づくパスグラデーションブラシを作成します。 このコードは、 <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>パスグラデーションブラシのプロパティを設定して、補間の色 (濃い緑、水色、青) と補間位置 (0、0.25、1) の配列を指定します。 三角形の境界から中心点に移動すると、色が濃い緑から水色に徐々に変化し、次に水色から青色に変わります。 濃い緑から水色への変更は、濃い緑から青への距離の 25% で行われます。  
  
     次の図は、カスタムパスグラデーションブラシで塗りつぶされた三角形を示しています。  
  
     ![カスタムパスグラデーションブラシで塗りつぶされた三角形。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>中心点を設定するには  
  
- 既定では、パスグラデーションブラシの中心点は、ブラシの構築に使用されるパスの重心にあります。 中心点の位置を変更するには、 <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> <xref:System.Drawing.Drawing2D.PathGradientBrush>クラスのプロパティを設定します。  
  
     次の例では、楕円に基づくパスグラデーションブラシを作成します。 楕円の中心は (70, 35) ですが、パスグラデーションブラシの中心点は (120, 40) に設定されています。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     次の図は、塗りつぶされた楕円とパスグラデーションブラシの中心点を示しています。  
  
     ![塗りつぶされた楕円と中心点を含むグラデーションパス。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- パスグラデーションブラシの中心点を、ブラシの作成に使用されたパスの外側の位置に設定できます。 次の例では、呼び出しを置き換え<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>て、前のコードでプロパティを設定します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     次の図は、この変更による出力を示しています。  
  
     ![パスの外側の中心点を持つグラデーションパス。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     前の図では、楕円の右端にある点は純粋な青ではありません (ただし、非常に閉じています)。 グラデーションの色は、塗りつぶしがポイント (145, 35) に達した場合と同じように配置されます。この場合、色は純粋な青 (0, 0, 255) になります。 ただし、パスグラデーションブラシはパス内でのみ描画されるため、塗りつぶしは (145, 35) に到達しません。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するように設計さ<xref:System.Windows.Forms.PaintEventArgs>れており、 <xref:System.Windows.Forms.Control.Paint>イベントハンドラーのパラメーターであるを必要`e`とします。  
  
## <a name="see-also"></a>関連項目

- [グラデーション ブラシを使用した図形の塗りつぶし](using-a-gradient-brush-to-fill-shapes.md)

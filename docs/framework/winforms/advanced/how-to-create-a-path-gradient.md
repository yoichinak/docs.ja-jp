---
title: '方法: パス グラデーションを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: cbbffa7b9250c5e489a95f687ea58eaf2a08d1bf
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126228"
---
# <a name="how-to-create-a-path-gradient"></a>方法: パス グラデーションを作成します。
<xref:System.Drawing.Drawing2D.PathGradientBrush>クラスでは、徐々 に変化する色に図形を塗りつぶす方法をカスタマイズできます。 たとえば、パスの中央の 1 つの色とパスの境界に別の色を指定できます。 各パスの境界に沿って複数ポイントの別の色を指定することもできます。  
  
> [!NOTE]
>  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、パスは、一連の直線と曲線によって管理される、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。 詳細については[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]パスを参照してください[GDI + でのグラフィックス パス](graphics-paths-in-gdi.md)と[描画パスの作成および](constructing-and-drawing-paths.md)します。  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>パス グラデーションを使用して楕円の塗りつぶしを  
  
-   次の例では、パスのグラデーション ブラシを使用して楕円を塗りつぶします。 中心の色を青に設定し、境界の色を水色に設定します。 次の図は、塗りつぶされた楕円を示します。  
  
     ![グラデーション パスでは、楕円を塗りつぶします。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     既定では、パスのグラデーション ブラシは、パスの境界の外側には拡張されません。 パスの境界を越える図形を塗りつぶすパス グラデーション ブラシを使用する場合、パスの外側の画面の領域は埋められません。  
  
     変更する場合、次の図は、<xref:System.Drawing.Graphics.FillEllipse%2A>で次のコードを呼び出す`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`:  
  
     ![グラデーション パス、パスの境界を超えて拡張します。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     上記のコード例が、Windows フォームで使用するために設計されており、必要があります、 <xref:System.Windows.Forms.PaintEventArgs> e で、パラメーターの<xref:System.Windows.Forms.PaintEventHandler>します。  
  
### <a name="to-specify-points-on-the-boundary"></a>境界でポイントを指定するには  
  
-   次の例では、星型のパスからのパスのグラデーション ブラシを作成します。 コードのセット、<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>プロパティで、赤色の星の重心で色を設定します。 コード セットし、<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>さまざまな色を指定するプロパティ (に格納されている、`colors`配列) の個々 のポイントで、`points`配列。 最後のコード ステートメントは、パスのグラデーション ブラシで星型のパスを設定します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   次の例では、描画せずパス グラデーションを<xref:System.Drawing.Drawing2D.GraphicsPath>コード内のオブジェクト。 特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>コンス トラクターの例では、点の配列を受け取りますは必要ありません、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。 また、<xref:System.Drawing.Drawing2D.PathGradientBrush>パスではなく、四角形の塗りつぶしに使用します。 四角形は四角形の一部は、ブラシによって描画されませんので、ブラシを定義するために使用する閉じたパスを超えています。 次の図は、(点線) 四角形とパスのグラデーション ブラシで塗りつぶされた四角形の部分を示しています。 
  
     ![パス グラデーション ブラシで描画されたグラデーション部分です。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>パス グラデーションをカスタマイズするには  
  
-   パス グラデーション ブラシをカスタマイズする方法の 1 つを設定するのにはその<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>プロパティ。 フォーカスのスケールでは、メインのパスの内側にある内部のパスを指定します。 中心点だけでなく、その内部のパス内で、すべての場所で中心の色が表示されます。  
  
     次の例では、楕円のパスに基づくパス グラデーション ブラシを作成します。 コードは、境界の色を青に設定を水色に中心の色を設定し、パス グラデーション ブラシを使用して、楕円のモーション パスを入力します。  
  
     次に、コードは、パスのグラデーション ブラシのフォーカスのスケールを設定します。 X フォーカス スケールは、0.3 に設定され、y のフォーカスのスケールが 0.8 に設定されます。 コードの呼び出し、<xref:System.Drawing.Graphics.TranslateTransform%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクトように後続の呼び出し<xref:System.Drawing.Graphics.FillPath%2A>最初の楕円の右側に配置される楕円を塗りつぶします。  
  
     フォーカスのスケールの効果を表示するには、メインの楕円の中心を共有する小さな楕円を想像してください。 小規模 (内部) 楕円は、メインの楕円の 0.3 の係数を使用して、垂直方向に 0.8 の係数 (の中心) 水平方向に拡張です。 内側の楕円の境界線の外側の楕円の境界から移動すると、色が徐々 に変化青からを水色にします。 内部の楕円の境界を水色、色は、共有のセンターに移動します。  
  
     以下のコードの出力を次の図に示します。 左側の楕円は、中心点にのみ aqua です。 右側の楕円は、内部のパス内ですべての場所で aqua です。  
  
 ![フォーカスの規模のグラデーション効果](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>補間でカスタマイズするには  
  
-   パス グラデーション ブラシをカスタマイズする別の方法では、補間の色の配列と、補間の位置の配列を指定します。  
  
     次の例では、三角形に基づくパス グラデーション ブラシを作成します。 コードのセット、<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>補間の色 (濃い緑、aqua、青) の配列と、補間の位置 (0, 0.25, 1) の配列を指定するパスのグラデーション ブラシのプロパティ。 中心点にある三角形の境界から移動すると、色が徐々 に変化濃い緑からを水色に、青に aqua から。 濃い緑から青からの距離の 25% でを水色に濃い緑から変更が行われます。  
  
     次の図は、カスタム パスのグラデーション ブラシで塗りつぶした三角形を示します。  
  
     ![三角形は、カスタム パス グラデーション ブラシで塗りつぶされます。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>中心点を設定するには  
  
-   既定では、パスのグラデーション ブラシの中心点は、ブラシを作成するために使用するパスの重心では。 中心点の位置を設定して変更することができます、<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>のプロパティ、<xref:System.Drawing.Drawing2D.PathGradientBrush>クラス。  
  
     次の例では、楕円に基づくパス グラデーション ブラシを作成します。 楕円の中心 (70、35) に設定されているパスのグラデーション ブラシの中心点が (120, 40)。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     次の図は、塗りつぶされた楕円とパスのグラデーション ブラシの中心点を示しています。  
  
     ![塗りつぶされた楕円と center ポイントとグラデーションのパス。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
-   パス グラデーション ブラシの中心点は、ブラシを作成するために使用されたパスの外部の場所に設定できます。 次の例では、置換を設定する呼び出し、<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>上記のコードでのプロパティ。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     次の図は、この変更により、出力を示しています。  
  
     ![パスの外側の中心点でグラデーションのパス。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     前の図では、楕円の右端にある点のない純粋な青 (ただし、これらはよく似ています)。 グラデーションの色は、塗りつぶし色が純粋な青 (0, 0, 255) をすると、点 (145, 35) に達するかのように配置されます。 塗りつぶしに決して到達しませんが、(145, 35) ため、そのパス内でのみパス グラデーション ブラシを描画します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記の例は、Windows フォームで使用するために設計されていて、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーター、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目
- [グラデーション ブラシを使用した図形の塗りつぶし](using-a-gradient-brush-to-fill-shapes.md)

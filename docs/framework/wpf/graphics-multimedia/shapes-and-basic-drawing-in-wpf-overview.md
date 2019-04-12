---
title: WPF での図形と基本描画の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 1ce0e661d88b7c4d5719c4f11ef0912c5bacb587
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189134"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF での図形と基本描画の概要
このトピックを使用して描画する方法の概要を示します<xref:System.Windows.Shapes.Shape>オブジェクト。 A<xref:System.Windows.Shapes.Shape>の種類は、<xref:System.Windows.UIElement>画面に図形を描画することができます。 UI 要素であるため<xref:System.Windows.Shapes.Shape>オブジェクトは内で使用できる<xref:System.Windows.Controls.Panel>要素とほとんどのコントロール。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] グラフィックスとレンダリング サービスへのアクセスの複数のレイヤーを提供します。 最上位のレイヤー<xref:System.Windows.Shapes.Shape>オブジェクトは、簡単に使用し、レイアウトへの参加など、多くの便利な機能を提供、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]イベント システム。  

<a name="shapes"></a>   
## <a name="shape-objects"></a>図形オブジェクト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] すぐに使用できるさまざまな<xref:System.Windows.Shapes.Shape>オブジェクト。  すべての図形オブジェクトの継承、<xref:System.Windows.Shapes.Shape>クラス。 使用可能な図形オブジェクトには、 <xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、および<xref:System.Windows.Shapes.Rectangle>します。 <xref:System.Windows.Shapes.Shape> オブジェクトは、次の一般的なプロパティを共有します。  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>:図形のアウトラインを描画する方法について説明します。  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>:図形のアウトラインの太さについて説明します。  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>:図形の内部を描画する方法について説明します。  
  
-   デバイス非依存ピクセル単位で計測される座標と頂点を指定するデータ プロパティ。  
  
 派生するため<xref:System.Windows.UIElement>、図形オブジェクトは、パネルおよびほとんどのコントロール内で使用できます。 <xref:System.Windows.Controls.Canvas>パネルはその子オブジェクトの絶対配置をサポートするため、複雑な描画の作成に特に適しています。  
  
 <xref:System.Windows.Shapes.Line>クラスでは、2 点を結ぶ線を描画することができます。 直線の座標およびストローク プロパティを指定するいくつかの方法を次の例に示します。  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Line>します。  
  
 ![線の図](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 ですが、<xref:System.Windows.Shapes.Line>クラスは、提供、<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティを設定することも何も起こりませんため、<xref:System.Windows.Shapes.Line>領域がありません。  
  
 もう 1 つの一般的な図形は、<xref:System.Windows.Shapes.Ellipse>します。  作成、<xref:System.Windows.Shapes.Ellipse>図形を定義することで<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ。 円を描画するには指定、<xref:System.Windows.Shapes.Ellipse>が<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>値が等しい。  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 次の図は、レンダリングの例を示します<xref:System.Windows.Shapes.Ellipse>します。  
  
 ![楕円の図](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>パスとジオメトリの使用  
 <xref:System.Windows.Shapes.Path>クラスでは、曲線および複雑な図形を描画することができます。 これらの曲線および図形を使用して記述<xref:System.Windows.Media.Geometry>オブジェクト。 使用する、 <xref:System.Windows.Shapes.Path>、作成する、<xref:System.Windows.Media.Geometry>に設定して、<xref:System.Windows.Shapes.Path>オブジェクトの<xref:System.Windows.Shapes.Path.Data%2A>プロパティ。  
  
 さまざまな<xref:System.Windows.Media.Geometry>から選択するオブジェクト。 <xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.RectangleGeometry>、および<xref:System.Windows.Media.EllipseGeometry>クラスは、比較的単純な図形をについて説明します。 複雑な図形を作成または曲線を作成、使用して、<xref:System.Windows.Media.PathGeometry>します。  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry と PathSegment  
 <xref:System.Windows.Media.PathGeometry> オブジェクトは、1 つまたは複数の構成要素は<xref:System.Windows.Media.PathFigure>オブジェクト。 各<xref:System.Windows.Media.PathFigure>異なる"図"または図形を表します。 各<xref:System.Windows.Media.PathFigure>自体は 1 つ以上ので構成されます<xref:System.Windows.Media.PathSegment>それぞれ図や図形の接続されている部分を表すオブジェクトします。 セグメントの種類は、次を含める: <xref:System.Windows.Media.LineSegment>、 <xref:System.Windows.Media.BezierSegment>、および<xref:System.Windows.Media.ArcSegment>します。  
  
 次の例では、 <xref:System.Windows.Shapes.Path> 2 次ベジエ曲線の描画に使用します。  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 レンダリングされた図形を次の図に示します。  
  
 ![パスの図](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 詳細については<xref:System.Windows.Media.PathGeometry>およびその他、<xref:System.Windows.Media.Geometry>クラスを参照してください、[ジオメトリの概要](geometry-overview.md)します。  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>省略された XAML 構文  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、記述する特別な省略構文を使用することも、<xref:System.Windows.Shapes.Path>します。 次の例では、省略された構文を使用して複雑な図形を描画します。  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Path>します。  
  
 ![パスの図](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>属性文字列の先頭の座標システムで、パスの開始点を確立、M で示される"moveto"コマンドが、<xref:System.Windows.Controls.Canvas>します。 <xref:System.Windows.Shapes.Path> データのパラメーターは大文字小文字を区別します。 大文字の M では、現在の新しい点の絶対位置を示します。 小文字の m は、相対座標を示します。 最初のセグメントは、2 つの制御点 (100,25) と (400,350) を使用して描画される、始点が (100,200) で終点が (400,175) の 3 次ベジエ曲線です。 このセグメントは、C のコマンドで示される、<xref:System.Windows.Shapes.Path.Data%2A>属性の文字列。 ここでも、大文字の C は絶対パスを示し、小文字の c は相対パスを示します。  
  
 2 番目のセグメントは、絶対水平 "lineto" コマンド H で始まります。このコマンドは、前のサブパスの終点 (400,175) から新しい終点 (280,175) まで描画される直線を指定します。 指定された値は、水平"lineto"コマンドであるため、 *x*-を調整します。  
  
 完全なパスの構文を参照してください、<xref:System.Windows.Shapes.Path.Data%2A>参照と[PathGeometry を使用して図形を作成](how-to-create-a-shape-by-using-a-pathgeometry.md)です。  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>図形の塗りつぶし  
 <xref:System.Windows.Media.Brush> オブジェクトが図形の描画に使用される<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.Fill%2A>します。 次の例、ストロークおよび塗りつぶしの<xref:System.Windows.Shapes.Ellipse>が指定されています。 ブラシ プロパティの有効な入力は、キーワードまたは 16 進数のカラー値のいずれかです。 使用可能なカラー キーワードの詳細については、のプロパティを参照してください、<xref:System.Windows.Media.Colors>クラス、<xref:System.Windows.Media>名前空間。  
  
```xaml
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Ellipse>します。  
  
 ![楕円](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 または、プロパティ要素構文を使用して明示的に作成することができます、<xref:System.Windows.Media.SolidColorBrush>純色で図形を描画するオブジェクト。  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 レンダリングされた図形を次の図に示します。  
  
 ![SolidColorBrush の図](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 図形のストロークまたは塗りつぶしをグラデーション、イメージ、パターンなどで塗りつぶすこともできます。 詳細については、次を参照してください。、[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)します。  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>伸縮可能な図形  
 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、および<xref:System.Windows.Shapes.Rectangle>クラスがすべて、<xref:System.Windows.Shapes.Shape.Stretch%2A>プロパティ。 このプロパティを決定する方法、<xref:System.Windows.Shapes.Shape>オブジェクトのコンテンツ (描画される図形) がいっぱいに拡大されます、<xref:System.Windows.Shapes.Shape>オブジェクトのレイアウト空間。 A<xref:System.Windows.Shapes.Shape>オブジェクトのレイアウト空間は、領域の量、<xref:System.Windows.Shapes.Shape>が割り当てられる、レイアウト システムでは、いずれかが原因、明示的な<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>設定のため、またはその<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>設定します。 Windows Presentation Foundation でのレイアウトの詳細については、次を参照してください。[レイアウト](../advanced/layout.md)の概要。  
  
 プロパティには、次のいずれかの値を指定します。  
  
-   <xref:System.Windows.Media.Stretch.None>:<xref:System.Windows.Shapes.Shape>オブジェクトのコンテンツは引き伸ばされません。  
  
-   <xref:System.Windows.Media.Stretch.Fill>:<xref:System.Windows.Shapes.Shape>レイアウト空間を入力するオブジェクトのコンテンツは引き伸ばされます。  縦横比は維持されません。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>:<xref:System.Windows.Shapes.Shape>オブジェクトのコンテンツは元の縦横比を維持しながら、レイアウト空間を入力する可能な限り引き伸ばされます。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>:<xref:System.Windows.Shapes.Shape>オブジェクトの内容は、元の縦横比を維持しながら、レイアウト空間を完全に埋めるに引き伸ばされます。  
  
 なお、ときに、<xref:System.Windows.Shapes.Shape>オブジェクトのコンテンツを引き伸ばす、<xref:System.Windows.Shapes.Shape>拡大した後はオブジェクトのアウトラインを描画します。  
  
 次の例では、 <xref:System.Windows.Shapes.Polygon> (1, 1) に (0, 1) に (0, 0) から非常に小さな三角形の描画に使用します。 <xref:System.Windows.Shapes.Polygon>オブジェクトの<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>が 100 に設定し、その stretch プロパティを Fill に設定されます。 結果として、<xref:System.Windows.Shapes.Polygon>オブジェクトのコンテンツ (三角形) は拡大のスペースを埋めるに引き伸ばされます。  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a>図形の変換  
 <xref:System.Windows.Media.Transform>クラスには、2 次元平面内の図形を変換するための手段が用意されています。  変換のさまざまな種類は、回転 (<xref:System.Windows.Media.RotateTransform>)、スケール (<xref:System.Windows.Media.ScaleTransform>)、傾斜 (<xref:System.Windows.Media.SkewTransform>)、および翻訳 (<xref:System.Windows.Media.TranslateTransform>)。  
  
 図形に適用される一般的な変換は回転です。  図形を回転するには、作成、<xref:System.Windows.Media.RotateTransform>指定とその<xref:System.Windows.Media.RotateTransform.Angle%2A>します。 <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 の要素を 45 度回転角度が 90 の要素を 90 度回転; まで、時計回り時計回りします。 設定、<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティ要素を回転、位置を制御する場合。 これらのプロパティ値は、変換する要素の座標空間で表します。 <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0 の既定値を指定します。 最後に、適用、<xref:System.Windows.Media.RotateTransform>要素にします。 レイアウトに影響する変換しない場合は、設定、図形の<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>図形の左上隅 (0, 0) の図形を 45 度回転するために使用します。  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 次の例では、別の図形を 45 度回転していますが、この場合は (25,50) が回転の中心です。  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 上記 2 つの変換を適用すると、結果は次の図のようになります。  
  
 ![中心点が異なる 45 度の回転](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 前の例では、単一の変換を各図形オブジェクトに適用しました。 図形 (またはその他の UI 要素) には、複数の変換を適用するには、使用、<xref:System.Windows.Media.TransformGroup>します。  
  
## <a name="see-also"></a>関連項目

- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [ジオメトリの概要](geometry-overview.md)
- [チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [アニメーションの概要](animation-overview.md)

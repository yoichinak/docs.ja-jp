---
title: 図形と基本的な図面の概要
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
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141329"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF での図形と基本描画の概要
このトピックでは、<xref:System.Windows.Shapes.Shape>オブジェクトを使用して描画する方法の概要を説明します。 A<xref:System.Windows.Shapes.Shape>は、画面<xref:System.Windows.UIElement>に図形を描画できるタイプの 1 です。 これらは UI 要素であるため<xref:System.Windows.Shapes.Shape>、オブジェクトは要素と<xref:System.Windows.Controls.Panel>ほとんどのコントロールの内部で使用できます。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、グラフィックス サービスやレンダリング サービスへのアクセスのレイヤーがいくつか用意されています。 最上層では、<xref:System.Windows.Shapes.Shape>オブジェクトは使いやすく、レイアウトやイベントシステムへの参加など、多くの便利な[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]機能を提供します。  

<a name="shapes"></a>
## <a name="shape-objects"></a>図形オブジェクト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、すぐに使用<xref:System.Windows.Shapes.Shape>できるオブジェクトが多数用意されています。  すべてのシェイプ オブジェクトはクラス<xref:System.Windows.Shapes.Shape>から継承されます。 使用可能な図形オブジェクト<xref:System.Windows.Shapes.Ellipse>には<xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、 <xref:System.Windows.Shapes.Rectangle>、 、 、 などがあります。 <xref:System.Windows.Shapes.Shape>オブジェクトは、次の共通プロパティを共有します。  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: 図形のアウトラインの描画方法を説明します。  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: 図形のアウトラインの太さを示します。  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: 図形の内部の描画方法を説明します。  
  
- デバイス非依存ピクセル単位で計測される座標と頂点を指定するデータ プロパティ。  
  
 シェイプ オブジェクトは<xref:System.Windows.UIElement>から派生するため、パネルやほとんどのコントロールの内部でシェイプ オブジェクトを使用できます。 この<xref:System.Windows.Controls.Canvas>パネルは、子オブジェクトの絶対配置をサポートするため、複雑な図面を作成する場合に特に適しています。  
  
 この<xref:System.Windows.Shapes.Line>クラスでは、2 点間に線を引くことができます。 直線の座標およびストローク プロパティを指定するいくつかの方法を次の例に示します。  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 次の図は、レンダリング<xref:System.Windows.Shapes.Line>された .  
  
 ![線の図](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 クラスは<xref:System.Windows.Shapes.Line>プロパティを<xref:System.Windows.Shapes.Shape.Fill%2A>提供しますが、a には<xref:System.Windows.Shapes.Line>エリアがないため、設定しても効果はありません。  
  
 もう 1 つの<xref:System.Windows.Shapes.Ellipse>一般的なシェイプは、 です。  図形<xref:System.Windows.Shapes.Ellipse><xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティを定義して を作成します。 円を描画するには、値が<xref:System.Windows.Shapes.Ellipse>等<xref:System.Windows.FrameworkElement.Width%2A>しい<xref:System.Windows.FrameworkElement.Height%2A>値を持つ値を指定します。  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Ellipse>.  
  
 ![楕円の図](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>パスとジオメトリの使用  
 この<xref:System.Windows.Shapes.Path>クラスでは、曲線や複雑なシェイプを描画できます。 これらの曲線とシェイプは、オブジェクト<xref:System.Windows.Media.Geometry>を使用して記述されます。 <xref:System.Windows.Shapes.Path>を使用するには、 を<xref:System.Windows.Media.Geometry>作成し、それを使用してオブジェクト<xref:System.Windows.Shapes.Path>の<xref:System.Windows.Shapes.Path.Data%2A>プロパティを設定します。  
  
 選択できる<xref:System.Windows.Media.Geometry>オブジェクトはさまざまです。 クラス<xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>、 <xref:System.Windows.Media.EllipseGeometry> 、および クラスは比較的単純なシェイプを記述します。 より複雑なシェイプを作成したり、曲線を作成<xref:System.Windows.Media.PathGeometry>したりするには、 を使用します。  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry と PathSegment  
 <xref:System.Windows.Media.PathGeometry>オブジェクトは 1 つ以上<xref:System.Windows.Media.PathFigure>のオブジェクトで構成されます。それぞれが<xref:System.Windows.Media.PathFigure>異なる「図」または形状を表します。 各<xref:System.Windows.Media.PathFigure>オブジェクト自体は 1 つ以上<xref:System.Windows.Media.PathSegment>のオブジェクトで構成され、それぞれが図形または図形の接続部分を表します。 セグメントの種類には<xref:System.Windows.Media.LineSegment>、 、 <xref:System.Windows.Media.BezierSegment>、<xref:System.Windows.Media.ArcSegment>および が含まれます。  
  
 次の例では、a<xref:System.Windows.Shapes.Path>を使用して 2 次ベジエ曲線を描画しています。  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 レンダリングされた図形を次の図に示します。  
  
 ![パスの図](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 その他<xref:System.Windows.Media.Geometry>のクラス<xref:System.Windows.Media.PathGeometry>の詳細については、「[ジオメトリの概要](geometry-overview.md)」を参照してください。  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>省略された XAML 構文  
 では[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 の説明に特別な省略構文を<xref:System.Windows.Shapes.Path>使用することもできます。 次の例では、省略された構文を使用して複雑な図形を描画します。  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 次の図は、レンダリング<xref:System.Windows.Shapes.Path>された .  
  
 ![パスの図](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 属性<xref:System.Windows.Shapes.Path.Data%2A>文字列は、M で示される "moveto" コマンドで始まり、このコマンドは、パスの始点をの座標系<xref:System.Windows.Controls.Canvas>に設定します。 <xref:System.Windows.Shapes.Path>データ パラメーターでは大文字と小文字が区別されます。 大文字 M は、新しい現在のポイントの絶対位置を示します。 小文字の m は、相対座標を示します。 最初のセグメントは、2 つの制御点 (100,25) と (400,350) を使用して描画される、始点が (100,200) で終点が (400,175) の 3 次ベジエ曲線です。 このセグメントは、<xref:System.Windows.Shapes.Path.Data%2A>属性ストリングの C コマンドによって示されます。 ここでも、大文字の C は絶対パスを示し、小文字の c は相対パスを示します。  
  
 2 番目のセグメントは、絶対水平 "lineto" コマンド H で始まります。このコマンドは、前のサブパスの終点 (400,175) から新しい終点 (280,175) まで描画される直線を指定します。 水平の "lineto" コマンドなので、指定された値は*x*座標です。  
  
 完全なパス構文については、<xref:System.Windows.Shapes.Path.Data%2A>参照および[PathGeometry を使用してシェイプを作成するを](how-to-create-a-shape-by-using-a-pathgeometry.md)参照してください。  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>図形の塗りつぶし  
 <xref:System.Windows.Media.Brush>オブジェクトは、図形<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.Fill%2A>のをペイントするために使用されます。 次の例では、線と塗りの塗<xref:System.Windows.Shapes.Ellipse>りが指定されています。 ブラシ プロパティの有効な入力は、キーワードまたは 16 進数のカラー値のいずれかです。 使用可能な色キーワードの詳細については、名前空間のクラスのプロパティ<xref:System.Windows.Media.Colors>を<xref:System.Windows.Media>参照してください。  
  
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
  
 次の図は、レンダリング<xref:System.Windows.Shapes.Ellipse>された .  
  
 ![楕円](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 または、プロパティ要素構文を使用して、オブジェクトを<xref:System.Windows.Media.SolidColorBrush>明示的に作成して、図形を単色で描画することもできます。  
  
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
  
 図形のストロークまたは塗りつぶしをグラデーション、イメージ、パターンなどで塗りつぶすこともできます。 詳細については、「[単色とグラデーションによるペイントの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>伸縮可能な図形  
 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>、、<xref:System.Windows.Shapes.Rectangle>および クラスには<xref:System.Windows.Shapes.Shape.Stretch%2A>、すべてプロパティがあります。 このプロパティは、<xref:System.Windows.Shapes.Shape>オブジェクトの内容 (描画する図形) を<xref:System.Windows.Shapes.Shape>オブジェクトのレイアウト空間に広げるためにどのように拡大するかを決定します。 <xref:System.Windows.Shapes.Shape>オブジェクトのレイアウト空間は、<xref:System.Windows.Shapes.Shape>明示的<xref:System.Windows.FrameworkElement.Width%2A>な設定と<xref:System.Windows.FrameworkElement.Height%2A>設定、またはレイアウトシステムと設定により、レイアウト システムによって割り当てられるスペースの<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A><xref:System.Windows.FrameworkElement.VerticalAlignment%2A>量です。 Windows プレゼンテーションの基礎のレイアウトの詳細については、「[レイアウト](../advanced/layout.md)の概要」を参照してください。  
  
 プロパティには、次のいずれかの値を指定します。  
  
- <xref:System.Windows.Media.Stretch.None>:<xref:System.Windows.Shapes.Shape>オブジェクトの内容は引き伸ばされていません。  
  
- <xref:System.Windows.Media.Stretch.Fill>:<xref:System.Windows.Shapes.Shape>オブジェクトの内容は、レイアウト空間に収めるために引き伸ばされます。  縦横比は維持されません。  
  
- <xref:System.Windows.Media.Stretch.Uniform>:<xref:System.Windows.Shapes.Shape>オブジェクトの内容は、元の縦横比を維持したまま、レイアウト空間を埋めるために可能な限り伸長されます。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>:<xref:System.Windows.Shapes.Shape>オブジェクトの内容は、元の縦横比を維持したまま、レイアウト空間全体に完全に広がっています。  
  
 オブジェクトの内容を<xref:System.Windows.Shapes.Shape>ストレッチすると、<xref:System.Windows.Shapes.Shape>オブジェクトの輪郭はストレッチ後に描画されます。  
  
 次の例では、a<xref:System.Windows.Shapes.Polygon>を使用して、(0,0) から (0,1) から (1,1) までの非常に小さな三角形を描画します。 オブジェクト<xref:System.Windows.Shapes.Polygon>の<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>が 100 に設定され、そのストレッチ プロパティが Fill に設定されます。 その結果、オブジェクトの<xref:System.Windows.Shapes.Polygon>内容(三角形)が拡大したスペースに拡大されます。  
  
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
 クラス<xref:System.Windows.Media.Transform>は、2 次元平面で図形を変換する手段を提供します。  変換の種類には、回転 (<xref:System.Windows.Media.RotateTransform>)<xref:System.Windows.Media.ScaleTransform>、スケール<xref:System.Windows.Media.SkewTransform>( )<xref:System.Windows.Media.TranslateTransform>、 スキュー ( ) 、 変換 ( ) などがあります。  
  
 図形に適用される一般的な変換は回転です。  図形を回転するには、 を<xref:System.Windows.Media.RotateTransform>作成し、<xref:System.Windows.Media.RotateTransform.Angle%2A>図形を指定します。 45 の A は<xref:System.Windows.Media.RotateTransform.Angle%2A>、要素を時計回りに 45 度回転します。角度 90 は、要素を時計回りに 90 度回転します。などなど。 要素を<xref:System.Windows.Media.RotateTransform.CenterX%2A>回転<xref:System.Windows.Media.RotateTransform.CenterY%2A>するポイントをコントロールする場合は、 と プロパティを設定します。 これらのプロパティ値は、変換する要素の座標空間で表します。 <xref:System.Windows.Media.RotateTransform.CenterX%2A>既定値<xref:System.Windows.Media.RotateTransform.CenterY%2A>が 0 です。 最後に、要素<xref:System.Windows.Media.RotateTransform>にを適用します。 変換がレイアウトに影響しない場合は、図形の<xref:System.Windows.UIElement.RenderTransform%2A>プロパティを設定します。  
  
 次の例では、a<xref:System.Windows.Media.RotateTransform>を使用して図形の左上隅 (0,0) を中心に図形を 45 度回転します。  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 次の例では、別の図形を 45 度回転していますが、この場合は (25,50) が回転の中心です。  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 上記 2 つの変換を適用すると、結果は次の図のようになります。  
  
 ![中心点が異なる 45 度の回転](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 前の例では、単一の変換を各図形オブジェクトに適用しました。 図形 (または他の UI 要素) に複数の変換を<xref:System.Windows.Media.TransformGroup>適用するには、 を使用します。  
  
## <a name="see-also"></a>関連項目

- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [ジオメトリの概要](geometry-overview.md)
- [チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [アニメーションの概要](animation-overview.md)

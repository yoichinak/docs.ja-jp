---
title: ジオメトリの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: ff42e59edd9d98b0b52dc3bdd3ace0c35df60878
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112376"
---
# <a name="geometry-overview"></a>ジオメトリの概要
この概要では、クラスを使用して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Media.Geometry>図形を記述する方法について説明します。 また、このトピックでは、オブジェクトと<xref:System.Windows.Media.Geometry><xref:System.Windows.Shapes.Shape>要素の違いについても説明します。  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>ジオメトリとは  
 クラス<xref:System.Windows.Media.Geometry>と、そこから派生するクラス<xref:System.Windows.Media.EllipseGeometry><xref:System.Windows.Media.PathGeometry>( など<xref:System.Windows.Media.CombinedGeometry>) を使用すると、2D 図形のジオメトリを記述できます。 これらの幾何学的な記述には、画面を塗りつぶす図形を定義したり、ヒット テストやクリップ領域を定義するなど、多くの用途があります。 ジオメトリを使用して、アニメーション パスを定義することもできます。  
  
 <xref:System.Windows.Media.Geometry>オブジェクトは、2 つ以上のジオメトリ オブジェクトから作成された、矩形や円などの単純なオブジェクト、または合成オブジェクトにすることができます。  より複雑なジオメトリを作成するには、<xref:System.Windows.Media.PathGeometry>クラスと<xref:System.Windows.Media.StreamGeometry>クラスを使用して円弧と曲線を記述できます。  
  
 オブジェクト<xref:System.Windows.Media.Geometry>は、 の<xref:System.Windows.Freezable><xref:System.Windows.Media.Geometry>一種であるため、[リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)として宣言したり、複数のオブジェクト間で共有したり、パフォーマンスを向上させるために読み取り専用にしたり、クローンを作成したり、スレッドセーフにしたりできます。 オブジェクトによって<xref:System.Windows.Freezable>提供されるさまざまな機能の詳細については、 [[フリーザブル オブジェクトの概要](../advanced/freezable-objects-overview.md)] を参照してください。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>ジオメトリとシェイプ  
 クラス<xref:System.Windows.Media.Geometry>と<xref:System.Windows.Shapes.Shape>クラスは、2D 形状(比較<xref:System.Windows.Media.EllipseGeometry>と例)を表<xref:System.Windows.Shapes.Ellipse>す点で似ているように見えますが、重要な違いがあります。  
  
 1 つには<xref:System.Windows.Media.Geometry>、クラスが<xref:System.Windows.Freezable>クラスから継承され<xref:System.Windows.Shapes.Shape>、クラスが<xref:System.Windows.FrameworkElement>から継承されます。 オブジェクトは要素であるため、<xref:System.Windows.Shapes.Shape>オブジェクトはレンダリングしてレイアウト システムに参加できますが<xref:System.Windows.Media.Geometry>、オブジェクトはレンダリングできません。  
  
 オブジェクト<xref:System.Windows.Shapes.Shape>はオブジェクトよりも<xref:System.Windows.Media.Geometry>簡単に使用できますが、<xref:System.Windows.Media.Geometry>オブジェクトの方が汎用性が高くなります。 オブジェクトを<xref:System.Windows.Shapes.Shape>使用して 2D グラフィックスをレンダリングする<xref:System.Windows.Media.Geometry>場合、オブジェクトを使用して 2D グラフィックスのジオメトリ領域を定義したり、クリップ領域を定義したり、ヒット テスト用の領域を定義したりできます。  
  
### <a name="the-path-shape"></a>パス図形  
 クラス<xref:System.Windows.Shapes.Shape>の<xref:System.Windows.Shapes.Path>1 つは、実際<xref:System.Windows.Media.Geometry>には、 が内容を記述するために使用します。 のプロパティを<xref:System.Windows.Shapes.Path.Data%2A>設定<xref:System.Windows.Shapes.Path><xref:System.Windows.Media.Geometry>し、その<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティと<xref:System.Windows.Shapes.Shape.Stroke%2A>プロパティを<xref:System.Windows.Media.Geometry>設定することで、 をレンダリングできます。  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>ジオメトリを使用する一般的なプロパティ  
 これまでのセクションでは、図形の描画、アニメーション、クリッピングなどのさまざまな目的で、ジオメトリ オブジェクトを他のオブジェクトと共に使用できることを説明しました。 次の表は、オブジェクトを受け取るプロパティ<xref:System.Windows.Media.Geometry>を持ついくつかのクラスを示しています。  
  
|Type|プロパティ|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>単純なジオメトリの種類  
 すべてのジオメトリの基本クラスは 抽象クラス<xref:System.Windows.Media.Geometry>です。  <xref:System.Windows.Media.Geometry>クラスから派生するクラスは、単純なジオメトリ、パス ジオメトリ、複合ジオメトリの 3 つのカテゴリに大別できます。  
  
 単純なジオメトリ クラス<xref:System.Windows.Media.LineGeometry>には<xref:System.Windows.Media.RectangleGeometry>、 <xref:System.Windows.Media.EllipseGeometry> 、および が含まれ、線、四角形、円などの基本的なジオメトリック シェイプを作成するために使用されます。  
  
- A<xref:System.Windows.Media.LineGeometry>は、線の始点と終点を指定することによって定義されます。  
  
- A<xref:System.Windows.Media.RectangleGeometry>は、相対的<xref:System.Windows.Rect>な位置、高さ、幅を指定する構造体で定義されます。 プロパティと プロパティを設定して、角<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>丸<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>長方形を作成できます。  
  
- A<xref:System.Windows.Media.EllipseGeometry>は、中心点、x 半径、および y 半径によって定義されます。  レンダリングとクリッピング用の単純ジオメトリの作成方法を次の例に示します。  
  
 これらの同じシェイプと複雑なシェイプは、ジオメトリ オブジェクトを組<xref:System.Windows.Media.PathGeometry>み合わせて作成したり、組み合わせて作成することもできますが、これらのクラスは、これらの基本的なジオメトリシェイプを簡単に作成できます。  
  
 を作成してレンダリングする方法を次の例<xref:System.Windows.Media.LineGeometry>に示します。  前に説明したように、<xref:System.Windows.Media.Geometry>オブジェクト自体は描画できないため、この例では図形を<xref:System.Windows.Shapes.Path>使用して線を描画します。  ラインにはエリアがないため、 の<xref:System.Windows.Shapes.Shape.Fill%2A><xref:System.Windows.Shapes.Path>プロパティを設定しても効果はありません。代わりに、<xref:System.Windows.Shapes.Shape.Stroke%2A>および<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティのみが指定されます。 この例からの出力を次の図に示します。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
(10,20) から (100,130) まで描画された LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 次の例では、 を作成してレンダリング<xref:System.Windows.Media.EllipseGeometry>する方法を示します。  この例<xref:System.Windows.Media.EllipseGeometry.Center%2A>では<xref:System.Windows.Media.EllipseGeometry>、の を点`50,50`に設定し、x 半径と y 半径の両方をに`50`設定し、直径 100 の円を作成します。  楕円の内部は、Path 要素の Fill プロパティ (この場合<xref:System.Windows.Media.Brushes.Gold%2A>は) に値を割り当てることによって描画されます。 この例からの出力を次の図に示します。  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
(50,50) に描画された EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 を作成してレンダリングする方法を次の例<xref:System.Windows.Media.RectangleGeometry>に示します。  四角形の位置と寸法は<xref:System.Windows.Rect>、構造体によって定義されます。 位置は `50,50`、高さと幅は両方とも `25` で、正方形が作成されます。 この例からの出力を次の図に示します。  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
50,50 に描画された RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 イメージのクリップ領域として を<xref:System.Windows.Media.EllipseGeometry>使用する方法を次の例に示します。  オブジェクト<xref:System.Windows.Controls.Image>は 200、150<xref:System.Windows.FrameworkElement.Width%2A>で<xref:System.Windows.FrameworkElement.Height%2A>定義されます。  値<xref:System.Windows.Media.EllipseGeometry>が<xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 100、75、<xref:System.Windows.Media.EllipseGeometry.Center%2A>値 100,75 がイメージの<xref:System.Windows.UIElement.Clip%2A>プロパティに設定されます。  イメージの楕円の領域内の部分だけが表示されます。 この例からの出力を次の図に示します。  
  
 ![クリッピングを使用する (または使用しない) イメージ](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
イメージ コントロールのクリップに使用される EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>パス ジオメトリ  
 クラス<xref:System.Windows.Media.PathGeometry>とその軽量の同等の<xref:System.Windows.Media.StreamGeometry>クラスは、アーク、曲線、および線で構成される複数の複雑な図形を記述する手段を提供します。  
  
 a<xref:System.Windows.Media.PathGeometry>の中心にはオブジェクトの<xref:System.Windows.Media.PathFigure>コレクションがあるため、各図は. <xref:System.Windows.Media.PathGeometry> 各<xref:System.Windows.Media.PathFigure>オブジェクト自体は 1 つ以上<xref:System.Windows.Media.PathSegment>のオブジェクトで構成され、それぞれが図の 1 つのセグメントを表します。  
  
 多くの種類のセグメントがあります。  
  
|セグメントの種類|説明|例|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの点の間の楕円の円弧を作成します。|[楕円弧 を作成](how-to-create-an-elliptical-arc.md)します。|  
|<xref:System.Windows.Media.BezierSegment>|2 つの点の間の 3 次ベジエ曲線を作成します。|[3 次ベジエ曲線を作成する](how-to-create-a-cubic-bezier-curve.md)。|  
|<xref:System.Windows.Media.LineSegment>|2 つの点を結ぶ直性を作成します。|[PathGeometry で LineSegment を作成する](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|一連の 3 次ベジエ曲線を作成します。|タイプページ<xref:System.Windows.Media.PolyBezierSegment>を参照してください。|  
|<xref:System.Windows.Media.PolyLineSegment>|一続きの直線を作成します。|タイプページ<xref:System.Windows.Media.PolyLineSegment>を参照してください。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一連の 2 次ベジエ曲線を作成します。|ページを<xref:System.Windows.Media.PolyQuadraticBezierSegment>参照してください。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|[二次ベジェ曲線を作成](how-to-create-a-quadratic-bezier-curve.md)します。|  
  
 内のセグメント<xref:System.Windows.Media.PathFigure>は、1 つのジオメトリック形状に結合され、各セグメントの終点が次のセグメントの始点になります。 の<xref:System.Windows.Media.PathFigure.StartPoint%2A><xref:System.Windows.Media.PathFigure>プロパティは、最初のセグメントが描画されるポイントを指定します。 後続の各セグメントは、前のセグメントの終点から開始します。 たとえば、`10,50`から垂直な線を`10,150`定義するには、 プロパティを<xref:System.Windows.Media.PathFigure.StartPoint%2A>に`10,50`設定し、<xref:System.Windows.Media.LineSegment>プロパティ<xref:System.Windows.Media.LineSegment.Point%2A>の設定`10,150`を .  
  
 次の例では、単<xref:System.Windows.Media.PathGeometry><xref:System.Windows.Media.PathFigure>一で構成されるシンプルな<xref:System.Windows.Media.LineSegment>a を作成し<xref:System.Windows.Shapes.Path>、要素を使用して表示します。 オブジェクト<xref:System.Windows.Media.PathFigure>の<xref:System.Windows.Media.PathFigure.StartPoint%2A>が に`10,20`設定され、の<xref:System.Windows.Media.LineSegment>終点で 定義されます。 `100,130` 次の図は、<xref:System.Windows.Media.PathGeometry>この例で作成された例を示しています。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
単一の LineSegment を含む PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 この例を前の例と比較すると価値があります<xref:System.Windows.Media.LineGeometry>。  に<xref:System.Windows.Media.PathGeometry>使用される構文は、単純<xref:System.Windows.Media.LineGeometry>な に使用される構文よりもはるかに冗長であり、この場合は<xref:System.Windows.Media.LineGeometry>クラスを使用する方が理にかなっていますが、詳細な構文<xref:System.Windows.Media.PathGeometry>では非常に複雑で複雑な幾何学的領域が可能です。  
  
 <xref:System.Windows.Media.PathSegment>オブジェクトの組み合わせを使用して、より複雑なジオメトリを作成できます。  
  
 次の例では<xref:System.Windows.Media.BezierSegment>、 <xref:System.Windows.Media.LineSegment>a および<xref:System.Windows.Media.ArcSegment>a を使用して、図形を作成します。 最初に 3 次ベジエ曲線を作成するには、開始点(前のセグメントの終点)、終点()、<xref:System.Windows.Media.BezierSegment.Point3%2A>および 2 つの制御点(<xref:System.Windows.Media.BezierSegment.Point1%2A>と<xref:System.Windows.Media.BezierSegment.Point2%2A>)の 4 点を定義します。  3 次ベジエ曲線の 2 つの制御点は磁石のように動作し、本来は直線になる部分を制御点の方へ引き寄せ、曲線を生成します。 1 つ目の<xref:System.Windows.Media.BezierSegment.Point1%2A>コントロール ポイント は、曲線の開始部分に影響します。2 番目のコントロール<xref:System.Windows.Media.BezierSegment.Point2%2A>ポイント は、曲線の終了部分に影響します。  
  
 次に、前の<xref:System.Windows.Media.LineSegment>プロパティで指定された点に前の終<xref:System.Windows.Media.BezierSegment>点の間に描画される を追加<xref:System.Windows.Media.LineSegment>します。  
  
 次に、前の<xref:System.Windows.Media.ArcSegment>プロパティで指定した点<xref:System.Windows.Media.LineSegment>に、前の終点から描画される を追加<xref:System.Windows.Media.ArcSegment.Point%2A>します。 また、円弧の x 半径と y 半径<xref:System.Windows.Media.ArcSegment.Size%2A>( )、回転<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>角度 ( ) 、生成される円弧の角度をどの<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>程度大きくするかを示すフラグ ( ) と<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>、円弧を描画する方向を示す値 ( ) を指定します。 この例で作成した図形を次の図に示します。  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 さらに複雑なジオメトリは、 内の複数<xref:System.Windows.Media.PathFigure>のオブジェクトを<xref:System.Windows.Media.PathGeometry>使用して作成できます。  
  
 次の例では、2 <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.PathFigure>つのオブジェクトを持つ a<xref:System.Windows.Media.PathSegment>を作成し、それぞれに複数のオブジェクトが含まれています。  上記<xref:System.Windows.Media.PathFigure>の例からa<xref:System.Windows.Media.PathFigure><xref:System.Windows.Media.PolyLineSegment>とaが<xref:System.Windows.Media.QuadraticBezierSegment>使用される。  A<xref:System.Windows.Media.PolyLineSegment>は、点の配列で定義され<xref:System.Windows.Media.QuadraticBezierSegment>、コントロール ポイントと終了点を使用して 定義されます。 この例で作成した図形を次の図に示します。  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
複数の図形を使用する PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 クラスと<xref:System.Windows.Media.PathGeometry>同様に、a は<xref:System.Windows.Media.StreamGeometry>曲線、円弧、および線分を含む複雑な幾何学的形状を定義します。 と<xref:System.Windows.Media.PathGeometry>は異なり、 の<xref:System.Windows.Media.StreamGeometry>コンテンツは、データ バインディング、アニメーション、または変更をサポートしていません。 複雑な<xref:System.Windows.Media.StreamGeometry>ジオメトリを記述する必要があるが、データ バインディング、アニメーション、または変更をサポートするオーバーヘッドが必要ない場合に使用します。 効率が良いため、<xref:System.Windows.Media.StreamGeometry>クラスは装飾品を記述するための良い選択です。  
  
 例については、「[方法 : StreamGeometry を使用して図形を作成する](how-to-create-a-shape-using-a-streamgeometry.md)」をご覧ください。  
  
### <a name="path-markup-syntax"></a>パス マークアップ構文  
 <xref:System.Windows.Media.PathGeometry>型と<xref:System.Windows.Media.StreamGeometry>の間で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、特殊な一連の移動コマンドと描画コマンドを使用した属性構文がサポートされます。 詳しくは、「[パス マークアップ構文](path-markup-syntax.md)」をご覧ください。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>複合ジオメトリ  
 複合ジオメトリ<xref:System.Windows.Media.GeometryGroup>オブジェクトは、<xref:System.Windows.Media.CombinedGeometry>を使用して作成するか、 static<xref:System.Windows.Media.Geometry>メソッド<xref:System.Windows.Media.Geometry.Combine%2A>を呼び出すことによって作成できます。  
  
- オブジェクト<xref:System.Windows.Media.CombinedGeometry>と<xref:System.Windows.Media.Geometry.Combine%2A>メソッドはブール演算を実行し、2 つのジオメトリで定義された領域を結合します。 <xref:System.Windows.Media.Geometry>領域のないオブジェクトは破棄されます。 結合できる<xref:System.Windows.Media.Geometry>オブジェクトは 2 つだけです(ただし、この 2 つのジオメトリは複合ジオメトリである場合もあります)。  
  
- この<xref:System.Windows.Media.GeometryGroup>クラスは、その領域を結合せずに、<xref:System.Windows.Media.Geometry>含まれているオブジェクトの融合を作成します。 オブジェクトの任意<xref:System.Windows.Media.Geometry>の数を<xref:System.Windows.Media.GeometryGroup>に追加できます。 例については、「[方法 : 複合図形を作成する](how-to-create-a-composite-shape.md)」をご覧ください。  
  
 結合操作は実行されないため、オブジェクトを使用すると<xref:System.Windows.Media.GeometryGroup>、オブジェクトやメソッドを使用<xref:System.Windows.Media.CombinedGeometry>する場合よりも<xref:System.Windows.Media.Geometry.Combine%2A>パフォーマンス上の利点が得られます。  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>結合したジオメトリ  
 前のセクションでは、オブジェクト<xref:System.Windows.Media.CombinedGeometry>について説明し<xref:System.Windows.Media.Geometry.Combine%2A>、メソッドは、それらが含まれているジオメトリによって定義された領域を組み合わせた。 列挙<xref:System.Windows.Media.GeometryCombineMode>体は、ジオメトリの結合方法を指定します。 プロパティ<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>の値としては<xref:System.Windows.Media.GeometryCombineMode.Union>、 、 <xref:System.Windows.Media.GeometryCombineMode.Intersect>、 <xref:System.Windows.Media.GeometryCombineMode.Exclude>、<xref:System.Windows.Media.GeometryCombineMode.Xor>および が含まれます。  
  
 次の例では、結合<xref:System.Windows.Media.CombinedGeometry>モードが Union で定義されています。  と<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>は両方とも同じ半径の円として定義されますが、中心は 50 オフセットされます。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![結合組み合わせモードの結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 次の例では、<xref:System.Windows.Media.CombinedGeometry>を結合モードで定義<xref:System.Windows.Media.GeometryCombineMode.Xor>します。  と<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>は両方とも同じ半径の円として定義されますが、中心は 50 オフセットされます。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 組み合わせモードの結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 その他の例については、「[方法 : 複合図形を作成する](how-to-create-a-composite-shape.md)」と「[方法 : 結合したジオメトリを作成する](how-to-create-a-combined-geometry.md)」をご覧ください。  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable 機能  
 <xref:System.Windows.Freezable>クラスから継承されるため、<xref:System.Windows.Media.Geometry><xref:System.Windows.Media.Geometry>このクラスには、オブジェクトを XAML リソースとして宣言し、複数[の](../../../desktop-wpf/fundamentals/xaml-resources-define.md)オブジェクト間で共有したり、読み取り専用にしてパフォーマンスを向上させたり、クローンを作成したり、スレッド セーフにしたりといった特別な機能が用意されています。 オブジェクトによって<xref:System.Windows.Freezable>提供されるさまざまな機能の詳細については、 [[フリーザブル オブジェクトの概要](../advanced/freezable-objects-overview.md)] を参照してください。  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>その他のジオメトリ機能  
 この<xref:System.Windows.Media.Geometry>クラスには、次のような便利なユーティリティ メソッドも用意されています。  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- の領域を取得<xref:System.Windows.Media.Geometry>します。  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- ジオメトリに別<xref:System.Windows.Media.Geometry>の .  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- のストロークに指定した<xref:System.Windows.Media.Geometry>点が含まれているかどうかを判断します。  
  
 メソッドの<xref:System.Windows.Media.Geometry>完全なリストについては、クラスを参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [パス マークアップ構文](path-markup-syntax.md)
- [ハウツートピック](geometries-how-to-topics.md)
- [アニメーションの概要](animation-overview.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)

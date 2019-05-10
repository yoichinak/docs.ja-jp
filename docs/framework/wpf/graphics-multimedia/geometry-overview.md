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
ms.openlocfilehash: 3c26b08dd7ec70a1763fce89b34376350b985fb5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615386"
---
# <a name="geometry-overview"></a>ジオメトリの概要
この概要は、使用する方法を説明します、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry>クラス図形を記述します。 このトピックでは、間の相違点も対照的です。<xref:System.Windows.Media.Geometry>オブジェクトと<xref:System.Windows.Shapes.Shape>要素。  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>ジオメトリとは  
 <xref:System.Windows.Media.Geometry>クラスとクラスなど、そこから派生する<xref:System.Windows.Media.EllipseGeometry>、 <xref:System.Windows.Media.PathGeometry>、および<xref:System.Windows.Media.CombinedGeometry>、2-d 図形のジオメトリを記述できます。 これらの幾何学的な記述には、画面を塗りつぶす図形を定義したり、ヒット テストやクリップ領域を定義するなど、多くの用途があります。 ジオメトリを使用して、アニメーション パスを定義することもできます。  
  
 <xref:System.Windows.Media.Geometry> 四角形や円、複合では、2 つ以上のジオメトリ オブジェクトから作成など、オブジェクトは、単純なできます。  使用してより複雑なジオメトリを作成することができます、<xref:System.Windows.Media.PathGeometry>と<xref:System.Windows.Media.StreamGeometry>円弧や曲線を記述するためのクラス。  
  
 <xref:System.Windows.Media.Geometry>の種類は、 <xref:System.Windows.Freezable>、<xref:System.Windows.Media.Geometry>オブジェクトは、いくつかの特別な機能を提供: と宣言されている[リソース](../advanced/xaml-resources.md)、複製すると、パフォーマンスを向上させるために読み取り専用の複数のオブジェクト間で共有とスレッド セーフに行われます。 によって提供されるさまざまな機能の詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>ジオメトリと図形  
 <xref:System.Windows.Media.Geometry>と<xref:System.Windows.Shapes.Shape>2-d 図形が記述で、クラスが似て (比較<xref:System.Windows.Media.EllipseGeometry>と<xref:System.Windows.Shapes.Ellipse>など) が重要な違いがあります。  
  
 1 つは、<xref:System.Windows.Media.Geometry>クラスから継承、<xref:System.Windows.Freezable>時に、クラス、<xref:System.Windows.Shapes.Shape>クラスから継承<xref:System.Windows.FrameworkElement>します。 要素であるため<xref:System.Windows.Shapes.Shape>オブジェクトが自身をレンダリングし、レイアウト システムに参加中に<xref:System.Windows.Media.Geometry>オブジェクトことはできません。  
  
 <xref:System.Windows.Shapes.Shape>オブジェクトよりもより簡単に使用可能な<xref:System.Windows.Media.Geometry>オブジェクト、<xref:System.Windows.Media.Geometry>オブジェクトは汎用性が高まります。 中に、<xref:System.Windows.Shapes.Shape>オブジェクトは 2-d グラフィックスをレンダリングするために使用する<xref:System.Windows.Media.Geometry>オブジェクトは、2 D グラフィックスの幾何学的領域の定義、クリッピング用の領域を定義または例のヒット テスト用の領域を定義するために使用できます。  
  
### <a name="the-path-shape"></a>パス図形  
 1 つ<xref:System.Windows.Shapes.Shape>、<xref:System.Windows.Shapes.Path>クラスを使用して実際には、<xref:System.Windows.Media.Geometry>その内容を記述します。 設定して、<xref:System.Windows.Shapes.Path.Data%2A>のプロパティ、<xref:System.Windows.Shapes.Path>で、<xref:System.Windows.Media.Geometry>設定とその<xref:System.Windows.Shapes.Shape.Fill%2A>と<xref:System.Windows.Shapes.Shape.Stroke%2A>プロパティを表示するには、 <xref:System.Windows.Media.Geometry>。  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>ジオメトリを使用する一般的なプロパティ  
 これまでのセクションでは、図形の描画、アニメーション、クリッピングなどのさまざまな目的で、ジオメトリ オブジェクトを他のオブジェクトと共に使用できることを説明しました。 次の表に、いくつかのクラスを使用するプロパティを持つ、<xref:System.Windows.Media.Geometry>オブジェクト。  
  
|型|プロパティ|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>単純なジオメトリの種類  
 すべてのジオメトリの基底クラスは抽象クラス<xref:System.Windows.Media.Geometry>します。  クラスから派生するクラス、<xref:System.Windows.Media.Geometry>クラスを大まかに 3 つのカテゴリ分類: 単純なジオメトリ、パス ジオメトリ、および複合ジオメトリ。  
  
 単純なジオメトリ クラス<xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.RectangleGeometry>、および<xref:System.Windows.Media.EllipseGeometry>線、四角形や円などの基本的な幾何学的図形の作成に使用されます。  
  
- A<xref:System.Windows.Media.LineGeometry>行と終点の始点を指定することによって定義されます。  
  
- A<xref:System.Windows.Media.RectangleGeometry>を定義して、<xref:System.Windows.Rect>構造の相対的な位置、高さ、および幅を指定します。 角丸四角形を作成するには設定して、<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>と<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>プロパティ。  
  
- <xref:System.Windows.Media.EllipseGeometry>中心点、x 半径と y 半径によって定義されます。  レンダリングとクリッピング用の単純ジオメトリの作成方法を次の例に示します。  
  
 使用して、これらと同じ図形は、だけでなく、複雑な図形を作成できる、<xref:System.Windows.Media.PathGeometry>または geometry オブジェクトを合わせてがこれらのクラスを組み合わせることで、これらの基本的な幾何学的図形を生成するため簡単な手段を提供します。  
  
 次の例を作成してレンダリングする方法を示しています、<xref:System.Windows.Media.LineGeometry>します。  以前は、説明したように、<xref:System.Windows.Media.Geometry>オブジェクトができないため、この例では、それ自体を描画するために、<xref:System.Windows.Shapes.Path>図形、線を表示するためにします。  設定する行に領域があるないため、<xref:System.Windows.Shapes.Shape.Fill%2A>のプロパティ、<xref:System.Windows.Shapes.Path>は効果がありません。 代わりに、のみ、<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティが指定されてです。 この例からの出力を次の図に示します。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
(10,20) から (100,130) まで描画された LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 次の例を作成してレンダリングする方法を示しています、<xref:System.Windows.Media.EllipseGeometry>します。  例のセット、<xref:System.Windows.Media.EllipseGeometry.Center%2A>の<xref:System.Windows.Media.EllipseGeometry>ポイントに設定されている`50,50`x 半径と y 半径が両方とも設定`50`直径が 100 の円を作成します。  この場合、Path 要素の Fill プロパティの値を割り当てることで、楕円の内部を塗りつぶす<xref:System.Windows.Media.Brushes.Gold%2A>します。 この例からの出力を次の図に示します。  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
(50,50) に描画された EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 次の例を作成してレンダリングする方法を示しています、<xref:System.Windows.Media.RectangleGeometry>します。  位置と四角形のディメンションがによって定義、<xref:System.Windows.Rect>構造体。 位置は `50,50`、高さと幅は両方とも `25` で、正方形が作成されます。 この例からの出力を次の図に示します。  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
50,50 に描画された RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 次の例は、使用する方法を示します、<xref:System.Windows.Media.EllipseGeometry>イメージのクリップ領域として。  <xref:System.Windows.Controls.Image>でオブジェクトが定義されている、 <xref:System.Windows.FrameworkElement.Width%2A> 200 と<xref:System.Windows.FrameworkElement.Height%2A>150。  <xref:System.Windows.Media.EllipseGeometry>で、<xref:System.Windows.Media.EllipseGeometry.RadiusX%2A>値が 100 の<xref:System.Windows.Media.EllipseGeometry.RadiusY%2A>75 の値と<xref:System.Windows.Media.EllipseGeometry.Center%2A>が 100, 75 の値に設定されて、<xref:System.Windows.UIElement.Clip%2A>イメージのプロパティ。  イメージの楕円の領域内の部分だけが表示されます。 この例からの出力を次の図に示します。  
  
 ![イメージとクリッピングなし](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
イメージ コントロールのクリップに使用される EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>パス ジオメトリ  
 <xref:System.Windows.Media.PathGeometry>クラスとその軽量等価、<xref:System.Windows.Media.StreamGeometry>クラス、円弧、曲線、および行ので構成される複数の複雑な図形を記述するための手段を提供します。  
  
 中核を<xref:System.Windows.Media.PathGeometry>のコレクションである<xref:System.Windows.Media.PathFigure>オブジェクト、各図形で個別の図形を記述するため、この名前が付いて、<xref:System.Windows.Media.PathGeometry>します。 各<xref:System.Windows.Media.PathFigure>自体は 1 つ以上ので構成されます<xref:System.Windows.Media.PathSegment>オブジェクト、それぞれの図形のセグメントをについて説明します。  
  
 多くの種類のセグメントがあります。  
  
|セグメントの種類|説明|例|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの点を結ぶ楕円の円弧を作成します。|[楕円の円弧を作成する](how-to-create-an-elliptical-arc.md)。|  
|<xref:System.Windows.Media.BezierSegment>|2 つの点を結ぶ 3 次ベジエ曲線を作成します。|[3 次ベジエ曲線を作成する](how-to-create-a-cubic-bezier-curve.md)。|  
|<xref:System.Windows.Media.LineSegment>|2 つの点を結ぶ直性を作成します。|[PathGeometry で LineSegment を作成する](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|一続きの 3 次ベジエ曲線を作成します。|参照してください、<xref:System.Windows.Media.PolyBezierSegment>の種類 ページ。|  
|<xref:System.Windows.Media.PolyLineSegment>|一続きの直線を作成します。|参照してください、<xref:System.Windows.Media.PolyLineSegment>の種類 ページ。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一続きの 2 次ベジエ曲線を作成します。|参照してください、<xref:System.Windows.Media.PolyQuadraticBezierSegment>ページ。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|[2 次ベジエ曲線を作成する](how-to-create-a-quadratic-bezier-curve.md)。|  
  
 内のセグメントを<xref:System.Windows.Media.PathFigure>されて次のセグメントの始点、各セグメントの終点の 1 つの幾何学図形に結合されます。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>のプロパティを<xref:System.Windows.Media.PathFigure>最初のセグメントの描画元となるポイントを指定します。 後続の各セグメントは、前のセグメントの終点から始まります。 垂直線など`10,50`に`10,150`を設定して定義できます、<xref:System.Windows.Media.PathFigure.StartPoint%2A>プロパティを`10,50`を作成して、<xref:System.Windows.Media.LineSegment>で、<xref:System.Windows.Media.LineSegment.Point%2A>プロパティの設定`10,150`。  
  
 次の例では、単純な<xref:System.Windows.Media.PathGeometry>、1 つから成る<xref:System.Windows.Media.PathFigure>で、<xref:System.Windows.Media.LineSegment>使用して、表示、<xref:System.Windows.Shapes.Path>要素。 <xref:System.Windows.Media.PathFigure>オブジェクトの<xref:System.Windows.Media.PathFigure.StartPoint%2A>に設定されている`10,20`と<xref:System.Windows.Media.LineSegment>の終点で定義されて`100,130`します。 次の図は、<xref:System.Windows.Media.PathGeometry>この例で作成します。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
単一の LineSegment を含む PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 前述のこの例は<xref:System.Windows.Media.LineGeometry>例。  使用される構文、<xref:System.Windows.Media.PathGeometry>は簡単なために使用するよりもかなり詳細<xref:System.Windows.Media.LineGeometry>を使用する方が簡単にして、<xref:System.Windows.Media.LineGeometry>の冗語構文が、ここでは、クラス、<xref:System.Windows.Media.PathGeometry>非常に難解で複雑では、幾何学領域。  
  
 組み合わせを使用して、複雑なジオメトリを作成する<xref:System.Windows.Media.PathSegment>オブジェクト。  
  
 次の例では、 <xref:System.Windows.Media.BezierSegment>、 <xref:System.Windows.Media.LineSegment>、および<xref:System.Windows.Media.ArcSegment>図形を作成します。 例は、まず、3 次ベジエ曲線は 4 つのポイントを定義することを作成します。 前のセグメントの終点の終了点は、始点 (<xref:System.Windows.Media.BezierSegment.Point3%2A>)、と 2 つのコントロール ポイント (<xref:System.Windows.Media.BezierSegment.Point1%2A>と<xref:System.Windows.Media.BezierSegment.Point2%2A>)。  3 次ベジエ曲線の 2 つの制御点は磁石のように動作し、本来は直線になる部分を制御点の方へ引き寄せ、曲線を生成します。 最初の制御点、 <xref:System.Windows.Media.BezierSegment.Point1%2A>、先頭に影響を与えます曲線の部分は、2 つ目のコントロール ポイント<xref:System.Windows.Media.BezierSegment.Point2%2A>曲線の終了部分に影響します。  
  
 例を追加し、 <xref:System.Windows.Media.LineSegment>、前述の終点の間で描画される<xref:System.Windows.Media.BezierSegment>前に指定された地点をその<xref:System.Windows.Media.LineSegment>プロパティ。  
  
 例を追加し、 <xref:System.Windows.Media.ArcSegment>、これは、上記の点から描画されます<xref:System.Windows.Media.LineSegment>で指定されたポイントにその<xref:System.Windows.Media.ArcSegment.Point%2A>プロパティ。 この例では、円弧の x 半径と y 半径も指定します (<xref:System.Windows.Media.ArcSegment.Size%2A>)、回転角度 (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>)、結果の円弧の角度にする必要があります大きさを示すフラグ (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>)、円弧が描画される方向を示す値 (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). この例で作成した図形を次の図に示します。  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 複数を使用して、さらに複雑なジオメトリを作成することができます<xref:System.Windows.Media.PathFigure>内のオブジェクトは、<xref:System.Windows.Media.PathGeometry>します。  
  
 次の例では、作成、<xref:System.Windows.Media.PathGeometry>の 2 つ<xref:System.Windows.Media.PathFigure>複数含まれている各オブジェクト<xref:System.Windows.Media.PathSegment>オブジェクト。  <xref:System.Windows.Media.PathFigure>上の例と<xref:System.Windows.Media.PathFigure>で、<xref:System.Windows.Media.PolyLineSegment>と<xref:System.Windows.Media.QuadraticBezierSegment>使用されます。  A<xref:System.Windows.Media.PolyLineSegment>ポイントの配列で定義されて、<xref:System.Windows.Media.QuadraticBezierSegment>制御点と終点で定義されます。 この例で作成した図形を次の図に示します。  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
複数の図形を使用する PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 ように、<xref:System.Windows.Media.PathGeometry>クラス、<xref:System.Windows.Media.StreamGeometry>曲線、円弧、および行を含む可能性のある複雑な幾何学図形を定義します。 異なり、<xref:System.Windows.Media.PathGeometry>の内容を<xref:System.Windows.Media.StreamGeometry>データ バインディング、アニメーション、または変更をサポートしていません。 使用して、<xref:System.Windows.Media.StreamGeometry>複雑なジオメトリを記述する必要がある場合がデータ バインディング、アニメーション、または変更をサポートするオーバーヘッドを作成したくないです。 、効率的であるため、<xref:System.Windows.Media.StreamGeometry>クラスは、装飾の記述に適しています。  
  
 例については、「[方法 : StreamGeometry を使用して図形を作成する](how-to-create-a-shape-using-a-streamgeometry.md)」をご覧ください。  
  
### <a name="path-markup-syntax"></a>パス マークアップ構文  
 <xref:System.Windows.Media.PathGeometry>と<xref:System.Windows.Media.StreamGeometry>サポートの種類、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]属性構文は特殊な一連の移動を使用して、描画コマンド。 詳しくは、「[パス マークアップ構文](path-markup-syntax.md)」をご覧ください。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>複合ジオメトリ  
 使用して複合ジオメトリ オブジェクトを作成することができます、 <xref:System.Windows.Media.GeometryGroup>、 <xref:System.Windows.Media.CombinedGeometry>、または静的なを呼び出すことによって<xref:System.Windows.Media.Geometry>メソッド<xref:System.Windows.Media.Geometry.Combine%2A>します。  
  
- <xref:System.Windows.Media.CombinedGeometry>オブジェクトと<xref:System.Windows.Media.Geometry.Combine%2A>メソッドが 2 つのジオメトリで定義される領域を結合するブール型の操作を実行します。 <xref:System.Windows.Media.Geometry> 領域がオブジェクトは破棄されません。 2 つだけ<xref:System.Windows.Media.Geometry>(ただし、これら 2 つのジオメトリは複合ジオメトリの役割を果たす場合もあります)、オブジェクトを組み合わせることができます。  
  
- <xref:System.Windows.Media.GeometryGroup>クラスを融合したものを作成し、<xref:System.Windows.Media.Geometry>オブジェクトの領域を結合せずにします。 任意の数の<xref:System.Windows.Media.Geometry>オブジェクトに追加することができます、<xref:System.Windows.Media.GeometryGroup>します。 例については、「[方法 : 複合図形を作成する](how-to-create-a-composite-shape.md)」をご覧ください。  
  
 使用して結合操作を実行しないため、<xref:System.Windows.Media.GeometryGroup>オブジェクトを使用してパフォーマンスのメリットが得<xref:System.Windows.Media.CombinedGeometry>オブジェクトまたは<xref:System.Windows.Media.Geometry.Combine%2A>メソッド。  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>結合したジオメトリ  
 説明したように、前のセクション、<xref:System.Windows.Media.CombinedGeometry>オブジェクトと<xref:System.Windows.Media.Geometry.Combine%2A>メソッドが含まれるジオメトリで定義される領域を結合します。 <xref:System.Windows.Media.GeometryCombineMode>列挙型では、ジオメトリを結合する方法を指定します。 使用可能な値を<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>プロパティには: <xref:System.Windows.Media.GeometryCombineMode.Union>、 <xref:System.Windows.Media.GeometryCombineMode.Intersect>、 <xref:System.Windows.Media.GeometryCombineMode.Exclude>、および<xref:System.Windows.Media.GeometryCombineMode.Xor>します。  
  
 次の例では、<xref:System.Windows.Media.CombinedGeometry>共用体の結合モードで定義されます。  両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>、 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 50 と <xref:system.windows.media.combinedgeometry.geometry2%2a> が、同じ半径の円として定義されます。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![和集合結合モードの結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 次の例では、<xref:System.Windows.Media.CombinedGeometry>の結合モードで定義されて<xref:System.Windows.Media.GeometryCombineMode.Xor>します。  両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>、 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 50 と <xref:system.windows.media.combinedgeometry.geometry2%2a> が、同じ半径の円として定義されます。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 結合モードの結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 その他の例については、「[方法 : 複合図形を作成する](how-to-create-a-composite-shape.md)」と「[方法 : 結合したジオメトリを作成する](how-to-create-a-combined-geometry.md)」をご覧ください。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 機能  
 継承するため、<xref:System.Windows.Freezable>クラス、<xref:System.Windows.Media.Geometry>クラスがいくつかの特別な機能を提供:<xref:System.Windows.Media.Geometry>オブジェクトとして宣言できます[XAML リソース](../advanced/xaml-resources.md)、向上させるために読み取り専用の複数のオブジェクト間で共有パフォーマンス、複製され、スレッド セーフです。 によって提供されるさまざまな機能の詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>その他のジオメトリ機能  
 <xref:System.Windows.Media.Geometry>クラスは、次などの便利なユーティリティ メソッドも提供します。  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A> -の領域を取得、<xref:System.Windows.Media.Geometry>します。  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A> -別のジオメトリを含むかどうかを判断します<xref:System.Windows.Media.Geometry>します。  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A> 指定するかどうかのストロークを<xref:System.Windows.Media.Geometry>指定したポイントが含まれています。  
  
 参照してください、<xref:System.Windows.Media.Geometry>クラスのメソッドの完全な一覧についてはします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [パス マークアップ構文](path-markup-syntax.md)
- [方法トピック](geometries-how-to-topics.md)
- [アニメーションの概要](animation-overview.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)

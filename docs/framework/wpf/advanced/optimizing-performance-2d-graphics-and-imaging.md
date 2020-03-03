---
title: パフォーマンスの最適化:2D グラフィックスとイメージング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933347"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>パフォーマンスの最適化:2D グラフィックスとイメージング
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、アプリケーションの要件に合わせて最適化できる広範な 2D グラフィックス機能とイメージング機能が用意されています。 このトピックでは、この領域でのパフォーマンスの最適化に関する情報を提供します。  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>描画と図形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には<xref:System.Windows.Media.Drawing> 、 <xref:System.Windows.Shapes.Shape>グラフィック描画コンテンツを表すオブジェクトとオブジェクトの両方が用意されています。 ただし、 <xref:System.Windows.Media.Drawing>オブジェクトはオブジェクトよりも<xref:System.Windows.Shapes.Shape>単純なコンストラクトであり、より優れたパフォーマンス特性を提供します。  
  
 を<xref:System.Windows.Shapes.Shape>使用すると、画面にグラフィカルな図形を描画できます。 これらは<xref:System.Windows.FrameworkElement>クラスから派生するため、 <xref:System.Windows.Shapes.Shape>オブジェクトは、パネルやほとんどのコントロール内で使用できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、グラフィックス サービスやレンダリング サービスへのアクセスのレイヤーがいくつか用意されています。 最上位のレイヤーで<xref:System.Windows.Shapes.Shape>は、オブジェクトは簡単に使用でき、レイアウトやイベント処理などの多くの便利な機能を提供します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、すぐに使用できるさまざまな図形オブジェクトが用意されています。 すべての図形オブジェクトは、 <xref:System.Windows.Shapes.Shape>クラスから継承されます。 使用できる図形オブジェクト<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>には、、、 <xref:System.Windows.Shapes.Rectangle>、、、およびがあります。 <xref:System.Windows.Shapes.Path>  
  
 <xref:System.Windows.Media.Drawing>一方、オブジェクトは<xref:System.Windows.FrameworkElement>クラスから派生せず、形状、画像、およびテキストをレンダリングするための軽量な実装を提供します。  
  
 オブジェクトには、次<xref:System.Windows.Media.Drawing>の4種類があります。  
  
- <xref:System.Windows.Media.GeometryDrawing>図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing>イメージを描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>テキストを描画します。  
  
- <xref:System.Windows.Media.DrawingGroup>他の描画を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 オブジェクト<xref:System.Windows.Media.GeometryDrawing>は、ジオメトリの内容を表示するために使用されます。 クラス<xref:System.Windows.Media.Geometry>およびそれから派生した具象クラス ( <xref:System.Windows.Media.CombinedGeometry>、 <xref:System.Windows.Media.EllipseGeometry>、 <xref:System.Windows.Media.PathGeometry>など) は、2d グラフィックスをレンダリングするための手段と、ヒットテストとクリッピングサポートを提供します。 ジオメトリ オブジェクトを使用すると、たとえば、コントロールの領域を定義したり、イメージに適用するクリップ領域を定義したりすることができます。 ジオメトリ オブジェクトは、四角形や円などの単純な領域にすることも、2 つ以上のジオメトリ オブジェクトから作成された複合的な領域にすることもできます。 <xref:System.Windows.Media.ArcSegment>、 <xref:System.Windows.Media.PathSegment> 、<xref:System.Windows.Media.BezierSegment>などの派生オブジェクトを組み合わせることによって、より複雑なジオメトリック領域を<xref:System.Windows.Media.QuadraticBezierSegment>作成できます。  
  
 サーフェイス<xref:System.Windows.Media.Geometry>では、クラス<xref:System.Windows.Shapes.Shape>とクラスは非常に似ています。 両方とも2d グラフィックスのレンダリングで使用されます。 <xref:System.Windows.Media.EllipseGeometry>また、と<xref:System.Windows.Shapes.Ellipse>など、これらのクラスから派生する類似の具象クラスもあります。 ただし、この 2 つのクラスのセットの間には重要な違いがいくつかあります。 1つ<xref:System.Windows.Media.Geometry>のクラスには、クラス自体を描画する<xref:System.Windows.Shapes.Shape>機能など、クラスの機能の一部が不足しています。 ジオメトリ オブジェクトを描画するには、DrawingContext、Drawing、Path (Path が Shape であることは注目に値します) などの別のクラスを使用して描画操作を実行する必要があります。 塗りつぶし、ストローク、ストロークの太さなどの描画プロパティは、ジオメトリ オブジェクトを描画するクラスにあります。一方、図形オブジェクトにはこれらのプロパティが含まれています。 この違いは、ジオメトリ オブジェクトが円などの領域を定義するのに対し、図形オブジェクトは領域を定義するとともに、その領域の塗りつぶしやアウトラインも定義し、レイアウト システムに参加する、と考えることができます。  
  
 オブジェクト<xref:System.Windows.Shapes.Shape>は<xref:System.Windows.FrameworkElement>クラスから派生するため、それらを使用すると、アプリケーションのメモリ消費量が大幅に増加する可能性があります。 グラフィカルコンテンツの<xref:System.Windows.FrameworkElement>機能が不要な場合は、軽量<xref:System.Windows.Media.Drawing>のオブジェクトを使用することを検討してください。  
  
 オブジェクトの<xref:System.Windows.Media.Drawing>詳細については、「 [Drawing オブジェクトの概要](../graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry オブジェクト  
 オブジェクト<xref:System.Windows.Media.StreamGeometry>は、幾何学図形を<xref:System.Windows.Media.PathGeometry>作成するための軽量の代替です。 複雑な<xref:System.Windows.Media.StreamGeometry>ジオメトリを記述する必要がある場合は、を使用します。 <xref:System.Windows.Media.StreamGeometry>は、多数<xref:System.Windows.Media.PathGeometry>のオブジェクトを処理するために最適化されており<xref:System.Windows.Media.PathGeometry> 、多くの個別のオブジェクトを使用する場合と比較してパフォーマンスが向上します。  
  
 次の例では、属性構文を使用<xref:System.Windows.Media.StreamGeometry>し[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]て、に三角形を作成します。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 オブジェクトの<xref:System.Windows.Media.StreamGeometry>詳細については、「 [streamgeometry を使用して図形を作成](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)する」を参照してください。  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual オブジェクト  
 <xref:System.Windows.Media.DrawingVisual>オブジェクトは、図形、画像、またはテキストを表示するために使用される軽量の描画クラスです。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。 詳しくは、「[DrawingVisual オブジェクトの使用](../graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。  
  
<a name="Images"></a>   
## <a name="images"></a>画像  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イメージングを使用すると、以前のバージョンの Windows では、イメージング機能が大幅に向上します。 イメージング機能 (ビットマップの表示や一般的なコントロール上でのイメージの使用など) は、以前は主に Microsoft Windows Graphics Device Interface (GDI) または Microsoft Windows GDI+ のアプリケーション プログラミング インターフェイス (API) によって処理されていました。 これらの API では、基本的なイメージング機能は提供されていましたが、コーデック拡張機能のサポートや高品質なイメージのサポートなどの機能が不足していました。 WPF Imaging API は、GDI および GDI+ の欠点を克服し、アプリケーション内でイメージを表示および使用するための新しい API のセットを提供するために再設計されています。  
  
 イメージを使用する際には、パフォーマンスを向上させるために以下の推奨事項をご検討ください。  
  
- アプリケーションでサムネイル イメージを表示する必要がある場合は、縮小版のイメージを作成することをご検討ください。 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は読み込んだイメージを本来のサイズにデコードします。 サムネイル バージョンのイメージのみが必要な場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がイメージを本来のサイズにデコードしてからサムネイル サイズに縮小するという無駄が生じます。 この不要なオーバーヘッドを回避するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対してイメージをサムネイル サイズにデコードするように要求するか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にサムネイル サイズのイメージを読み込むように要求します。  
  
- イメージは常に、既定のサイズではなく必要なサイズにデコードするようにしてください。 前述のように、既定の実際のサイズではなく必要なサイズにイメージをデコードするように [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に要求します。 これにより、アプリケーションの作業セットを縮小できるだけでなく、実行速度も向上します。  
  
- 可能であれば、複数のイメージを 1 つに結合します (複数のイメージから成るフィルム ストリップなど)。  
  
- 詳しくは、「 [イメージングの概要](../graphics-multimedia/imaging-overview.md)」をご覧ください。  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 ビットマップのスケーリングをアニメーション化する場合、既定の高品質イメージの再サンプリング アルゴリズムは、フレーム レートを低下させるほどシステム リソースを消費する場合があり、実際にはアニメーションの動きが滑らかでなくなることがあります。 オブジェクトのプロパティをに<xref:System.Windows.Media.BitmapScalingMode.LowQuality>設定すると、ビットマップをスケーリングするときに、より滑らかなアニメーションを作成できます。 <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> <xref:System.Windows.Media.RenderOptions> <xref:System.Windows.Media.BitmapScalingMode.LowQuality>モードは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イメージを処理するときに品質最適化アルゴリズムから速度最適化アルゴリズムに切り替えるようにレンダリングエンジンに指示します。  
  
 次の例は、 <xref:System.Windows.Media.BitmapScalingMode>イメージオブジェクトのを設定する方法を示しています。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、は、 <xref:System.Windows.Media.DrawingBrush>や<xref:System.Windows.Media.VisualBrush>などのオブジェクト<xref:System.Windows.Media.TileBrush>の表示内容をキャッシュしません。 シーン<xref:System.Windows.Media.TileBrush>内のの内容も使用も変更されていない静的なシナリオでは、ビデオメモリを節約するため、これは理にかなっています。 静的なコンテンツ<xref:System.Windows.Media.TileBrush>を含むが静的な方法で使用されている場合 (たとえば、回転する3d オブジェクトの表面に静的<xref:System.Windows.Media.DrawingBrush>また<xref:System.Windows.Media.VisualBrush>はが割り当てられている場合)、あまり意味がありません。 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]既定の動作では、コンテンツが変更されてい<xref:System.Windows.Media.DrawingBrush>ない場合でも、すべてのフレームに対してまたは<xref:System.Windows.Media.VisualBrush>のコンテンツ全体が再レンダリングされます。  
  
 オブジェクトのプロパティをに<xref:System.Windows.Media.CachingHint.Cache>設定すると、タイル化されたブラシオブジェクトのキャッシュされたバージョンを使用してパフォーマンスを向上させることができます。 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> <xref:System.Windows.Media.RenderOptions>  
  
 プロパティ<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>値<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>とプロパティ値は、スケールの変更によっ<xref:System.Windows.Media.TileBrush>てオブジェクトを再生成するタイミングを決定する相対サイズ値です。 たとえば、 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>プロパティを2.0 に設定すると、そのサイズが現在<xref:System.Windows.Media.TileBrush>のキャッシュのサイズの2倍を超える場合にのみ、のキャッシュを再生成する必要があります。  
  
 次の例は、の<xref:System.Windows.Media.DrawingBrush>キャッシュヒントオプションを使用する方法を示しています。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
- [アニメーションのヒントとテクニック](../graphics-multimedia/animation-tips-and-tricks.md)

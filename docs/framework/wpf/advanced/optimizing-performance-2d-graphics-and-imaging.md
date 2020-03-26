---
title: 'パフォーマンスの最適化 : 2D グラフィックスとイメージング'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: eb3686367873276587572addda436471cd1abf27
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291803"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>パフォーマンスの最適化 : 2D グラフィックスとイメージング
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、アプリケーションの要件に合わせて最適化できる広範な 2D グラフィックス機能とイメージング機能が用意されています。 このトピックでは、この領域でのパフォーマンスの最適化に関する情報を提供します。  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>描画と図形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、<xref:System.Windows.Media.Drawing>グラフィック<xref:System.Windows.Shapes.Shape>図面の内容を表すオブジェクトとオブジェクトの両方が用意されています。 ただし、<xref:System.Windows.Media.Drawing>オブジェクトはオブジェクトよりも<xref:System.Windows.Shapes.Shape>単純な構造であり、パフォーマンス特性が向上します。  
  
 A<xref:System.Windows.Shapes.Shape>を使用すると、画面にグラフィカルな図形を描画できます。 オブジェクトは<xref:System.Windows.FrameworkElement>クラスから派生するため、<xref:System.Windows.Shapes.Shape>オブジェクトはパネルやほとんどのコントロールの内部で使用できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、グラフィックス サービスやレンダリング サービスへのアクセスのレイヤーがいくつか用意されています。 最上層では、<xref:System.Windows.Shapes.Shape>オブジェクトは使いやすく、レイアウトやイベント処理など、便利な機能が多数用意されています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、すぐに使用できるさまざまな図形オブジェクトが用意されています。 すべてのシェイプ オブジェクトはクラス<xref:System.Windows.Shapes.Shape>から継承されます。 使用可能な図形オブジェクト<xref:System.Windows.Shapes.Ellipse>には<xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、 <xref:System.Windows.Shapes.Rectangle>、 、 、 などがあります。  
  
 <xref:System.Windows.Media.Drawing>一方、オブジェクトは<xref:System.Windows.FrameworkElement>クラスから派生せず、図形、イメージ、およびテキストをレンダリングするための軽量化の実装を提供します。  
  
 オブジェクトには、次の<xref:System.Windows.Media.Drawing>4 つのタイプがあります。  
  
- <xref:System.Windows.Media.GeometryDrawing>図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing>イメージを描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>テキストを描画します。  
  
- <xref:System.Windows.Media.DrawingGroup>他の図面を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 オブジェクト<xref:System.Windows.Media.GeometryDrawing>は、ジオメトリの内容をレンダリングするために使用されます。 クラス<xref:System.Windows.Media.Geometry>と、そこから派生する具象クラス<xref:System.Windows.Media.CombinedGeometry><xref:System.Windows.Media.EllipseGeometry>、 などは、2D グラフィックスをレンダリングし<xref:System.Windows.Media.PathGeometry>、ヒット テストとクリッピングのサポートを提供する手段を提供します。 ジオメトリ オブジェクトを使用すると、たとえば、コントロールの領域を定義したり、イメージに適用するクリップ領域を定義したりすることができます。 ジオメトリ オブジェクトは、四角形や円などの単純な領域にすることも、2 つ以上のジオメトリ オブジェクトから作成された複合的な領域にすることもできます。 より複雑な幾何学的領域は、 、<xref:System.Windows.Media.PathSegment>など<xref:System.Windows.Media.ArcSegment><xref:System.Windows.Media.BezierSegment>派生オブジェクトを組み合わせて<xref:System.Windows.Media.QuadraticBezierSegment>作成できます。  
  
 表面的には、<xref:System.Windows.Media.Geometry>クラスと<xref:System.Windows.Shapes.Shape>クラスは似ています。 どちらも 2D グラフィックスのレンダリングで使用され、<xref:System.Windows.Media.EllipseGeometry>両方とも、それらから派生する同様の具象クラスを<xref:System.Windows.Shapes.Ellipse>持っています。 ただし、この 2 つのクラスのセットの間には重要な違いがいくつかあります。 1 つには<xref:System.Windows.Media.Geometry>、クラスには、自身を描画する機能<xref:System.Windows.Shapes.Shape>など、クラスの機能の一部が欠けている。 ジオメトリ オブジェクトを描画するには、DrawingContext、Drawing、Path (Path が Shape であることは注目に値します) などの別のクラスを使用して描画操作を実行する必要があります。 塗り、ストローク、ストロークなどのレンダリング プロパティは、ジオメトリ オブジェクトを描画するクラス上に表示され、シェイプ オブジェクトにはこれらのプロパティが含まれます。 この違いの 1 つは、ジオメトリ オブジェクトが領域 (たとえば、円) を定義し、シェイプ オブジェクトが領域を定義し、その領域の塗りつぶしとアウトラインの方法を定義し、レイアウト システムに参加するという点です。  
  
 オブジェクト<xref:System.Windows.Shapes.Shape>はクラスから派生<xref:System.Windows.FrameworkElement>するため、オブジェクトを使用すると、アプリケーションでのメモリ消費量が大幅に増加する可能性があります。 グラフィカルコンテンツの機能が本当に<xref:System.Windows.FrameworkElement>必要ない場合は、軽量<xref:System.Windows.Media.Drawing>オブジェクトの使用を検討してください。  
  
 オブジェクトの詳細については<xref:System.Windows.Media.Drawing>、「[図面オブジェクトの概要](../graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>StreamGeometry オブジェクト  
 オブジェクト<xref:System.Windows.Media.StreamGeometry>は、ジオメトリック シェイプ<xref:System.Windows.Media.PathGeometry>を作成するための軽量な代替手段です。 複雑な<xref:System.Windows.Media.StreamGeometry>ジオメトリを記述する必要がある場合に使用します。 <xref:System.Windows.Media.StreamGeometry>は、多数<xref:System.Windows.Media.PathGeometry>のオブジェクトを処理するために最適化されており、多数の個別<xref:System.Windows.Media.PathGeometry>オブジェクトを使用する場合に比べてパフォーマンスが向上します。  
  
 次の例では、属性構文を使用して、<xref:System.Windows.Media.StreamGeometry>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]三角形を作成します。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 オブジェクトの<xref:System.Windows.Media.StreamGeometry>詳細については、「 [StreamGeometry を使用して図形を作成する](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)」を参照してください。  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>DrawingVisual オブジェクト  
 オブジェクト<xref:System.Windows.Media.DrawingVisual>は、図形、イメージ、またはテキストのレンダリングに使用される軽量の描画クラスです。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。 詳しくは、「[DrawingVisual オブジェクトの使用](../graphics-multimedia/using-drawingvisual-objects.md)」をご覧ください。  
  
<a name="Images"></a>
## <a name="images"></a>イメージ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イメージングにより、以前のバージョンの Windows のイメージング機能よりも大幅に向上します。 ビットマップの表示や共通コントロールでのイメージの使用などのイメージング機能は、主に Windows グラフィックス デバイス インターフェイス (GDI) または Microsoft Windows GDI+ アプリケーション プログラミング インターフェイス (API) によって処理されました。 これらの API は、ベースライン イメージ作成機能を提供しましたが、コーデックの拡張性や忠実度の高いイメージサポートなどの機能が不足しています。 WPF イメージング API は、GDI および GDI+ の欠点を克服し、アプリケーション内でイメージを表示および使用するための新しい API セットを提供するように再設計されました。  
  
 イメージを使用する際には、パフォーマンスを向上させるために以下の推奨事項をご検討ください。  
  
- アプリケーションでサムネイル イメージを表示する必要がある場合は、縮小版のイメージを作成することをご検討ください。 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は読み込んだイメージを本来のサイズにデコードします。 サムネイル バージョンのイメージのみが必要な場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がイメージを本来のサイズにデコードしてからサムネイル サイズに縮小するという無駄が生じます。 この不要なオーバーヘッドを回避するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対してイメージをサムネイル サイズにデコードするように要求するか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にサムネイル サイズのイメージを読み込むように要求します。  
  
- イメージは常に、既定のサイズではなく必要なサイズにデコードするようにしてください。 前述のように、既定の実際のサイズではなく必要なサイズにイメージをデコードするように [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に要求します。 これにより、アプリケーションの作業セットを縮小できるだけでなく、実行速度も向上します。  
  
- 可能であれば、複数のイメージを 1 つに結合します (複数のイメージから成るフィルム ストリップなど)。  
  
- 詳細については、「[イメージングの概要」を](../graphics-multimedia/imaging-overview.md)参照してください。  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 ビットマップのスケールをアニメーション化する場合、既定の高品質イメージ リサンプリング アルゴリズムでは、フレーム レートの低下を引き起こすのに十分なシステム リソースが消費され、アニメーションが効果的に途切れることがあります。 オブジェクトのプロパティ<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>を<xref:System.Windows.Media.RenderOptions>に<xref:System.Windows.Media.BitmapScalingMode.LowQuality>設定すると、ビットマップをスケーリングするときに、より滑らかなアニメーションを作成できます。 <xref:System.Windows.Media.BitmapScalingMode.LowQuality>mode は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、イメージを処理するときに、品質最適化アルゴリズムから速度最適化アルゴリズムに切り替えるレンダリング エンジンに指示します。  
  
 イメージ オブジェクトの を設定する<xref:System.Windows.Media.BitmapScalingMode>方法を次の例に示します。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]や<xref:System.Windows.Media.TileBrush><xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.VisualBrush>などのオブジェクトのレンダリングされた内容はキャッシュされません。 シーン<xref:System.Windows.Media.TileBrush>内での コンテンツや使用が変化しない静的なシナリオでは、ビデオ メモリを節約できるため、これは意味があります。 静的コンテンツを持つ a が<xref:System.Windows.Media.TileBrush>非静的な方法で使用される場合(たとえば、静的<xref:System.Windows.Media.DrawingBrush>な 3D オブジェクトの<xref:System.Windows.Media.VisualBrush>サーフェスにマップされている場合など)、それほど意味がありません。 のデフォルトの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動作では、コンテンツが変更されていない場合でも、<xref:System.Windows.Media.DrawingBrush>フレームごとに<xref:System.Windows.Media.VisualBrush>またはすべてのフレームのコンテンツ全体を再レンダリングします。  
  
 オブジェクトのプロパティ<xref:System.Windows.Media.RenderOptions.CachingHint%2A>を<xref:System.Windows.Media.RenderOptions>に<xref:System.Windows.Media.CachingHint.Cache>設定すると、キャッシュされたバージョンのブラシ オブジェクトを使用してパフォーマンスを向上させることができます。  
  
 プロパティ<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>値<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>とは、スケールの変更によってオブジェクトを<xref:System.Windows.Media.TileBrush>再生成するタイミングを決定する相対サイズ値です。 たとえば、プロパティを<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>2.0 に設定すると、そのサイズが<xref:System.Windows.Media.TileBrush>現在のキャッシュの 2 倍のサイズを超えた場合に、キャッシュのみのキャッシュを再生成する必要があります。  
  
 次の例は、 のキャッシュ ヒント オプションを<xref:System.Windows.Media.DrawingBrush>使用する方法を示しています。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [テキスト](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
- [アニメーションのヒントとテクニック](../graphics-multimedia/animation-tips-and-tricks.md)

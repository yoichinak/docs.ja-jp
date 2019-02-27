---
title: Drawing オブジェクトの概要
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: edbb5521069caaa83dc24ca03af510d8e12f1b11
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836527"
---
# <a name="drawing-objects-overview"></a>Drawing オブジェクトの概要
このトピックでは<xref:System.Windows.Media.Drawing>オブジェクトし、それらを使用して、図形、ビットマップ、テキスト、およびメディアを効率的に描画する方法について説明します。 使用して、<xref:System.Windows.Media.Drawing>を使用して、クリップアートを作成するときに、オブジェクトのペイントを<xref:System.Windows.Media.DrawingBrush>を使用して、または<xref:System.Windows.Media.Visual>オブジェクト。  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Drawing オブジェクトとは  
 A<xref:System.Windows.Media.Drawing>オブジェクトには、図形、ビットマップ、ビデオ、または行のテキストなど、表示されるコンテンツがについて説明します。 さまざまな種類の描画で、さまざまな種類のコンテンツを記述します。 次の一覧に、さまざまな種類の描画オブジェクトを示します。  
  
-   <xref:System.Windows.Media.GeometryDrawing> – 図形を描画します。  
  
-   <xref:System.Windows.Media.ImageDrawing> – イメージを描画します。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – テキストを描画します。  
  
-   <xref:System.Windows.Media.VideoDrawing> – オーディオまたはビデオ ファイルを再生します。  
  
-   <xref:System.Windows.Media.DrawingGroup> – 他の描画を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.Drawing> オブジェクトは汎用です。使用する多くの方法がある、<xref:System.Windows.Media.Drawing>オブジェクト。  
  
-   使用してイメージとして表示できます、<xref:System.Windows.Media.DrawingImage>と<xref:System.Windows.Controls.Image>コントロール。  
  
-   と共に使用することができます、<xref:System.Windows.Media.DrawingBrush>など、オブジェクトを描画する、<xref:System.Windows.Controls.Page.Background%2A>の<xref:System.Windows.Controls.Page>します。  
  
-   外観の記述に使用することができます、<xref:System.Windows.Media.DrawingVisual>します。  
  
-   内容を列挙するために使用することができます、<xref:System.Windows.Media.Visual>します。  
  
 WPF には、図形、ビットマップ、テキスト、メディアを描画できる他の型のオブジェクトが用意されています。 たとえば、使用することできますも<xref:System.Windows.Shapes.Shape>、図形を描画するオブジェクト、<xref:System.Windows.Controls.MediaElement>コントロールには、ビデオ、アプリケーションを追加する別の方法が用意されています。 これを使用すると<xref:System.Windows.Media.Drawing>オブジェクトでしょうか。 パフォーマンスを向上するフレームワーク レベルの機能を犠牲にする必要がある場合または<xref:System.Windows.Freezable>機能します。 <xref:System.Windows.Media.Drawing>オブジェクトに対応していない[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)、入力、および、集中できるように、低レベルの描画の背景の記述、クリップアート、最適なパフォーマンス上の利点を提供する<xref:System.Windows.Media.Visual>オブジェクト。  
  
 型であるため<xref:System.Windows.Freezable>オブジェクト、<xref:System.Windows.Media.Drawing>オブジェクトは、次を含むいくつかの特別な機能を得る: と宣言されている[リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)、向上させるために読み取り専用の複数のオブジェクト間で共有パフォーマンス、複製され、スレッド セーフです。 によって提供されるさまざまな機能の詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)します。  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>図形の描画  
 使用する図形を描画するために、<xref:System.Windows.Media.GeometryDrawing>します。 ジオメトリ描画の<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>プロパティを描画する図形を記述するその<xref:System.Windows.Media.GeometryDrawing.Brush%2A>プロパティは、図形の内部の描画する方法について説明しますとその<xref:System.Windows.Media.GeometryDrawing.Pen%2A>プロパティは、アウトラインを描画する方法について説明します。  
  
 次の例では、<xref:System.Windows.Media.GeometryDrawing>な図形を描画します。 図形は、<xref:System.Windows.Media.GeometryGroup>と 2 つ<xref:System.Windows.Media.EllipseGeometry>オブジェクト。 図形の内部を塗りつぶす、<xref:System.Windows.Media.LinearGradientBrush>アウトラインの描画に使用して、 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>します。  
  
 この例は、次を作成します<xref:System.Windows.Media.GeometryDrawing>します。  
  
 ![2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 完全な例については、「[GeometryDrawing を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md)」をご覧ください。  
  
 その他の<xref:System.Windows.Media.Geometry>などのクラス<xref:System.Windows.Media.PathGeometry>曲線や円弧を作成してより複雑な図形を作成することができます。 詳細については<xref:System.Windows.Media.Geometry>、オブジェクトを参照してください、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)します。  
  
 使用していない図形を描画するには、他の方法の詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください[図形と基本描画の WPF の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)します。  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>イメージの描画  
 使用するイメージを描画するために、<xref:System.Windows.Media.ImageDrawing>します。 <xref:System.Windows.Media.ImageDrawing>オブジェクトの<xref:System.Windows.Media.ImageDrawing.ImageSource%2A>プロパティを描画するイメージの説明とその<xref:System.Windows.Media.ImageDrawing.Rect%2A>プロパティは、イメージの描画領域を定義します。  
  
 次の例では、(75,75) に存在する 100 x 100 ピクセルの四角形にイメージを描画します。 次の図は、<xref:System.Windows.Media.ImageDrawing>の例で作成します。 灰色の枠線が表示の境界に追加された、<xref:System.Windows.Media.ImageDrawing>します。  
  
 ![100 × 100 の ImageDrawing に描画&#40;75, 75&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100×100 の ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 イメージについて詳しくは、「[イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)」をご覧ください。  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>メディアの再生 (コードのみ)  
  
> [!NOTE]
>  宣言することもできます、<xref:System.Windows.Media.VideoDrawing>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、だけことができますを読み込むし、コードを使用して、そのメディアを再生します。 ビデオを再生する[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を使用して、<xref:System.Windows.Controls.MediaElement>代わりにします。  
  
 使用するオーディオまたはビデオ ファイルを再生するには<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>します。 メディアを読み込んで再生するには、2 つの方法があります。 1 つ目は、使用する、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>自体を 2 番目の方法は、独自に作成する<xref:System.Windows.Media.MediaTimeline>で使用する、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>します。  
  
> [!NOTE]
>  アプリケーションでメディアを配布するときは、イメージのようにプロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
 独自に作成しないでメディアを再生する<xref:System.Windows.Media.MediaTimeline>、次の手順を実行します。  
  
1.  <xref:System.Windows.Media.MediaPlayer> オブジェクトを作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  使用して、<xref:System.Windows.Media.MediaPlayer.Open%2A>メディア ファイルを読み込みます。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  <xref:System.Windows.Media.VideoDrawing> を作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  指定サイズと位置を設定して、メディアを描画するために、<xref:System.Windows.Media.VideoDrawing.Rect%2A>のプロパティ、<xref:System.Windows.Media.VideoDrawing>します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  設定、<xref:System.Windows.Media.VideoDrawing.Player%2A>のプロパティ、<xref:System.Windows.Media.VideoDrawing>で、<xref:System.Windows.Media.MediaPlayer>を作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  使用して、<xref:System.Windows.Media.MediaPlayer.Play%2A>のメソッド、<xref:System.Windows.Media.MediaPlayer>メディアの再生を開始します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 次の例では、<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>をビデオ ファイルを 1 回再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 使用して、メディアを介した追加のタイミングを制御する、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>オブジェクト。 <xref:System.Windows.Media.MediaTimeline>ビデオを繰り返す必要があるかどうかを指定することができます。 使用する、<xref:System.Windows.Media.MediaTimeline>で、 <xref:System.Windows.Media.VideoDrawing>、次の手順を実行します。  
  
1.  宣言、<xref:System.Windows.Media.MediaTimeline>し、そのタイミング動作を設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  作成、<xref:System.Windows.Media.MediaClock>から、<xref:System.Windows.Media.MediaTimeline>します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  作成、<xref:System.Windows.Media.MediaPlayer>を使用して、<xref:System.Windows.Media.MediaClock>設定をその<xref:System.Windows.Media.MediaPlayer.Clock%2A>プロパティ。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  作成、<xref:System.Windows.Media.VideoDrawing>を割り当てると、<xref:System.Windows.Media.MediaPlayer>を<xref:System.Windows.Media.VideoDrawing.Player%2A>のプロパティ、<xref:System.Windows.Media.VideoDrawing>します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 次の例では、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>ビデオを繰り返し再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 使用すると、 <xref:System.Windows.Media.MediaTimeline>、対話型を使用する<xref:System.Windows.Media.Animation.ClockController>から返される、<xref:System.Windows.Media.Animation.Clock.Controller%2A>のプロパティ、<xref:System.Windows.Media.MediaClock>の対話型のメソッドではなくメディア再生を制御する<xref:System.Windows.Media.MediaPlayer>。  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>テキストの描画  
 使用するテキストを描画するために、<xref:System.Windows.Media.GlyphRunDrawing>と<xref:System.Windows.Media.GlyphRun>します。 次の例では、 <xref:System.Windows.Media.GlyphRunDrawing> "Hello World"テキストを描画します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A<xref:System.Windows.Media.GlyphRun>は固定形式のドキュメント プレゼンテーションと印刷のシナリオで使用するための低レベル オブジェクトです。 画面にテキストを描画する簡単な方法は使用する、<xref:System.Windows.Controls.Label>または<xref:System.Windows.Controls.TextBlock>します。 詳細については<xref:System.Windows.Media.GlyphRun>を参照してください、 [GlyphRun オブジェクトと Glyphs 要素の概要](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)の概要。  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>複合描画  
 A<xref:System.Windows.Media.DrawingGroup>複数の描画を 1 つの複合描画を結合することができます。 使用して、 <xref:System.Windows.Media.DrawingGroup>、図形、イメージ、およびテキストを 1 つに結合できます<xref:System.Windows.Media.Drawing>オブジェクト。  
  
 次の例では、<xref:System.Windows.Media.DrawingGroup>を 2 つを組み合わせる<xref:System.Windows.Media.GeometryDrawing>オブジェクトおよび<xref:System.Windows.Media.ImageDrawing>オブジェクト。 この例を実行すると、次の出力が生成されます。  
  
 ![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
複合描画  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A<xref:System.Windows.Media.DrawingGroup>不透明マスク、変換、ビットマップ効果、およびその他の操作をその内容に適用することもできます。 <xref:System.Windows.Media.DrawingGroup> 操作は、次の順序で適用されます: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、し<xref:System.Windows.Media.DrawingGroup.Transform%2A>します。  
  
 次の図は、これで順序を示します<xref:System.Windows.Media.DrawingGroup>操作が適用されます。  
  
 ![操作の DrawingGroup 順序](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup の操作の順序  
  
 次の表に、操作に使用できるプロパティ、<xref:System.Windows.Media.DrawingGroup>オブジェクトの内容。  
  
|プロパティ|説明|図|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|選択した部分の不透明度を変更、<xref:System.Windows.Media.DrawingGroup>内容。 例については、「[方法: 描画の不透明度を制御](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))します。|![不透明マスクを含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|不透明度を一様に変更、<xref:System.Windows.Media.DrawingGroup>内容。 このプロパティを使用して、<xref:System.Windows.Media.Drawing>透明または部分的にします。 例については、「[方法: 不透明度マスクを描画に適用する](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))します。|![不透明度の設定が異なる DrawingGroups](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|適用対象を<xref:System.Windows.Media.Effects.BitmapEffect>を<xref:System.Windows.Media.DrawingGroup>内容。 例については、「[方法: BitmapEffect を描画に適用する](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))します。|![BlurBitmapEffect のある DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|クリップ、<xref:System.Windows.Media.DrawingGroup>を使ってを記述した領域に内容を<xref:System.Windows.Media.Geometry>します。 例については、「[方法: 描画をクリップ](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90))します。|![クリップ領域が定義された DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|デバイスに依存しないピクセルを、指定したガイドラインに沿ったデバイス ピクセルにスナップします。 このプロパティは、低解像度ディスプレイで、非常に詳細なグラフィックスがはっきりとレンダリングされるようにするのに便利です。 例については、「[方法 : 描画に GuidelineSet を適用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md)」をご覧ください。|![GuidelineSet が有効/無効な DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|変換、<xref:System.Windows.Media.DrawingGroup>内容。 例については、「[方法: 図面に変換を適用](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))します。|![回転された DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>描画をイメージとして表示する  
 表示する、<xref:System.Windows.Media.Drawing>で、<xref:System.Windows.Controls.Image>コントロールを使用して、<xref:System.Windows.Media.DrawingImage>として、<xref:System.Windows.Controls.Image>コントロールの<xref:System.Windows.Controls.Image.Source%2A>設定と、<xref:System.Windows.Media.DrawingImage>オブジェクトの<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>プロパティを表示する描画。  
  
 次の例では、<xref:System.Windows.Media.DrawingImage>と<xref:System.Windows.Controls.Image>を表示するコントロールを<xref:System.Windows.Media.GeometryDrawing>します。 この例を実行すると、次の出力が生成されます。  
  
 ![2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>描画によるオブジェクトの塗りつぶし  
 A<xref:System.Windows.Media.DrawingBrush>は描画オブジェクトを使用して領域を描画するブラシの一種です。 描画でほとんどすべてのグラフィカル オブジェクトを塗りつぶすために使うことができます。 <xref:System.Windows.Media.Drawing>のプロパティを<xref:System.Windows.Media.DrawingBrush>について説明します、<xref:System.Windows.Media.DrawingBrush.Drawing%2A>します。 表示するために、<xref:System.Windows.Media.Drawing>で、 <xref:System.Windows.Media.DrawingBrush>、ブラシを使用して、ブラシに追加<xref:System.Windows.Media.Drawing>プロパティとコントロールなど、オブジェクトまたはパネル グラフィカルな描画するブラシを使用します。  
  
 次の例では、<xref:System.Windows.Media.DrawingBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>から作成されたパターンを持つ、<xref:System.Windows.Media.GeometryDrawing>します。 この例を実行すると、次の出力が生成されます。  
  
 ![タイル表示の DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush で使われる GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush>クラスには、さまざまな拡大したり、コンテンツを並べて表示するためのオプションが用意されています。 詳細については<xref:System.Windows.Media.DrawingBrush>を参照してください、[イメージ、描画、およびビジュアル](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)の概要。  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>ビジュアルで描画をレンダリングする  
 A<xref:System.Windows.Media.DrawingVisual>は描画をレンダリングするためのビジュアル オブジェクトの一種です。 高度にカスタマイズされたグラフィカル環境を構築したい開発者は、ビジュアル レイヤーを直接操作できますが、この概要ではそれについては説明しません。 詳しくは、「[DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)」をご覧ください。  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext オブジェクト  
 <xref:System.Windows.Media.DrawingContext>クラスでは、設定することができます、<xref:System.Windows.Media.Visual>または<xref:System.Windows.Media.Drawing>にビジュアル コンテンツ。 このような多くの低レベルのグラフィック オブジェクトを使用して、<xref:System.Windows.Media.DrawingContext>グラフィカル コンテンツを非常に効率よく記述できるため、します。  
  
 ですが、<xref:System.Windows.Media.DrawingContext>の描画メソッドのような描画メソッドが表示されます、<xref:System.Drawing.Graphics?displayProperty=nameWithType>型が実際には非常に異なります。 <xref:System.Windows.Media.DrawingContext> 保持モード グラフィックス システムで使用中に、<xref:System.Drawing.Graphics?displayProperty=nameWithType>型はイミディ エイト モード グラフィックス システムで使用します。 使用すると、<xref:System.Windows.Media.DrawingContext>オブジェクトの描画コマンド、レンダリング命令のセットを実際に格納する (厳密なストレージ メカニズムを提供するオブジェクトの種類によって異なります、 <xref:System.Windows.Media.DrawingContext>)、グラフィックスによって後で使用されるシステムはリアルタイムの画面に描画されません。 Windows Presentation Foundation (WPF) のグラフィックス システムのしくみの詳細については、次を参照してください。、 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)します。  
  
 決して直接インスタンス化する、 <xref:System.Windows.Media.DrawingContext>; など、特定のメソッドから描画コンテキストを取得することができます、ただし、<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>します。  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>ビジュアルの内容の列挙  
 その他の使用方法だけでなく<xref:System.Windows.Media.Drawing>オブジェクトの内容を列挙するオブジェクト モデルは用意も、<xref:System.Windows.Media.Visual>します。  
  
 次の例では、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>を取得するメソッド、<xref:System.Windows.Media.DrawingGroup>の値を<xref:System.Windows.Media.Visual>し、それを列挙します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)

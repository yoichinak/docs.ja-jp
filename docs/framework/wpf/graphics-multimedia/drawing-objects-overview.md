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
ms.openlocfilehash: d739865a692fa5ef448eba91369015580e5eda97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916310"
---
# <a name="drawing-objects-overview"></a>Drawing オブジェクトの概要
ここでは、オブジェクトについて説明し、オブジェクトを使用して図形、ビットマップ、テキスト、およびメディアを効率的に描画する方法について説明します。<xref:System.Windows.Media.Drawing> オブジェクト<xref:System.Windows.Media.Drawing>は、クリップアートを作成するとき、を<xref:System.Windows.Media.DrawingBrush>使用して<xref:System.Windows.Media.Visual>描画するとき、またはオブジェクトを使用するときに使用します。  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Drawing オブジェクトとは  
 オブジェクト<xref:System.Windows.Media.Drawing>は、形状、ビットマップ、ビデオ、テキスト行など、表示される内容を記述します。 さまざまな種類の描画で、さまざまな種類のコンテンツを記述します。 次の一覧に、さまざまな種類の描画オブジェクトを示します。  
  
- <xref:System.Windows.Media.GeometryDrawing>–図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing>–イメージを描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>–テキストを描画します。  
  
- <xref:System.Windows.Media.VideoDrawing>–オーディオファイルまたはビデオファイルを再生します。  
  
- <xref:System.Windows.Media.DrawingGroup>–他の描画を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.Drawing>オブジェクトはさまざまです。オブジェクトを使用するには、 <xref:System.Windows.Media.Drawing>さまざまな方法があります。  
  
- <xref:System.Windows.Media.DrawingImage>とコントロールを使用して、イメージとして表示できます。<xref:System.Windows.Controls.Image>  
  
- これをと共<xref:System.Windows.Media.DrawingBrush>に使用し<xref:System.Windows.Controls.Page.Background%2A>て、のなどの<xref:System.Windows.Controls.Page>オブジェクトを描画できます。  
  
- このメソッドを使用して、 <xref:System.Windows.Media.DrawingVisual>の外観を記述できます。  
  
- このメソッドを使用して、 <xref:System.Windows.Media.Visual>の内容を列挙できます。  
  
 WPF には、図形、ビットマップ、テキスト、メディアを描画できる他の型のオブジェクトが用意されています。 たとえば、オブジェクトを使用<xref:System.Windows.Shapes.Shape>して図形を描画することもできます。また、コントロールは、 <xref:System.Windows.Controls.MediaElement>アプリケーションにビデオを追加する別の方法を提供します。 では、どのよう<xref:System.Windows.Media.Drawing>な場合にオブジェクトを使用すればよいでしょうか。 フレームワークレベルの機能を犠牲にして、パフォーマンス上の利点を<xref:System.Windows.Freezable>得ることができる場合や、機能が必要な場合。 オブジェクト<xref:System.Windows.Media.Drawing>の[レイアウト](../advanced/layout.md)、入力、およびフォーカスはサポートされていないため、オブジェクトを使用した背景、クリップアート、および低レベルの描画に最適<xref:System.Windows.Media.Visual>なパフォーマンス上の利点が得られます。  
  
 オブジェクトは型<xref:System.Windows.Freezable>オブジェクトであるため<xref:System.Windows.Media.Drawing> 、オブジェクトには、[リソース](../advanced/xaml-resources.md)として宣言したり、複数のオブジェクト間で共有したり、パフォーマンスを向上させるために読み取り専用にしたりできる、次のようないくつかの特殊な機能があります。スレッドセーフになりました。 オブジェクトによっ<xref:System.Windows.Freezable>て提供されるさまざまな機能の詳細については、「 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」を参照してください。  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>図形の描画  
 図形を描画するには、を<xref:System.Windows.Media.GeometryDrawing>使用します。 ジオメトリ描画の<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>プロパティは描画する図形を記述し、 <xref:System.Windows.Media.GeometryDrawing.Brush%2A>そのプロパティは図形の内部を描画する方法を記述し、 <xref:System.Windows.Media.GeometryDrawing.Pen%2A>そのプロパティはその輪郭を描画する方法を記述します。  
  
 次の例では<xref:System.Windows.Media.GeometryDrawing> 、を使用して図形を描画します。 図形は、との 2 <xref:System.Windows.Media.GeometryGroup>つ<xref:System.Windows.Media.EllipseGeometry>のオブジェクトによって記述されます。 図形の内部はを<xref:System.Windows.Media.LinearGradientBrush>使用して描画され、その輪郭はで描画<xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>されます。  
  
 この例では、 <xref:System.Windows.Media.GeometryDrawing>次のものが作成されます。  
  
 ![2 つの楕円の GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 完全な例については、「[GeometryDrawing を作成する](how-to-create-a-geometrydrawing.md)」をご覧ください。  
  
 など<xref:System.Windows.Media.Geometry>の他のクラス<xref:System.Windows.Media.PathGeometry>を使用すると、曲線と円弧を作成することにより、より複雑な図形を作成できます。 <xref:System.Windows.Media.Geometry>オブジェクトの詳細については、「 [Geometry の概要](geometry-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Drawing> オブジェクトを使用していない図形を描画する他の方法の詳細については、「[WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)」を参照してください。  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>イメージの描画  
 イメージを描画するには<xref:System.Windows.Media.ImageDrawing>、を使用します。 オブジェクト<xref:System.Windows.Media.ImageDrawing>の<xref:System.Windows.Media.ImageDrawing.ImageSource%2A>プロパティは描画するイメージを記述し、その<xref:System.Windows.Media.ImageDrawing.Rect%2A>プロパティはイメージが描画される領域を定義します。  
  
 次の例では、(75,75) に存在する 100 x 100 ピクセルの四角形にイメージを描画します。 次の図は、 <xref:System.Windows.Media.ImageDrawing>この例によって作成されたを示しています。 の境界を表示するために、 <xref:System.Windows.Media.ImageDrawing>灰色の枠線が追加されました。  
  
 ![75、75 &#40;&#41;で描画された 100/100 imagedrawing](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100×100 の ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 イメージについて詳しくは、「[イメージングの概要](imaging-overview.md)」をご覧ください。  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>メディアの再生 (コードのみ)  
  
> [!NOTE]
> <xref:System.Windows.Media.VideoDrawing> で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]はを宣言できますが、コードを使用してのみ、そのメディアの読み込みと再生を行うことができます。 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ビデオを再生するには<xref:System.Windows.Controls.MediaElement> 、代わりにを使用します。  
  
 オーディオファイルまたはビデオファイルを再生するには<xref:System.Windows.Media.VideoDrawing> 、 <xref:System.Windows.Media.MediaPlayer>とを使用します。 メディアを読み込んで再生するには、2 つの方法があります。 1つ目の方法は<xref:System.Windows.Media.MediaPlayer> 、 <xref:System.Windows.Media.VideoDrawing>とを単独で使用することです。2番目の<xref:System.Windows.Media.MediaTimeline>方法は、 <xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>で使用する独自のを作成することです。  
  
> [!NOTE]
> アプリケーションでメディアを配布するときは、イメージのようにプロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
 独自<xref:System.Windows.Media.MediaTimeline>のメディアを作成せずにメディアを再生するには、次の手順を実行します。  
  
1. <xref:System.Windows.Media.MediaPlayer> オブジェクトを作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. メディアファイル<xref:System.Windows.Media.MediaPlayer.Open%2A>を読み込むには、メソッドを使用します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. <xref:System.Windows.Media.VideoDrawing> を作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. のプロパティ<xref:System.Windows.Media.VideoDrawing.Rect%2A>を設定して、メディアを描画するサイズと場所を指定します。<xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. 作成し<xref:System.Windows.Media.VideoDrawing.Player%2A>たを使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>して、のプロパティを設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. のメソッドを使用して、メディアの再生を開始します。<xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaPlayer.Play%2A>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 次の例では<xref:System.Windows.Media.VideoDrawing> 、と<xref:System.Windows.Media.MediaPlayer>を使用して、ビデオファイルを1回再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 メディアに対する追加のタイミング制御を取得するに<xref:System.Windows.Media.MediaTimeline>は、 <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>オブジェクトとオブジェクトを使用してを使用します。 を<xref:System.Windows.Media.MediaTimeline>使用すると、ビデオを繰り返し表示するかどうかを指定できます。 <xref:System.Windows.Media.MediaTimeline> を<xref:System.Windows.Media.VideoDrawing>と共に使用するには、次の手順を実行します。  
  
1. を宣言し、そのタイミング動作を設定します。<xref:System.Windows.Media.MediaTimeline>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. からを<xref:System.Windows.Media.MediaClock>作成します。<xref:System.Windows.Media.MediaTimeline>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. を<xref:System.Windows.Media.MediaPlayer>作成し、 <xref:System.Windows.Media.MediaClock>を使用して<xref:System.Windows.Media.MediaPlayer.Clock%2A>そのプロパティを設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. を<xref:System.Windows.Media.VideoDrawing>作成し、の<xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing.Player%2A>プロパティ<xref:System.Windows.Media.VideoDrawing>にを割り当てます。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 次の例では<xref:System.Windows.Media.MediaTimeline> 、 <xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing> a を使用して、ビデオを繰り返し再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 を<xref:System.Windows.Media.MediaTimeline>使用する場合は、の<xref:System.Windows.Media.Animation.Clock.Controller%2A>プロパティ<xref:System.Windows.Media.MediaClock>から返された<xref:System.Windows.Media.Animation.ClockController>対話型のを使用して、の<xref:System.Windows.Media.MediaPlayer>対話型メソッドではなくメディアの再生を制御することに注意してください。  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>テキストの描画  
 テキストを描画するには、 <xref:System.Windows.Media.GlyphRunDrawing> <xref:System.Windows.Media.GlyphRun>とを使用します。 次の例では<xref:System.Windows.Media.GlyphRunDrawing> 、を使用して、"Hello World" というテキストを描画します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun>は、固定形式のドキュメントプレゼンテーションおよび印刷シナリオで使用するための低レベルのオブジェクトです。 画面にテキストを描画するためのより簡単な方法は<xref:System.Windows.Controls.Label> 、 <xref:System.Windows.Controls.TextBlock>またはを使用することです。 の詳細<xref:System.Windows.Media.GlyphRun>については、「 [GlyphRun オブジェクトと Glyphs 要素の](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)概要」を参照してください。  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>複合描画  
 を<xref:System.Windows.Media.DrawingGroup>使用すると、複数の描画を1つの複合描画に結合できます。 を使用<xref:System.Windows.Media.DrawingGroup>すると、図形、画像、およびテキストを1つ<xref:System.Windows.Media.Drawing>のオブジェクトに結合できます。  
  
 次の例では<xref:System.Windows.Media.DrawingGroup> 、を使用<xref:System.Windows.Media.GeometryDrawing>して、 <xref:System.Windows.Media.ImageDrawing> 2 つのオブジェクトと1つのオブジェクトを結合します。 この例を実行すると、次の出力が生成されます。  
  
 ![複数の描画を含む図面グループ](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
複合描画  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 また<xref:System.Windows.Media.DrawingGroup> 、を使用すると、不透明マスク、変換、ビットマップ効果などの操作をその内容に適用できます。 <xref:System.Windows.Media.DrawingGroup>操作<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>は<xref:System.Windows.Media.DrawingGroup.Opacity%2A>、、、 、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、、および<xref:System.Windows.Media.DrawingGroup.Transform%2A>の順に適用されます。 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
  
 次の図は、操作が適用<xref:System.Windows.Media.DrawingGroup>される順序を示しています。  
  
 ![操作の図面グループの順序](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup の操作の順序  
  
 次の表では、オブジェクトのコンテンツを<xref:System.Windows.Media.DrawingGroup>操作するために使用できるプロパティについて説明します。  
  
|プロパティ|説明|図|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|<xref:System.Windows.Media.DrawingGroup>コンテンツの選択部分の不透明度を変更します。 例については、「[方法: 描画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))の不透明度を制御します。|![不透明マスクを含む DrawingGroup](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|<xref:System.Windows.Media.DrawingGroup>コンテンツの不透明度を均一に変更します。 このプロパティを使用して<xref:System.Windows.Media.Drawing> 、透明または部分的に透明にします。 例については、「[方法: 不透明度マスクを描画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))に適用します。|![不透明度の設定が異なる DrawingGroups](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|コンテンツにを<xref:System.Windows.Media.Effects.BitmapEffect>適用します。 <xref:System.Windows.Media.DrawingGroup> 例については、「[方法: BitmapEffect を描画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))に適用します。|![BlurBitmapEffect のある DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|<xref:System.Windows.Media.DrawingGroup> を<xref:System.Windows.Media.Geometry>使用して、記述した領域にコンテンツをクリップします。 例については、「[方法: 描画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90))をクリップします。|![クリップ領域が定義された DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|デバイスに依存しないピクセルを、指定したガイドラインに沿ったデバイス ピクセルにスナップします。 このプロパティは、低解像度ディスプレイで、非常に詳細なグラフィックスがはっきりとレンダリングされるようにするのに便利です。 例については、「[方法 : 描画に GuidelineSet を適用する](how-to-apply-a-guidelineset-to-a-drawing.md)」をご覧ください。|![GuidelineSet が有効/無効な DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|コンテンツを<xref:System.Windows.Media.DrawingGroup>変換します。 例については、「[方法: 描画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))に変換を適用します。|![回転された DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>描画をイメージとして表示する  
 <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>コントロールを<xref:System.Windows.Controls.Image.Source%2A>使用してを表示するには、をコントロールのとして使用し、オブジェクトのプロパティを表示する描画に設定します。 <xref:System.Windows.Controls.Image>  
  
 次の例では<xref:System.Windows.Media.DrawingImage> 、 <xref:System.Windows.Controls.Image>およびコントロールを使用し<xref:System.Windows.Media.GeometryDrawing>てを表示します。 この例を実行すると、次の出力が生成されます。  
  
 ![2 つの楕円の GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>描画によるオブジェクトの塗りつぶし  
 は、描画オブジェクトを使用して領域を塗りつぶすブラシの一種です。<xref:System.Windows.Media.DrawingBrush> 描画でほとんどすべてのグラフィカル オブジェクトを塗りつぶすために使うことができます。 の<xref:System.Windows.Media.Drawing>プロパティは、 <xref:System.Windows.Media.DrawingBrush>その<xref:System.Windows.Media.DrawingBrush.Drawing%2A>を記述します。 を<xref:System.Windows.Media.Drawing> 使用し<xref:System.Windows.Media.Drawing>てをレンダリングするには、ブラシのプロパティを使用してブラシにそれを追加し、ブラシを使用してコントロールやパネルなどのグラフィカルオブジェクトを描画します。<xref:System.Windows.Media.DrawingBrush>  
  
 次の例では<xref:System.Windows.Media.DrawingBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle> 、から<xref:System.Windows.Media.GeometryDrawing>作成されたパターンでのを描画します。 この例を実行すると、次の出力が生成されます。  
  
 ![タイル化 DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush で使われる GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 クラス<xref:System.Windows.Media.DrawingBrush>には、コンテンツを拡大してタイル表示するためのさまざまなオプションが用意されています。 の詳細<xref:System.Windows.Media.DrawingBrush>については、「[イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)の概要」を参照してください。  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>ビジュアルで描画をレンダリングする  
 <xref:System.Windows.Media.DrawingVisual>は、描画をレンダリングするように設計されたビジュアルオブジェクトの一種です。 高度にカスタマイズされたグラフィカル環境を構築したい開発者は、ビジュアル レイヤーを直接操作できますが、この概要ではそれについては説明しません。 詳しくは、「[DrawingVisual オブジェクトの使用](using-drawingvisual-objects.md)」をご覧ください。  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext オブジェクト  
 クラスを使用すると、 <xref:System.Windows.Media.Visual>また<xref:System.Windows.Media.Drawing>はにビジュアルコンテンツを設定できます。 <xref:System.Windows.Media.DrawingContext> このような下位レベルのグラフィックスオブジェクトの<xref:System.Windows.Media.DrawingContext>多くは、グラフィカルなコンテンツを非常に効率的に記述しているため、を使用します。  
  
 描画メソッド<xref:System.Windows.Media.DrawingContext>は、 <xref:System.Drawing.Graphics?displayProperty=nameWithType>型の描画メソッドと同様に表示されますが、実際にはまったく異なります。 <xref:System.Windows.Media.DrawingContext>は、保持モードのグラフィックスシステム<xref:System.Drawing.Graphics?displayProperty=nameWithType>で使用されますが、型はイミディエイトモードのグラフィックスシステムで使用されます。 <xref:System.Windows.Media.DrawingContext>オブジェクトの描画コマンドを使用する場合、実際には、レンダリング命令のセットを格納します (ただし、正確なストレージメカニズムはを提供するオブジェクト<xref:System.Windows.Media.DrawingContext>の型に依存しますが、これは後でグラフィックスシステムによって使用されます)。リアルタイムで画面に描画されません。 Windows Presentation Foundation (WPF) グラフィックスシステムの動作の詳細については、「 [Wpf グラフィックスレンダリングの概要](wpf-graphics-rendering-overview.md)」を参照してください。  
  
 を<xref:System.Windows.Media.DrawingContext>直接インスタンス化することはありません。ただし、 <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType>や<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>などの特定のメソッドから描画コンテキストを取得することはできます。  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>ビジュアルの内容の列挙  
 <xref:System.Windows.Media.Drawing>オブジェクトは、他の用途に加えて、 <xref:System.Windows.Media.Visual>のコンテンツを列挙するためのオブジェクトモデルも提供します。  
  
 次の例では<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> 、メソッドを使用<xref:System.Windows.Media.DrawingGroup>しての<xref:System.Windows.Media.Visual>値を取得し、それを列挙します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [ジオメトリの概要](geometry-overview.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [方法トピック](drawings-how-to-topics.md)

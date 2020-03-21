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
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186536"
---
# <a name="drawing-objects-overview"></a>Drawing オブジェクトの概要
このトピックでは<xref:System.Windows.Media.Drawing>、オブジェクトを紹介し、それらを使用して図形、ビットマップ、テキスト、およびメディアを効率的に描画する方法について説明します。 クリップ アートを作成したり、でペイントしたり、<xref:System.Windows.Media.DrawingBrush>オブジェクトを使用<xref:System.Windows.Media.Visual>したりする場合は、オブジェクトを使用します。 <xref:System.Windows.Media.Drawing>  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Drawing オブジェクトとは  
 オブジェクト<xref:System.Windows.Media.Drawing>は、図形、ビットマップ、ビデオ、テキスト行などの表示されるコンテンツを表します。 さまざまな種類の描画で、さまざまな種類のコンテンツを記述します。 次の一覧に、さまざまな種類の描画オブジェクトを示します。  
  
- <xref:System.Windows.Media.GeometryDrawing>– 図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing>– 画像を描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– テキストを描画します。  
  
- <xref:System.Windows.Media.VideoDrawing>– オーディオまたはビデオファイルを再生します。  
  
- <xref:System.Windows.Media.DrawingGroup>– 他の図面を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.Drawing>オブジェクトは汎用性があります。<xref:System.Windows.Media.Drawing>オブジェクトを使用する方法は多数あります。  
  
- コントロール<xref:System.Windows.Media.DrawingImage>と<xref:System.Windows.Controls.Image>を使用して、イメージとして表示できます。  
  
- を使用して、 の<xref:System.Windows.Media.DrawingBrush>オブジェクトなどの<xref:System.Windows.Controls.Page.Background%2A>オブジェクトを<xref:System.Windows.Controls.Page>ペイントできます。  
  
- この機能を使用して、 の外観を<xref:System.Windows.Media.DrawingVisual>記述できます。  
  
- この機能を使用して、 の内容を<xref:System.Windows.Media.Visual>列挙できます。  
  
 WPF には、図形、ビットマップ、テキスト、メディアを描画できる他の型のオブジェクトが用意されています。 たとえば、オブジェクトを使用<xref:System.Windows.Shapes.Shape>して図形を描画したり、コントロールを<xref:System.Windows.Controls.MediaElement>使用してアプリケーションにビデオを追加することもできます。 では、オブジェクトを使用<xref:System.Windows.Media.Drawing>する必要がある場合は? フレームワーク レベルの機能を犠牲にしてパフォーマンス上のメリットを得<xref:System.Windows.Freezable>ることができる場合や、機能が必要な場合。 <xref:System.Windows.Media.Drawing>[オブジェクトはレイアウト](../advanced/layout.md)、入力、フォーカスをサポートしていないため、背景、クリップ アート、オブジェクトを使用した低レベルの描画に最適なパフォーマンス上の利点を<xref:System.Windows.Media.Visual>提供します。  
  
 オブジェクトは型<xref:System.Windows.Freezable>オブジェクトであるため、<xref:System.Windows.Media.Drawing>リソースとして宣言したり、複数[の](../../../desktop-wpf/fundamentals/xaml-resources-define.md)オブジェクト間で共有したり、読み取り専用にしてパフォーマンスを向上させたり、クローンを作成したり、スレッドセーフにしたりできる、いくつかの特別な機能を持ちます。 オブジェクトによって<xref:System.Windows.Freezable>提供されるさまざまな機能の詳細については、 [[フリーザブル オブジェクトの概要](../advanced/freezable-objects-overview.md)] を参照してください。  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>図形の描画  
 図形を描画するには、 を使用<xref:System.Windows.Media.GeometryDrawing>します。 ジオメトリ図面の<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>プロパティは、描画するシェイプを記述し、その<xref:System.Windows.Media.GeometryDrawing.Brush%2A>プロパティは、シェイプの内部を描画する方法を記述し、その<xref:System.Windows.Media.GeometryDrawing.Pen%2A>プロパティは、そのアウトラインを描画する方法を記述します。  
  
 次の例では、<xref:System.Windows.Media.GeometryDrawing>を使用して図形を描画します。 図形は a<xref:System.Windows.Media.GeometryGroup>および 2<xref:System.Windows.Media.EllipseGeometry>つのオブジェクトで記述されます。 図形の内部は で塗りつぶ<xref:System.Windows.Media.LinearGradientBrush>され、アウトラインは で描画されます。 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>  
  
 この例では、次<xref:System.Windows.Media.GeometryDrawing>のを作成します。  
  
 ![2 つの楕円の GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 完全な例については、「[GeometryDrawing を作成する](how-to-create-a-geometrydrawing.md)」をご覧ください。  
  
 他<xref:System.Windows.Media.Geometry>のクラス(例<xref:System.Windows.Media.PathGeometry>えば、曲線や円弧を作成することによってより複雑な形状を作成できます)。 オブジェクトの<xref:System.Windows.Media.Geometry>詳細については、「[ジオメトリの概要](geometry-overview.md)」を参照してください。  
  
 オブジェクトを使用<xref:System.Windows.Media.Drawing>しない図形を描画する他の方法の詳細については、「 [WPF の図形と基本的な描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)」を参照してください。  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>イメージの描画  
 イメージを描画するには、 を使用<xref:System.Windows.Media.ImageDrawing>します。 オブジェクト<xref:System.Windows.Media.ImageDrawing>の<xref:System.Windows.Media.ImageDrawing.ImageSource%2A>プロパティは描画するイメージを記述し、その<xref:System.Windows.Media.ImageDrawing.Rect%2A>プロパティはイメージが描画される領域を定義します。  
  
 次の例では、(75,75) に存在する 100 x 100 ピクセルの四角形にイメージを描画します。 次の図は、<xref:System.Windows.Media.ImageDrawing>この例で作成された例を示しています。 の境界を示す灰色の枠線が<xref:System.Windows.Media.ImageDrawing>追加されました。  
  
 ![&#40;75,75&#41; に描画される 100 × 100 の ImageDrawing](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100×100 の ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 イメージについて詳しくは、「[イメージングの概要](imaging-overview.md)」をご覧ください。  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>メディアの再生 (コードのみ)  
  
> [!NOTE]
> を宣言<xref:System.Windows.Media.VideoDrawing>することはできますが[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 は、コードを使用してメディアを読み込み、再生することしかできません。 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ビデオを再生するには、<xref:System.Windows.Controls.MediaElement>を使用します。  
  
 オーディオファイルまたはビデオファイルを再生するには、<xref:System.Windows.Media.VideoDrawing>および . <xref:System.Windows.Media.MediaPlayer> メディアを読み込んで再生するには、2 つの方法があります。 1 つ目は、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>を単独で使用する方法で、2 つ<xref:System.Windows.Media.MediaTimeline>目の<xref:System.Windows.Media.MediaPlayer>方法は、<xref:System.Windows.Media.VideoDrawing>と で使用する独自の方法を作成することです。  
  
> [!NOTE]
> アプリケーションでメディアを配布するときは、イメージのようにプロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
 独自<xref:System.Windows.Media.MediaTimeline>の を作成せずにメディアを再生するには、次の手順を実行します。  
  
1. <xref:System.Windows.Media.MediaPlayer> オブジェクトを作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. この方法<xref:System.Windows.Media.MediaPlayer.Open%2A>を使用して、メディア ファイルを読み込みます。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. <xref:System.Windows.Media.VideoDrawing> を作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. メディアを描画するサイズと位置を指定するには、<xref:System.Windows.Media.VideoDrawing.Rect%2A>のプロパティを<xref:System.Windows.Media.VideoDrawing>設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. のプロパティ<xref:System.Windows.Media.VideoDrawing.Player%2A><xref:System.Windows.Media.VideoDrawing>を、作成した<xref:System.Windows.Media.MediaPlayer>プロパティに設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. の<xref:System.Windows.Media.MediaPlayer.Play%2A>方法を<xref:System.Windows.Media.MediaPlayer>使用して、メディアの再生を開始します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 次の例では、<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>a を使用してビデオ ファイルを 1 回再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 メディアに対する追加のタイミング制御を得るために<xref:System.Windows.Media.MediaTimeline>は、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>オブジェクトと共に a を使用します。 を<xref:System.Windows.Media.MediaTimeline>使用すると、ビデオを繰り返すかどうかを指定できます。 と共<xref:System.Windows.Media.VideoDrawing>に<xref:System.Windows.Media.MediaTimeline>を使用するには、次の手順を実行します。  
  
1. を<xref:System.Windows.Media.MediaTimeline>宣言し、タイミング動作を設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. から<xref:System.Windows.Media.MediaClock>を作成<xref:System.Windows.Media.MediaTimeline>します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. を<xref:System.Windows.Media.MediaPlayer>作成し、<xref:System.Windows.Media.MediaClock>を使用して<xref:System.Windows.Media.MediaPlayer.Clock%2A>プロパティを設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. を<xref:System.Windows.Media.VideoDrawing>作成し、<xref:System.Windows.Media.MediaPlayer>の<xref:System.Windows.Media.VideoDrawing.Player%2A>プロパティに割り<xref:System.Windows.Media.VideoDrawing>当てます。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 次の例では、 <xref:System.Windows.Media.MediaTimeline> a<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>a を使用してビデオを繰り返し再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 を<xref:System.Windows.Media.MediaTimeline>使用する場合は、 の対話的なメソッド<xref:System.Windows.Media.Animation.ClockController>ではなく、<xref:System.Windows.Media.Animation.Clock.Controller%2A>の<xref:System.Windows.Media.MediaClock>プロパティから返されるインタラクティブなメディアの再生を制御<xref:System.Windows.Media.MediaPlayer>します。  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>テキストの描画  
 テキストを描画するには、 および<xref:System.Windows.Media.GlyphRunDrawing><xref:System.Windows.Media.GlyphRun>を使用します。 次の例では、<xref:System.Windows.Media.GlyphRunDrawing>を使用して"Hello World" というテキストを描画します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A<xref:System.Windows.Media.GlyphRun>は、固定形式のドキュメントプレゼンテーションおよび印刷シナリオで使用するための低レベルのオブジェクトです。 画面にテキストを描画する簡単な方法は、 または<xref:System.Windows.Controls.Label>を<xref:System.Windows.Controls.TextBlock>使用することです。 <xref:System.Windows.Media.GlyphRun>の詳細については、「 [GlyphRun オブジェクトとグリフ要素の概要](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)」を参照してください。  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>複合描画  
 A<xref:System.Windows.Media.DrawingGroup>を使用すると、複数の図面を 1 つの複合図面に結合できます。 を<xref:System.Windows.Media.DrawingGroup>使用すると、図形、イメージ、およびテキストを 1 つの<xref:System.Windows.Media.Drawing>オブジェクトに結合できます。  
  
 次の例では、<xref:System.Windows.Media.DrawingGroup>を使用<xref:System.Windows.Media.GeometryDrawing>して 2<xref:System.Windows.Media.ImageDrawing>つのオブジェクトと 1 つのオブジェクトを結合します。 この例を実行すると、次の出力が生成されます。  
  
 ![複数の描画を含む DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
複合描画  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 また<xref:System.Windows.Media.DrawingGroup>、不透明度マスク、変換、ビットマップ効果、およびその他の操作をその内容に適用することもできます。 <xref:System.Windows.Media.DrawingGroup><xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>操作は、 、 、 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、 、 <xref:System.Windows.Media.DrawingGroup.Transform%2A>、 、 の順に適用されます。  
  
 次の図は、操作が適用<xref:System.Windows.Media.DrawingGroup>される順序を示しています。  
  
 ![DrawingGroup 操作の順序](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup 操作の順序  
  
 次の表は、オブジェクトのコンテンツを操作するために使用できる<xref:System.Windows.Media.DrawingGroup>プロパティを示しています。  
  
|プロパティ|説明|図|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|コンテンツの選択部分の不透明度を変更します<xref:System.Windows.Media.DrawingGroup>。 例については、「[How to: Control the Opacity of a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))」(方法: 描画の不透明度を制御する) をご覧ください。|![不透明マスクを持つ図面グループ](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|内容の不透明度を均一に変更<xref:System.Windows.Media.DrawingGroup>します。 このプロパティを使用して、<xref:System.Windows.Media.Drawing>透明または部分的に透明にします。 例については、「[How to: Apply an Opacity Mask to a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))」(方法: 不透明マスクを描画に適用する) をご覧ください。|![不透明度の設定が異なる DrawingGroups](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|コンテンツに<xref:System.Windows.Media.Effects.BitmapEffect>a<xref:System.Windows.Media.DrawingGroup>を適用します。 例については、「[How to: Apply a BitmapEffect to a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))」(方法: BitmapEffect を描画に適用する) をご覧ください。|![BlurBitmapEffect を持つ DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|を使用<xref:System.Windows.Media.DrawingGroup>して記述した領域に内容をクリップ<xref:System.Windows.Media.Geometry>します。 例については、「[How to: Clip a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90))」(方法: 描画をクリッピングする) をご覧ください。|![クリップ領域が定義された DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|デバイスに依存しないピクセルを、指定したガイドラインに沿ったデバイス ピクセルにスナップします。 このプロパティは、低解像度ディスプレイで、非常に詳細なグラフィックスがはっきりとレンダリングされるようにするのに便利です。 例については、「[方法 : 描画に GuidelineSet を適用する](how-to-apply-a-guidelineset-to-a-drawing.md)」をご覧ください。|![GuidelineSet がある (またはない) DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|内容を変換<xref:System.Windows.Media.DrawingGroup>します。 例については、「[How to: Apply a Transform to a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))」(方法: 変換を描画に適用する) をご覧ください。|![回転した DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>描画をイメージとして表示する  
 コントロールを持<xref:System.Windows.Media.Drawing>つ<xref:System.Windows.Controls.Image>を表示するには、<xref:System.Windows.Media.DrawingImage><xref:System.Windows.Controls.Image>コントロールとして を使用<xref:System.Windows.Controls.Image.Source%2A>し、<xref:System.Windows.Media.DrawingImage>オブジェクトの<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>プロパティを表示する図面に設定します。  
  
 次の例では、<xref:System.Windows.Media.DrawingImage>および<xref:System.Windows.Controls.Image>コントロールを使用<xref:System.Windows.Media.GeometryDrawing>して を表示します。 この例を実行すると、次の出力が生成されます。  
  
 ![2 つの楕円の GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>描画によるオブジェクトの塗りつぶし  
 A<xref:System.Windows.Media.DrawingBrush>は、描画オブジェクトを使用して領域を描画するブラシの一種です。 描画でほとんどすべてのグラフィカル オブジェクトを塗りつぶすために使うことができます。 の<xref:System.Windows.Media.Drawing>プロパティは、<xref:System.Windows.Media.DrawingBrush>の<xref:System.Windows.Media.DrawingBrush.Drawing%2A>プロパティを記述します。 を<xref:System.Windows.Media.Drawing>使用して<xref:System.Windows.Media.DrawingBrush>をレンダリングするには、ブラシの<xref:System.Windows.Media.Drawing>プロパティを使用してブラシに追加し、ブラシを使用してコントロールやパネルなどのグラフィカル オブジェクトをペイントします。  
  
 次の例では、<xref:System.Windows.Media.DrawingBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して、<xref:System.Windows.Shapes.Rectangle>から作成されたパターンを<xref:System.Windows.Media.GeometryDrawing>使用して a の を描画します。 この例を実行すると、次の出力が生成されます。  
  
 ![並べて表示される DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush で使われる GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 この<xref:System.Windows.Media.DrawingBrush>クラスには、コンテンツの伸張とタイリングに関するさまざまなオプションが用意されています。 の詳細については、「[イメージ、図面、およびビジュアルを使用したペイント」の概要を](painting-with-images-drawings-and-visuals.md)参照してください。 <xref:System.Windows.Media.DrawingBrush>  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>ビジュアルで描画をレンダリングする  
 A<xref:System.Windows.Media.DrawingVisual>は、描画をレンダリングするように設計されたビジュアル オブジェクトの一種です。 高度にカスタマイズされたグラフィカル環境を構築したい開発者は、ビジュアル レイヤーを直接操作できますが、この概要ではそれについては説明しません。 詳しくは、「[DrawingVisual オブジェクトの使用](using-drawingvisual-objects.md)」をご覧ください。  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>DrawingContext オブジェクト  
 クラス<xref:System.Windows.Media.DrawingContext>を使用すると、 または<xref:System.Windows.Media.Visual>に<xref:System.Windows.Media.Drawing>ビジュアル コンテンツを設定できます。 このような低レベルのグラフィックオブジェクトの多くは<xref:System.Windows.Media.DrawingContext>、グラフィカルコンテンツを非常に効率的に記述しているため、を使用します。  
  
 <xref:System.Windows.Media.DrawingContext>描画メソッドは<xref:System.Drawing.Graphics?displayProperty=nameWithType>、型の描画メソッドと似ているように見えますが、実際には非常に異なります。 <xref:System.Windows.Media.DrawingContext>は保持モードのグラフィックス システムで使用され、<xref:System.Drawing.Graphics?displayProperty=nameWithType>型はイミディエイト モードのグラフィックス システムで使用されます。 オブジェクトの描画コマンド<xref:System.Windows.Media.DrawingContext>を使用する場合、実際にはレンダリング命令のセットを格納します (ただし、正確な記憶機構は、後でグラフィックス システムで<xref:System.Windows.Media.DrawingContext>使用されるオブジェクトの種類によって異なります)。リアルタイムで画面に描画していません。 Windows プレゼンテーション ファウンデーション (WPF) グラフィックス システムの動作の詳細については、「 [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)」を参照してください。  
  
 直接インスタンス化しない場合<xref:System.Windows.Media.DrawingContext>は、 ;ただし、 や などの<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType>特定のメソッドから図面コンテキストを<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>取得することはできます。  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>ビジュアルの内容の列挙  
 オブジェクトは、他の用途に<xref:System.Windows.Media.Drawing>加えて、 のコンテンツを列挙するためのオブジェクト モデルも提供<xref:System.Windows.Media.Visual>します。  
  
 次の例では、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>メソッドを使用して<xref:System.Windows.Media.DrawingGroup>a<xref:System.Windows.Media.Visual>の値を取得し、それを列挙します。  
  
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
- [ハウツートピック](drawings-how-to-topics.md)

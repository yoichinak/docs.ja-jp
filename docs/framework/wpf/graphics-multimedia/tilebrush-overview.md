---
title: TileBrush の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187107"
---
# <a name="tilebrush-overview"></a>TileBrush の概要
<xref:System.Windows.Media.TileBrush>オブジェクトを使用すると、領域をイメージ、<xref:System.Windows.Media.Drawing>または<xref:System.Windows.Media.Visual>で塗りつぶす方法を制御できます。 このトピックでは、機能を使用<xref:System.Windows.Media.TileBrush>して<xref:System.Windows.Media.ImageBrush>、領域 、または<xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.VisualBrush>の描画方法をより詳細に制御する方法について説明します。  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、 、<xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>クラスの基本機能を使用する方法を理解しておくと役に立ちます。 これらのタイプの概要については、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>タイルで領域を塗りつぶす  
 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>は<xref:System.Windows.Media.VisualBrush>オブジェクトの<xref:System.Windows.Media.TileBrush>タイプです。 タイル ブラシを使用すると、イメージ、描画、またはビジュアルで領域を塗りつぶす方法を細かく制御できます。 たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。  
  
 タイル ブラシによる領域の塗りつぶしには、コンテンツ、基本タイル、および出力領域の 3 つのコンポーネントが含まれます。  
  
 ![TileBrush のコンポーネント](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
単一のタイルを持つタイルブラシのコンポーネント  
  
 ![タイル表示された TileBrush のコンポーネント](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Tile の TileMode を使用する TileBrush のコンポーネント  
  
 出力<xref:System.Windows.Shapes.Shape.Fill%2A>領域は、 の<xref:System.Windows.Shapes.Ellipse>または<xref:System.Windows.Controls.Control.Background%2A>などのペイントされる領域です。 <xref:System.Windows.Controls.Button> 次のセクションでは、 の他の<xref:System.Windows.Media.TileBrush>2 つのコンポーネントについて説明します。  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>ブラシのコンテンツ  
 3種類の<xref:System.Windows.Media.TileBrush>塗料と各塗料の種類が異なります。  
  
- ブラシが<xref:System.Windows.Media.ImageBrush>の場合、このコンテンツはイメージです<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティは、 の内容<xref:System.Windows.Media.ImageBrush>を指定します。  
  
- ブラシが<xref:System.Windows.Media.DrawingBrush>の場合、この内容は描画です。 プロパティ<xref:System.Windows.Media.DrawingBrush.Drawing%2A>は、 の内容を<xref:System.Windows.Media.DrawingBrush>指定します。  
  
- ブラシが<xref:System.Windows.Media.VisualBrush>の場合、このコンテンツはビジュアルです。 プロパティ<xref:System.Windows.Media.VisualBrush.Visual%2A>は、 の内容を<xref:System.Windows.Media.VisualBrush>指定します。  
  
 このプロパティを使用してコンテンツの<xref:System.Windows.Media.TileBrush>位置とサイズを指定できますが、<xref:System.Windows.Media.TileBrush.Viewbox%2A>設定を既定値のままにするのは一般的です。 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 既定では、<xref:System.Windows.Media.TileBrush.Viewbox%2A>はブラシの内容を完全に含む構成になっています。 <xref:System.Windows.Controls.Viewbox>の構成の詳細については、プロパティ ページを<xref:System.Windows.Controls.Viewbox>参照してください。  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>基本タイル  
 基本<xref:System.Windows.Media.TileBrush>タイルにコンテンツを投影します。 この<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティは、<xref:System.Windows.Media.TileBrush>基本タイルを埋めるためにコンテンツを拡大する方法を制御します。 この<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティは、列挙体によって定義される次の<xref:System.Windows.Media.Stretch>値を受け入れます。  
  
- <xref:System.Windows.Media.Stretch.None>: ブラシの内容がタイルを埋めるために伸張されていません。  
  
- <xref:System.Windows.Media.Stretch.Fill>: ブラシのコンテンツはタイルに合わせて拡大縮小されます。 コンテンツの高さと幅は別々にスケーリングされるため、コンテンツの元の縦横比が維持されない場合があります。 つまり、出力タイルを完全に塗りつぶすために、ブラシのコンテンツがいびつになることがあります。  
  
- <xref:System.Windows.Media.Stretch.Uniform>: ブラシのコンテンツは、タイル内に完全に収まるように拡大縮小されます。 コンテンツの縦横比は維持されます。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: ブラシの内容は、コンテンツの元のアスペクト比を維持したまま、出力領域全体に完全に塗りつぶされるようにスケーリングされます。  
  
 次の図は、さまざまな<xref:System.Windows.Media.TileBrush.Stretch%2A>設定を示しています。  
  
 ![異なる TileBrush Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 次の例では、出力領域に合<xref:System.Windows.Media.ImageBrush>わせて伸縮しないように、a の内容が設定されています。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 既定では、1<xref:System.Windows.Media.TileBrush>つのタイル (基本タイル) が生成され、そのタイルが出力領域全体に完全に広がるように伸びています。 基本タイルのサイズと位置は、 および<xref:System.Windows.Media.TileBrush.Viewport%2A><xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを設定することで変更できます。  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>基本タイルのサイズ  
 プロパティ<xref:System.Windows.Media.TileBrush.Viewport%2A>は、基本タイルのサイズと位置を決定し、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティは、絶対座標<xref:System.Windows.Media.TileBrush.Viewport%2A>または相対座標を使用して指定されているかどうかを決定します。 座標が相対的な場合、座標は出力領域のサイズに対して相対的になります。 点 (0,0) は出力領域の左上隅を表し、(1,1) は出力領域の右下隅を表します。 プロパティが絶対座標<xref:System.Windows.Media.TileBrush.Viewport%2A>を使用するように指定するには、プロパティ<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>を<xref:System.Windows.Media.BrushMappingMode.Absolute>に設定します。  
  
 次の図は、 相対と相対値<xref:System.Windows.Media.TileBrush>の出力と絶対<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>値の出力の違いを示しています。 どの図も、並べて表示するパターンを示しています。次のセクションでは、パターンの指定方法について説明します。  
  
 ![ビューポートの絶対単位と相対単位](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 次の例では、イメージを使用して幅と高さが 50% のタイルを作成しています。 基本タイルは、出力領域の (0,0) の位置にあります。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 次の例では、デバイスに依存<xref:System.Windows.Media.ImageBrush>しないピクセルのタイルを 25 x 25 に設定します。 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>絶対値であるため、<xref:System.Windows.Media.ImageBrush>塗りつぶされている領域のサイズに関係なく、タイルは常に 25 x 25 ピクセルです。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>並べて表示する動作  
 A<xref:System.Windows.Media.TileBrush>は、基本タイルが出力領域を完全に満たさない場合にタイル パターンを生成し、<xref:System.Windows.Media.TileMode.None>その後タイル モードを指定します。 タイル ブラシのタイルが出力領域全体に完全に表示されない場合、<xref:System.Windows.Media.TileBrush.TileMode%2A>そのプロパティは、出力領域を埋めるためにベース タイルを複製するかどうか、また、その場合は、基本タイルを複製する方法を指定します。 この<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティは、列挙体によって定義される次の<xref:System.Windows.Media.TileMode>値を受け入れます。  
  
- <xref:System.Windows.Media.TileMode.None>: ベース タイルのみが描画されます。  
  
- <xref:System.Windows.Media.TileMode.Tile>: 基本タイルが描画され、残りの領域は、1 つのタイルの右端が次のタイルの左端に隣接し、同様に下と上の場合に隣接するように、ベース タイルを繰り返して塗りつぶされます。  
  
- <xref:System.Windows.Media.TileMode.FlipX>: と同<xref:System.Windows.Media.TileMode.Tile>じですが、タイルの代替列は水平に反転されます。  
  
- <xref:System.Windows.Media.TileMode.FlipY>: と同<xref:System.Windows.Media.TileMode.Tile>じですが、タイルの代替行は垂直に反転されます。  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: と<xref:System.Windows.Media.TileMode.FlipX>の<xref:System.Windows.Media.TileMode.FlipY>組み合わせです。  
  
 並べて表示するさまざまなモードを次のイメージに示します。  
  
 ![別の TileBrush TileMode 設定](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 次の例では、幅と高さが 100 ピクセルの四角形がイメージを使用して塗りつぶされます。 ブラシの設定<xref:System.Windows.Media.TileBrush.Viewport%2A>が 0,0,0.25,0.25 に設定されている場合、ブラシのベース タイルは出力領域の 1/4 になります。 ブラシの<xref:System.Windows.Media.TileBrush.TileMode%2A>が に<xref:System.Windows.Media.TileMode.FlipXY>設定されています。 そのため、四角形はタイルの行で塗りつぶされます。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [ハウツートピック](brushes-how-to-topics.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [ImageBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)

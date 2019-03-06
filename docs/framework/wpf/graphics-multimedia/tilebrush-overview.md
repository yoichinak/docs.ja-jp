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
ms.openlocfilehash: 8013bacf6c4d33ce89fc287e625ce8c8fb6c3ef0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369943"
---
# <a name="tilebrush-overview"></a>TileBrush の概要
<xref:System.Windows.Media.TileBrush> オブジェクトを提供する非常に大量のイメージで領域を塗りつぶす方法を制御<xref:System.Windows.Media.Drawing>、または<xref:System.Windows.Media.Visual>します。 このトピックでは、使用する方法を説明します<xref:System.Windows.Media.TileBrush>方法の詳細に制御する機能、 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>領域を塗りつぶします。  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するのにはの基本的な機能を使用する方法を理解しておいて、 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>クラス。 これらの型の概要については、次を参照してください。、[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>タイルで領域を塗りつぶす  
 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、は<xref:System.Windows.Media.VisualBrush>種類<xref:System.Windows.Media.TileBrush>オブジェクト。 タイル ブラシを使用すると、イメージ、描画、またはビジュアルで領域を塗りつぶす方法を細かく制御できます。 たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。  
  
 タイル ブラシによる領域の塗りつぶしには、コンテンツ、基本タイル、および出力領域の 3 つのコンポーネントが含まれます。  
  
 ![TileBrush コンポーネント](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
1 つのタイルを使用する TileBrush のコンポーネント  
  
 ![並べて表示された TileBrush のコンポーネント](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Tile の TileMode を使用する TileBrush のコンポーネント  
  
 出力領域がなど、塗りつぶされる領域、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>または<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>します。 次のセクションでは、説明の他の 2 つのコンポーネント、<xref:System.Windows.Media.TileBrush>します。  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>ブラシのコンテンツ  
 3 つの種類がある<xref:System.Windows.Media.TileBrush>し、それぞれを異なる種類のコンテンツを描画します。  
  
-   ブラシがの場合、 <xref:System.Windows.Media.ImageBrush>、このコンテンツは、イメージ、<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティの内容を指定する、<xref:System.Windows.Media.ImageBrush>します。  
  
-   ブラシがの場合、 <xref:System.Windows.Media.DrawingBrush>、このコンテンツは描画します。 <xref:System.Windows.Media.DrawingBrush.Drawing%2A>プロパティの内容を指定する、<xref:System.Windows.Media.DrawingBrush>します。  
  
-   ブラシがの場合、 <xref:System.Windows.Media.VisualBrush>、このコンテンツはビジュアル。 <xref:System.Windows.Media.VisualBrush.Visual%2A>プロパティの内容を指定する、<xref:System.Windows.Media.VisualBrush>します。  
  
 位置とのサイズを指定できます<xref:System.Windows.Media.TileBrush>コンテンツを使用して、<xref:System.Windows.Media.TileBrush.Viewbox%2A>プロパティのままにするが一般的ですが、<xref:System.Windows.Media.TileBrush.Viewbox%2A>が既定値に設定します。 既定で、<xref:System.Windows.Media.TileBrush.Viewbox%2A>ブラシの内容を完全に格納するように構成します。 構成の詳細については、<xref:System.Windows.Controls.Viewbox>を参照してください、<xref:System.Windows.Controls.Viewbox>プロパティ ページ。  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>基本タイル  
 A<xref:System.Windows.Media.TileBrush>を基本タイルにそのコンテンツを射影します。 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティ コントロール方法<xref:System.Windows.Media.TileBrush>コンテンツは、基本タイルをいっぱいに拡大されます。 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.Stretch>列挙体。  
  
-   <xref:System.Windows.Media.Stretch.None>:ブラシのコンテンツは、タイルを塗りつぶすには引き伸ばされません。  
  
-   <xref:System.Windows.Media.Stretch.Fill>:ブラシのコンテンツは、タイルに合わせてスケーリングされます。 コンテンツの高さと幅は別々にスケーリングされるため、コンテンツの元の縦横比が維持されない場合があります。 つまり、出力タイルを完全に塗りつぶすために、ブラシのコンテンツがいびつになることがあります。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>:ブラシのコンテンツに、タイル内で完全に収まるようにスケーリングされます。 コンテンツの縦横比は維持されます。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>:ブラシのコンテンツは、コンテンツの元の縦横比を維持しながら、出力領域が完全にいっぱいにように拡大縮小されます。  
  
 次の図は、異なる<xref:System.Windows.Media.TileBrush.Stretch%2A>設定します。  
  
 ![TileBrush のさまざまな Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 次の例でのコンテンツ、<xref:System.Windows.Media.ImageBrush>設定されているため、出力領域全体に伸縮しません。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 既定で、 <xref:System.Windows.Media.TileBrush> 1 つのタイル (基本タイル) を生成し、そのタイルを出力領域を完全に塗りつぶします。 基本タイルの位置とサイズを設定して変更することができます、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティ。  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>基本タイルのサイズ  
 <xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティは、基本のタイルの位置とサイズを決定します。 および<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを決定しますかどうか、<xref:System.Windows.Media.TileBrush.Viewport%2A>絶対または相対座標を使用して指定されます。 座標が相対的な場合、座標は出力領域のサイズに対して相対的になります。 点 (0,0) は出力領域の左上隅を表し、(1,1) は出力領域の右下隅を表します。 指定する、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティが絶対座標を使用して、設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>します。  
  
 次の図は、出力の間の違いを<xref:System.Windows.Media.TileBrush>で相対と絶対<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>します。 どの図も、並べて表示するパターンを示しています。次のセクションでは、パターンの指定方法について説明します。  
  
 ![ビューポートの絶対単位と総体単位](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 次の例では、イメージを使用して幅と高さが 50% のタイルを作成しています。 基本タイルは、出力領域の (0,0) の位置にあります。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 次の例では、設定のタイル、<xref:System.Windows.Media.ImageBrush>を 25 x 25 のデバイス非依存のピクセルにします。 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>は絶対的では、<xref:System.Windows.Media.ImageBrush>タイルが描画される領域のサイズに関係なくを 25 x 25 ピクセルでは常にします。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>並べて表示する動作  
 A<xref:System.Windows.Media.TileBrush>基本タイルが完全にいっぱいにならない、出力領域と、他のタイル モード時に並べて表示するパターンが生成されます<xref:System.Windows.Media.TileMode.None>を指定します。 タイル ブラシのタイルが出力領域を完全に塗りつぶしていないときにその<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティは、基本タイルは出力領域に複製する必要があり、基本のタイルを複製する必要があれば、かどうかを指定します。 <xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.TileMode>列挙体。  
  
-   <xref:System.Windows.Media.TileMode.None>:基本タイルのみを描画します。  
  
-   <xref:System.Windows.Media.TileMode.Tile>:基本タイルが描画され、残りの領域は基本タイルの繰り返しつまり、1 つのタイルの右端は、次の左端の横にある同様に上端と下端で塗りつぶされます。  
  
-   <xref:System.Windows.Media.TileMode.FlipX>:同じ<xref:System.Windows.Media.TileMode.Tile>タイルの代替列が水平方向に反転するがします。  
  
-   <xref:System.Windows.Media.TileMode.FlipY>:同じ<xref:System.Windows.Media.TileMode.Tile>が代替行のタイルが上下に反転します。  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>:<xref:System.Windows.Media.TileMode.FlipX> と <xref:System.Windows.Media.TileMode.FlipY> の組み合わせです。  
  
 並べて表示するさまざまなモードを次のイメージに示します。  
  
 ![TileBrush のさまざまな TileMode 設定](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 次の例では、幅と高さが 100 ピクセルの四角形がイメージを使用して塗りつぶされます。 ブラシを設定して<xref:System.Windows.Media.TileBrush.Viewport%2A>が設定されているブラシの基本タイルが出力領域の 1/4 が行わ 0,0,0.25,0.25 にします。 ブラシの<xref:System.Windows.Media.TileBrush.TileMode%2A>に設定されている<xref:System.Windows.Media.TileMode.FlipXY>します。 そのため、四角形はタイルの行で塗りつぶされます。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [方法トピック](brushes-how-to-topics.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)

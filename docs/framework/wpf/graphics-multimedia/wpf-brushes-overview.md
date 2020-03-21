---
title: ブラシの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186572"
---
# <a name="wpf-brushes-overview"></a>WPF のブラシの概要
画面に表示されるすべてのものは、ブラシでペイントされているため、表示されます。 たとえば、ブラシは、ボタンの背景、テキストの前景、図形の塗りつぶしを表すために使用されます。 このトピックでは、ブラシによるペイントの[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]概念を紹介し、例を示します。 ブラシを使用すると、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] オブジェクトを単色で塗りつぶすことも、パターンとイメージの複雑な組み合わせで塗りつぶすこともできます。  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>ブラシでペイントする  
 出力<xref:System.Windows.Media.Brush>を持つ領域を「ペイント」します。 さまざまなブラシで、出力の種類もさまざまです。 一部のブラシは、塗りつぶしの色で領域を描画し、他のブラシはグラデーション、パターン、イメージ、または描画を使用します。 次の図は、それぞれの<xref:System.Windows.Media.Brush>種類の例を示しています。  
  
 ![ブラシの種類](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
ブラシの例  
  
 ほとんどのビジュアル オブジェクトを使用すると、ペイント方法を指定できます。 次の表に、 を使用できる一般的なオブジェクトとプロパティ<xref:System.Windows.Media.Brush>の一覧を示します。  
  
|クラス|ブラシのプロパティ|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 次のセクションでは、さまざまな<xref:System.Windows.Media.Brush>型について説明し、それぞれの例を示します。  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>ソリッド カラーでペイントする  
 A<xref:System.Windows.Media.SolidColorBrush>は、ソリッドで領域を<xref:System.Windows.Media.Color>描画します。 a のを指定<xref:System.Windows.Media.SolidColorBrush.Color%2A>する方法はさまざまです: のアルファ、赤、青、緑のチャネルを指定したり、<xref:System.Windows.Media.Colors>クラスによって提供される定義済みの色のいずれかを使用することができます。 <xref:System.Windows.Media.SolidColorBrush>  
  
 次の例では、<xref:System.Windows.Media.SolidColorBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>を描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![SolidColorBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
ソリッドカラーブラシを使用して描画された長方形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.SolidColorBrush>詳細については、「[単色とグラデーションによるペイントの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>線形グラデーションでペイントする  
 線形<xref:System.Windows.Media.LinearGradientBrush>グラデーションで領域を描画します。 線状グラデーションでは、線、つまりグラデーション軸に沿って 2 つ以上の色をブレンドします。 グラデーションの<xref:System.Windows.Media.GradientStop>色と位置を指定するには、オブジェクトを使用します。  
  
 次の例では、<xref:System.Windows.Media.LinearGradientBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>を描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![LinearGradientBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
線形グラデーションブラシを使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.LinearGradientBrush>詳細については、「[単色とグラデーションによるペイントの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>放射状グラデーションでペイントする  
 A<xref:System.Windows.Media.RadialGradientBrush>は放射状グラデーションで領域を描画します。 放射状グラデーションは、円全体に 2 つ以上の色をブレンドします。 クラスと同様<xref:System.Windows.Media.LinearGradientBrush>に、グラデーションの<xref:System.Windows.Media.GradientStop>色と位置を指定するためにオブジェクトを使用します。  
  
 次の例では、<xref:System.Windows.Media.RadialGradientBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>を描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![RadialGradientBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
ラジアルグラデーションブラシを使用して描画された長方形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.RadialGradientBrush>詳細については、「[単色とグラデーションによるペイントの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>イメージを使用してペイントする  
 で<xref:System.Windows.Media.ImageBrush>領域を描画します<xref:System.Windows.Media.ImageSource>。  
  
 次の例では、<xref:System.Windows.Media.ImageBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>を描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![ImageBrush で描画された四角形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
イメージを使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.ImageBrush>詳細については、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>図面を使用してペイントする  
 で<xref:System.Windows.Media.DrawingBrush>領域を描画します<xref:System.Windows.Media.Drawing>。 は<xref:System.Windows.Media.Drawing>、図形、画像、テキスト、およびメディアを含むことができます。  
  
 次の例では、<xref:System.Windows.Media.DrawingBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>を描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![DrawingBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
描画ブラシを使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.DrawingBrush>詳細については、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>ビジュアルでペイントする  
 オブジェクト<xref:System.Windows.Media.VisualBrush>を使用して領域を<xref:System.Windows.Media.Visual>描画します。 ビジュアル オブジェクトの例<xref:System.Windows.Controls.Button>として<xref:System.Windows.Controls.Page>は、 <xref:System.Windows.Controls.MediaElement>、 、および が含まれます。 A<xref:System.Windows.Media.VisualBrush>を使用すると、アプリケーションのある部分から別の領域にコンテンツを投影することもできます。反射効果を作成し、画面の一部を拡大するのに非常に便利です。  
  
 次の例では、<xref:System.Windows.Media.VisualBrush>を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>を描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![VisualBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
ビジュアルブラシを使用して描画された長方形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.VisualBrush>詳細については、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>定義済みブラシとシステム ブラシを使用してペイントする  
 便利なため、Windows プレゼンテーション ファンデーション (WPF) には、オブジェクトの描画に使用できる定義済みのシステム ブラシのセットが用意されています。  
  
- 使用可能な定義済みのブラシのリストについては、クラスを<xref:System.Windows.Media.Brushes>参照してください。 定義済みのブラシの使用方法の例については、「[ソリッド カラーで領域をペイントする](how-to-paint-an-area-with-a-solid-color.md)」を参照してください。  
  
- 使用可能なシステム ブラシの一覧については、クラス<xref:System.Windows.SystemColors>を参照してください。 例については、「システム[ブラシで領域をペイントする](how-to-paint-an-area-with-a-system-brush.md)」を参照してください。  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>共通ブラシ機能  
 <xref:System.Windows.Media.Brush>オブジェクトは、<xref:System.Windows.Media.Brush.Opacity%2A>ブラシを透明または部分的に透明にするために使用できるプロパティを提供します。 値<xref:System.Windows.Media.Brush.Opacity%2A>0 を指定するとブラシは完全に透明<xref:System.Windows.Media.Brush.Opacity%2A>になり、値 1 はブラシを完全に不透明にします。 プロパティを<xref:System.Windows.Media.Brush.Opacity%2A>使用して 25%<xref:System.Windows.Media.SolidColorBrush>の不透明度を設定する例を次に示します。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 ブラシに部分的に透明な色が含まれている場合、カラーの不透明度の値は、ブラシの不透明度の値と乗算によって結合されます。 たとえば、ブラシの不透明度値が 0.5 で、ブラシで使用される色の不透明度も 0.5 の場合、出力カラーの不透明度値は 0.25 になります。  
  
> [!NOTE]
> ブラシの不透明度を変更する方が、そのプロパティを使用して要素全体の不透明度を変更するよりも効率的です<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>。  
  
 ブラシのコンテンツを回転、拡大縮小、傾斜、および移動するには、その 1 <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A>つまたは一覧プロパティを使用します。 詳細については、「[ブラシ変換の概要](brush-transformation-overview.md)」を参照してください。  
  
 オブジェクトは<xref:System.Windows.Media.Animation.Animatable>オブジェクトであるため、<xref:System.Windows.Media.Brush>オブジェクトをアニメートできます。 詳細については、「アニメーションの[概要](animation-overview.md)」を参照してください。  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Freezable 機能  
 <xref:System.Windows.Freezable>クラスから継承されるため、<xref:System.Windows.Media.Brush>このクラスには、<xref:System.Windows.Media.Brush>[リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)として宣言したり、複数のオブジェクト間で共有したり、クローンを作成したりできる特別な機能がいくつか用意されています。 さらに、パフォーマンスを<xref:System.Windows.Media.Brush>向上させ、<xref:System.Windows.Media.VisualBrush>スレッドセーフにするために、読み取り専用にする以外のすべての型を使用できます。  
  
 オブジェクトによって<xref:System.Windows.Freezable>提供されるさまざまな機能の詳細については、[フリーザブルオブジェクトの概要](../advanced/freezable-objects-overview.md)を参照してください。  
  
 オブジェクトをフリーズできない理由<xref:System.Windows.Media.VisualBrush>の詳細については、タイプページを<xref:System.Windows.Media.VisualBrush>参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [ブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [ImageBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [ハウツートピック](brushes-how-to-topics.md)
- [パフォーマンスに関するその他の推奨事項](../advanced/optimizing-performance-other-recommendations.md)

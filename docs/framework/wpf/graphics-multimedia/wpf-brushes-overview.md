---
title: WPF のブラシの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 29f0bc77306df5639c188295f9f5dff7f18b4706
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962845"
---
# <a name="wpf-brushes-overview"></a>WPF のブラシの概要
画面に表示されるすべてのものは、ブラシによって描画されているため、表示されます。 たとえば、ブラシを使用して、ボタンの背景、テキストの前景色、および図形の塗りつぶしを記述します。 このトピックでは、ブラシを使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]した描画の概念と例を紹介します。 ブラシを使用すると、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] オブジェクトを単色で塗りつぶすことも、パターンとイメージの複雑な組み合わせで塗りつぶすこともできます。  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>ブラシを使用した塗りつぶし  
 は<xref:System.Windows.Media.Brush> 、出力を使用して領域を "描画" します。 さまざまなブラシの出力の種類が異なります。 ブラシによっては、純色、グラデーション、パターン、画像、または描画を使用して領域を塗りつぶすことができます。 次の図は、それぞれ<xref:System.Windows.Media.Brush>の種類の例を示しています。  
  
 ![ブラシの種類](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
ブラシの例  
  
 ほとんどのビジュアルオブジェクトを使用すると、描画方法を指定できます。 次の表に、 <xref:System.Windows.Media.Brush>で使用できる一般的なオブジェクトとプロパティの一覧を示します。  
  
|クラス|ブラシのプロパティ|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 以下のセクションでは、 <xref:System.Windows.Media.Brush>さまざまな種類について説明し、それぞれの例を示します。  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>純色で塗りつぶす  
 は<xref:System.Windows.Media.SolidColorBrush> 、純色<xref:System.Windows.Media.Color>で領域を塗りつぶします。 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.Colors>のを指定するには、さまざまな方法があります。たとえば、アルファ、赤、青、および緑のチャネルを指定したり、クラスによって提供される定義済みの色のいずれかを使用したりすることができます。<xref:System.Windows.Media.SolidColorBrush>  
  
 次の例では<xref:System.Windows.Media.SolidColorBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>のを描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![System.windows.media.solidcolorbrush> を使用して塗りつぶされる四角形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
System.windows.media.solidcolorbrush> を使用して塗りつぶされる四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <xref:System.Windows.Media.SolidColorBrush> クラスの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>線状グラデーションを使用した塗りつぶし  
 は<xref:System.Windows.Media.LinearGradientBrush> 、線状グラデーションで領域を塗りつぶします。 線状グラデーションは、直線全体の2つ以上の色をグラデーション軸としてブレンドします。 オブジェクトを<xref:System.Windows.Media.GradientStop>使用して、グラデーションの色とその位置を指定します。  
  
 次の例では<xref:System.Windows.Media.LinearGradientBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>のを描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![System.windows.media.lineargradientbrush> を使用して塗りつぶされる四角形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
System.windows.media.lineargradientbrush> を使用して塗りつぶされる四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.LinearGradientBrush> クラスの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>放射状グラデーションを使用した塗りつぶし  
 は<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーションで領域を塗りつぶします。 放射状グラデーションは、円全体で2つ以上の色をブレンドします。 クラスと同様に、オブジェクトを<xref:System.Windows.Media.GradientStop>使用して、グラデーションの色とその位置を指定します。 <xref:System.Windows.Media.LinearGradientBrush>  
  
 次の例では<xref:System.Windows.Media.RadialGradientBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>のを描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![RadialGradientBrush を使用して塗りつぶされる四角形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
RadialGradientBrush を使用して塗りつぶされる四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.RadialGradientBrush> クラスの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>イメージを使用した塗りつぶし  
 は、を<xref:System.Windows.Media.ImageSource>使用して領域を塗りつぶします。<xref:System.Windows.Media.ImageBrush>  
  
 次の例では<xref:System.Windows.Media.ImageBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>のを描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![ImageBrush によって塗りつぶされた四角形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
画像を使用して塗りつぶされる四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.ImageBrush>詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>描画を使用した塗りつぶし  
 は<xref:System.Windows.Media.DrawingBrush> 、<xref:System.Windows.Media.Drawing>を使用して領域を塗りつぶします。 に<xref:System.Windows.Media.Drawing>は、図形、画像、テキスト、およびメディアを含めることができます。  
  
 次の例では<xref:System.Windows.Media.DrawingBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>のを描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![DrawingBrush を使用して塗りつぶされる四角形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush を使用して塗りつぶされる四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.DrawingBrush>詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>ビジュアルを使用した塗りつぶし  
 は<xref:System.Windows.Media.VisualBrush> 、オブジェクトを<xref:System.Windows.Media.Visual>使用して領域を塗りつぶします。 ビジュアルオブジェクトの例と<xref:System.Windows.Controls.Button>し<xref:System.Windows.Controls.Page>て<xref:System.Windows.Controls.MediaElement>、、、などがあります。 また<xref:System.Windows.Media.VisualBrush> 、を使用すると、アプリケーションのある部分から別の領域にコンテンツを投影することができます。これは、反射効果を作成し、画面の一部を拡大する場合に非常に便利です。  
  
 次の例では<xref:System.Windows.Media.VisualBrush> 、を使用<xref:System.Windows.Shapes.Shape.Fill%2A>して<xref:System.Windows.Shapes.Rectangle>のを描画します。 次の図は、塗りつぶされた四角形を示しています。  
  
 ![VisualBrush を使用して塗りつぶされる四角形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush を使用して塗りつぶされる四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 クラスの<xref:System.Windows.Media.VisualBrush>詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>定義済みブラシとシステムブラシを使用したペイント  
 便宜上、Windows Presentation Foundation (WPF) には、オブジェクトの描画に使用できる定義済みのブラシとシステムブラシのセットが用意されています。  
  
- 使用できる定義済みのブラシの一覧につい<xref:System.Windows.Media.Brushes>ては、クラスを参照してください。 定義済みのブラシの使用方法を示す例については、「[純色で領域を塗りつぶす](how-to-paint-an-area-with-a-solid-color.md)」を参照してください。  
  
- 使用可能なシステムブラシの一覧について<xref:System.Windows.SystemColors>は、クラスを参照してください。 例については、「[システムブラシを使用して領域を塗りつぶす](how-to-paint-an-area-with-a-system-brush.md)」を参照してください。  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>一般的なブラシの機能  
 <xref:System.Windows.Media.Brush>オブジェクトは、 <xref:System.Windows.Media.Brush.Opacity%2A>ブラシを透明または部分的に透明にするために使用できるプロパティを提供します。 値を0にすると、ブラシが完全に透明<xref:System.Windows.Media.Brush.Opacity%2A>になります。一方、値が1の場合、ブラシは完全に不透明になります。 <xref:System.Windows.Media.Brush.Opacity%2A> 次の例では<xref:System.Windows.Media.Brush.Opacity%2A> 、プロパティを使用<xref:System.Windows.Media.SolidColorBrush>して、25% の不透明度を設定しています。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 ブラシに部分的に透明な色が含まれている場合、色の不透明度の値は、ブラシの不透明度の値を乗算して結合されます。 たとえば、ブラシの不透明度の値が0.5 で、ブラシで使用される色も不透明度の値が0.5 の場合、出力の色の不透明度の値は0.25 になります。  
  
> [!NOTE]
> ブラシの不透明度の値を変更する方が、 <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>プロパティを使用して要素全体の不透明度を変更するよりも効率的です。  
  
 ブラシのコンテンツは、プロパティ<xref:System.Windows.Media.Brush.Transform%2A>または<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティを使用して、回転、拡大縮小、傾斜、および平行移動を行うことができます。 詳細については、「[ブラシ変換の概要](brush-transformation-overview.md)」を参照してください。  
  
 これらは<xref:System.Windows.Media.Animation.Animatable>オブジェクトである<xref:System.Windows.Media.Brush>ため、オブジェクトをアニメーション化できます。 詳しくは、「 [アニメーションの概要](animation-overview.md)」をご覧ください。  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable 機能  
 クラスは<xref:System.Windows.Freezable>クラスから継承するため、 <xref:System.Windows.Media.Brush>クラスにはいくつかの<xref:System.Windows.Media.Brush>特別な機能があります。オブジェクトは[リソース](../advanced/xaml-resources.md)として宣言したり、複数のオブジェクト間で共有したり、複製したりできます。 また、を除く<xref:System.Windows.Media.Brush> <xref:System.Windows.Media.VisualBrush>すべての型は、パフォーマンスを向上させ、スレッドセーフにするために、読み取り専用にすることができます。  
  
 オブジェクトによっ<xref:System.Windows.Freezable>て提供されるさまざまな機能の詳細については、「 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」を参照してください。  
  
 オブジェクトを固定できない<xref:System.Windows.Media.VisualBrush>理由の詳細については<xref:System.Windows.Media.VisualBrush> 、「型」ページを参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush サンプル](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)
- [方法トピック](brushes-how-to-topics.md)
- [パフォーマンスに関するその他の推奨事項](../advanced/optimizing-performance-other-recommendations.md)

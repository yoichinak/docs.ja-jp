---
title: WPF のブラシの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 12671c62a887f863bfb423cf67d7a25eed4118b2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362605"
---
# <a name="wpf-brushes-overview"></a>WPF のブラシの概要
画面に表示できるものは、ブラシによって描画されているために表示されます。 など、ブラシを使用して、ボタン、テキストの前景色および図形の塗りつぶしの背景について説明します。 このトピックでの描画の概念を説明する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ブラシし、例について説明します。 ブラシを使用すると、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] オブジェクトを単色で塗りつぶすことも、パターンとイメージの複雑な組み合わせで塗りつぶすこともできます。  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>ブラシと描画  
 A<xref:System.Windows.Media.Brush>その出力を使用して領域を「塗りつぶして」。 さまざまなブラシには、さまざまな種類の出力があります。 いくつかのブラシは、純色、グラデーション、パターン、画像、または描画を他のユーザーで領域を塗りつぶします。 次の図は、それぞれ、別の例を示します<xref:System.Windows.Media.Brush>型。  
  
 ![ブラシの種類](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
ブラシの例  
  
 ほとんどのビジュアル オブジェクトには、描画する方法を指定することが有効にします。 次の表は、いくつかの一般的なオブジェクトおよびプロパティを使用することができます、<xref:System.Windows.Media.Brush>します。  
  
|クラス|ブラシのプロパティ|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 次のセクションでは、説明、異なる<xref:System.Windows.Media.Brush>型し、それぞれの例を提供します。  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>純色で描画  
 A<xref:System.Windows.Media.SolidColorBrush>ソリッドで領域を塗りつぶす<xref:System.Windows.Media.Color>します。 さまざまなを指定する方法がある、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>: はアルファ、赤、青、および緑チャネルを指定またはによって提供される定義済みの色のいずれかを使用するなど、<xref:System.Windows.Media.Colors>クラス。  
  
 次の例では、<xref:System.Windows.Media.SolidColorBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。 次の図は、塗りつぶされた四角形を示します。  
  
 ![SolidColorBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
SolidColorBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.SolidColorBrush>クラスを参照してください[純色およびグラデーション概要](painting-with-solid-colors-and-gradients-overview.md)します。  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>線形グラデーションでの塗りつぶし  
 A<xref:System.Windows.Media.LinearGradientBrush>線形グラデーションを使用して領域を塗りつぶします。 線形グラデーションをグラデーション軸線の間で 2 つまたは複数のカラーをブレンドします。 使用する<xref:System.Windows.Media.GradientStop>グラデーションとそれらの位置で色を指定するオブジェクト。  
  
 次の例では、<xref:System.Windows.Media.LinearGradientBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。 次の図は、塗りつぶされた四角形を示します。  
  
 ![LinearGradientBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
LinearGradientBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.LinearGradientBrush>クラスを参照してください[純色およびグラデーション概要](painting-with-solid-colors-and-gradients-overview.md)します。  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>放射状グラデーションの描画  
 A<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーションを使用して領域を塗りつぶします。 放射状グラデーション円の間で 2 つまたは複数のカラーをブレンドします。 同様、<xref:System.Windows.Media.LinearGradientBrush>クラスを使用する<xref:System.Windows.Media.GradientStop>グラデーションとそれらの位置で色を指定するオブジェクト。  
  
 次の例では、<xref:System.Windows.Media.RadialGradientBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。 次の図は、塗りつぶされた四角形を示します。  
  
 ![RadialGradientBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
RadialGradientBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.RadialGradientBrush>クラスを参照してください[純色およびグラデーション概要](painting-with-solid-colors-and-gradients-overview.md)します。  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>イメージの描画  
 <xref:System.Windows.Media.ImageBrush>で領域を塗りつぶす、<xref:System.Windows.Media.ImageSource>します。  
  
 次の例では、<xref:System.Windows.Media.ImageBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。 次の図は、塗りつぶされた四角形を示します。  
  
 ![ImageBrush で描画された四角形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
イメージを使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.ImageBrush>クラスを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>描画による描画  
 A<xref:System.Windows.Media.DrawingBrush>で領域を塗りつぶす、<xref:System.Windows.Media.Drawing>します。 A<xref:System.Windows.Media.Drawing>図形、イメージ、テキスト、およびメディアに含めることができます。  
  
 次の例では、<xref:System.Windows.Media.DrawingBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。 次の図は、塗りつぶされた四角形を示します。  
  
 ![DrawingBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.DrawingBrush>クラスを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>ビジュアルでの塗りつぶし  
 A<xref:System.Windows.Media.VisualBrush>で領域を塗りつぶす、<xref:System.Windows.Media.Visual>オブジェクト。 ビジュアル オブジェクトの例として、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.Page>、および<xref:System.Windows.Controls.MediaElement>します。 A<xref:System.Windows.Media.VisualBrush>別の領域に、アプリケーションの 1 つの部分からコンテンツをプロジェクトすることもできますが反射効果を作成し、画面の一部を際立たせるに便利です。  
  
 次の例では、<xref:System.Windows.Media.VisualBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。 次の図は、塗りつぶされた四角形を示します。  
  
 ![VisualBrush を使用して描画された四角形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.VisualBrush>クラスを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>定義済みおよびシステム ブラシを使用して描画します。  
 便宜上は、Windows Presentation Foundation (WPF) は、定義済みの一連のおよびシステム ブラシ オブジェクトの描画に使用できるを提供します。  
  
-   使用可能な定義済みのブラシの一覧は、次を参照してください。、<xref:System.Windows.Media.Brushes>クラス。 定義済みのブラシを使用する方法を示す例は、次を参照してください。[純色で領域を塗りつぶす](how-to-paint-an-area-with-a-solid-color.md)します。  
  
-   使用可能なシステム ブラシの一覧は、次を参照してください。、<xref:System.Windows.SystemColors>クラス。 例については、次を参照してください。[システム ブラシで領域を塗りつぶす](how-to-paint-an-area-with-a-system-brush.md)します。  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>ブラシの共通機能  
 <xref:System.Windows.Media.Brush> オブジェクトを提供する<xref:System.Windows.Media.Brush.Opacity%2A>透明または部分的に透明のブラシを作成するために使用できるプロパティです。 <xref:System.Windows.Media.Brush.Opacity%2A> 0 の値を指定すると、ブラシは、中に完全に透明、 <xref:System.Windows.Media.Brush.Opacity%2A> 1 の値を指定すると、ブラシは完全に不透明です。 次の例では、<xref:System.Windows.Media.Brush.Opacity%2A>プロパティを<xref:System.Windows.Media.SolidColorBrush>不透明度が 25% です。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 ブラシには、部分的に透明な色が含まれています場合、は、ブラシの不透明度の値との乗算により色の不透明度の値が組み合わされます。 たとえば、ブラシが不透明度値は 0.5、ブラシで使用される色では、0.5 の不透明度の値も持っている場合は、出力の色によって 0.25 の不透明度値があります。  
  
> [!NOTE]
>  使用して、要素全体の不透明度を変更するよりも、ブラシの不透明度の値を変更する方が効率的です、<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>プロパティ。  
  
 回転、拡大縮小、傾斜、およびを使用して、ブラシのコンテンツを変換、<xref:System.Windows.Media.Brush.Transform%2A>または<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティ。 詳細については、次を参照してください。[ブラシの変換の概要](brush-transformation-overview.md)します。  
  
 いるため、<xref:System.Windows.Media.Animation.Animatable>オブジェクト、<xref:System.Windows.Media.Brush>オブジェクトをアニメーション化することができます。 詳しくは、「 [アニメーションの概要](animation-overview.md)」をご覧ください。  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable 機能  
 継承するため、<xref:System.Windows.Freezable>クラス、<xref:System.Windows.Media.Brush>クラスには、いくつかの特別な機能が用意されています:<xref:System.Windows.Media.Brush>としてオブジェクトを宣言することができます[リソース](../advanced/xaml-resources.md)、複数のオブジェクト間で共有および複製します。 さらに、すべて、<xref:System.Windows.Media.Brush>型除く<xref:System.Windows.Media.VisualBrush>パフォーマンスを向上させるために読み取り専用し、スレッド セーフに行われたことができます。  
  
 によって提供されるさまざまな機能の詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
 その理由の詳細については<xref:System.Windows.Media.VisualBrush>オブジェクトにすることはできません固定されているを参照してください、<xref:System.Windows.Media.VisualBrush>の種類 ページ。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)
- [方法トピック](brushes-how-to-topics.md)
- [パフォーマンスに関するその他の推奨事項](../advanced/optimizing-performance-other-recommendations.md)

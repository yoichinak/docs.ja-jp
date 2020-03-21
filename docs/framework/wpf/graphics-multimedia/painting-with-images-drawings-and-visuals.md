---
title: イメージ、描画、およびビジュアルによる塗りつぶし
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186919"
---
# <a name="painting-with-images-drawings-and-visuals"></a>イメージ、描画、およびビジュアルによる塗りつぶし
ここでは、 、<xref:System.Windows.Media.ImageBrush>および<xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.VisualBrush>オブジェクトを使用して、イメージ、、、または を使用して<xref:System.Windows.Media.Drawing>領域を描画<xref:System.Windows.Media.Visual>する方法について説明します。  

<a name="prereqs"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] に用意されているさまざまな種類のブラシとその基本的な機能を理解している必要があります。 概要については、「[WPF のブラシの概要](wpf-brushes-overview.md)」を参照してください。  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>イメージで領域を塗りつぶす  
 では<xref:System.Windows.Media.ImageBrush>、領域が で描画<xref:System.Windows.Media.ImageSource>されます。 で使用<xref:System.Windows.Media.ImageSource>する最も一般的なタイプ<xref:System.Windows.Media.ImageBrush>は<xref:System.Windows.Media.Imaging.BitmapImage>、ビットマップグラフィックを記述する です。 を<xref:System.Windows.Media.DrawingImage>使用してオブジェクトを<xref:System.Windows.Media.Drawing>使用してペイントできますが、<xref:System.Windows.Media.DrawingBrush>代わりにを使用する方法は簡単です。 オブジェクトの<xref:System.Windows.Media.ImageSource>詳細については、「 イメージングの[概要](imaging-overview.md)」を参照してください。  
  
 でペイントするには、<xref:System.Windows.Media.ImageBrush>を<xref:System.Windows.Media.Imaging.BitmapImage>作成し、それを使用してビットマップコンテンツを読み込みます。 次に、<xref:System.Windows.Media.Imaging.BitmapImage>を使用して<xref:System.Windows.Media.ImageBrush.ImageSource%2A>、 の<xref:System.Windows.Media.ImageBrush>プロパティを設定します。 最後に、ペイント<xref:System.Windows.Media.ImageBrush>するオブジェクトに を適用します。  では[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、読み込むイメージの<xref:System.Windows.Media.ImageBrush.ImageSource%2A>パス<xref:System.Windows.Media.ImageBrush>を持つ プロパティを設定することもできます。  
  
 シェイプ、<xref:System.Windows.Media.Brush>パネル、コントロール<xref:System.Windows.Media.ImageBrush>、テキストなどのオブジェクトを描画するために、すべてのオブジェクトと同様に、 を使用できます。 次の図は、 で実現できる効果をいくつか示<xref:System.Windows.Media.ImageBrush>しています。  
  
 ![ImageBrush の出力例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush で描画されたオブジェクト  
  
 既定では、イメージ<xref:System.Windows.Media.ImageBrush>が完全に塗りつぶされる領域に拡大され、ペイントされた領域の縦横比がイメージと異なる場合はイメージが変形する可能性があります。 この動作を変更するには、プロパティを<xref:System.Windows.Media.TileBrush.Stretch%2A>既定値<xref:System.Windows.Media.Stretch.Fill>の<xref:System.Windows.Media.Stretch.None>、 、<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>に変更します。 の<xref:System.Windows.Media.ImageBrush>種類<xref:System.Windows.Media.TileBrush>なので、イメージ ブラシが出力領域を塗りつぶす方法を正確に指定したり、パターンを作成したりすることもできます。 高度な<xref:System.Windows.Media.TileBrush>機能の詳細については、「[タイル ブラシの概要](tilebrush-overview.md)」を参照してください。  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>例: ビットマップ イメージによるオブジェクトの塗りつぶし  
 次の例では、<xref:System.Windows.Media.ImageBrush>を使用<xref:System.Windows.Controls.Panel.Background%2A>して<xref:System.Windows.Controls.Canvas>を描画します。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>描画を使用して領域を塗りつぶす  
 A<xref:System.Windows.Media.DrawingBrush>を使用すると、図形、テキスト、画像、およびビデオを含む領域をペイントできます。 描画ブラシの中の図形は、それ自体が単色、グラデーション、イメージ、あるいは別<xref:System.Windows.Media.DrawingBrush>の色で塗りつぶされることがあります。 次の図は、 の使用方法を<xref:System.Windows.Media.DrawingBrush>示しています。  
  
 ![DrawingBrush の出力例](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush で塗りつぶされたオブジェクト  
  
 オブジェクト<xref:System.Windows.Media.DrawingBrush>を使用して領域を<xref:System.Windows.Media.Drawing>描画します。 オブジェクト<xref:System.Windows.Media.Drawing>は、図形、ビットマップ、ビデオ、テキスト行などの表示されるコンテンツを表します。 さまざまな種類の描画で、さまざまな種類のコンテンツを記述します。 次の一覧に、さまざまな種類の描画オブジェクトを示します。  
  
- <xref:System.Windows.Media.GeometryDrawing>– 図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing>– 画像を描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– テキストを描画します。  
  
- <xref:System.Windows.Media.VideoDrawing>– オーディオまたはビデオファイルを再生します。  
  
- <xref:System.Windows.Media.DrawingGroup>– 他の図面を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 オブジェクトの<xref:System.Windows.Media.Drawing>詳細については、「[図面オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
 のように<xref:System.Windows.Media.ImageBrush>、出力領域<xref:System.Windows.Media.DrawingBrush>を埋めるために<xref:System.Windows.Media.DrawingBrush.Drawing%2A>伸縮します。 この動作をオーバーライドするには、プロパティを<xref:System.Windows.Media.TileBrush.Stretch%2A>既定の<xref:System.Windows.Media.Stretch.Fill>設定の から変更します。 詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを参照してください。  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>例: 描画によるオブジェクトの塗りつぶし  
 次の例は、3 つの楕円の描画によってオブジェクトを塗りつぶす方法を示しています。 は<xref:System.Windows.Media.GeometryDrawing>省略記号を記述するために使用されます。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>ビジュアルで領域を塗りつぶす  
 すべてのブラシの中で最も汎用性と強力な、<xref:System.Windows.Media.VisualBrush>塗料の領域を. <xref:System.Windows.Media.Visual> A<xref:System.Windows.Media.Visual>は、多くの有用なグラフィカルコンポーネントの先祖となる低レベルのグラフィカルタイプです。 たとえば<xref:System.Windows.Window>、 、、<xref:System.Windows.FrameworkElement>および<xref:System.Windows.Controls.Control>クラスは、すべての種類<xref:System.Windows.Media.Visual>のオブジェクトです。 <xref:System.Windows.Media.VisualBrush>を使用すると、ほぼすべての[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グラフィカル オブジェクトで領域をペイントできます。  
  
> [!NOTE]
> オブジェクト<xref:System.Windows.Media.VisualBrush>の型ですが、<xref:System.Windows.Freezable>プロパティが<xref:System.Windows.Media.VisualBrush.Visual%2A>`null`以外の値に設定されている場合、オブジェクトを固定 (読み取り専用) にすることはできません。  
  
 の内容を指定するには<xref:System.Windows.Media.VisualBrush.Visual%2A>2 つの方法<xref:System.Windows.Media.VisualBrush>があります。  
  
- 新<xref:System.Windows.Media.Visual>しいを作成し、それを使用して<xref:System.Windows.Media.VisualBrush.Visual%2A><xref:System.Windows.Media.VisualBrush>. 例については、この後の「[例: ビジュアルによるオブジェクトの塗りつぶし](#examplevisualbrush1)」セクションを参照してください。  
  
- 既存<xref:System.Windows.Media.Visual>の を使用して、ターゲットの複製イメージを<xref:System.Windows.Media.Visual>作成します。 その後、 を<xref:System.Windows.Media.VisualBrush>使用して、反射や拡大などの興味深い効果を作成できます。 例については、「[方法 : 反射を作成する](#examplevisualbrush2)」セクションを参照してください。  
  
 に新<xref:System.Windows.Media.VisualBrush.Visual%2A><xref:System.Windows.Media.VisualBrush>しいを定義し<xref:System.Windows.Media.Visual><xref:System.Windows.UIElement>、(パネルやコントロールなど)、<xref:System.Windows.UIElement><xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A>プロパティが`true`に設定されているときに、レイアウト システムは、 とその子要素で実行されます。 ただし、ルート<xref:System.Windows.UIElement>は基本的にシステムの他の部分から分離されています: スタイルと外部レイアウトは、この境界に浸透することはできません。 したがって、ルート<xref:System.Windows.UIElement>のサイズは<xref:System.Windows.Media.VisualBrush>明示的に指定する必要があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのレイアウトの詳細については、「[レイアウト](../advanced/layout.md)」を参照してください。  
  
 と<xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>のように、<xref:System.Windows.Media.VisualBrush>出力領域を埋めるためにコンテンツを伸ばします。 この動作をオーバーライドするには、プロパティを<xref:System.Windows.Media.TileBrush.Stretch%2A>既定の<xref:System.Windows.Media.Stretch.Fill>設定の から変更します。 詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを参照してください。  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>例: ビジュアルによるオブジェクトの塗りつぶし  
 次の例では、さまざまなコントロールとパネルを使用して四角形を塗りつぶします。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>方法 : 反射を作成する  
 前の例では、背景として使用する新<xref:System.Windows.Media.Visual>しいを作成する方法を示しました。 また、 を<xref:System.Windows.Media.VisualBrush>使用して既存のビジュアルを表示することもできます。この機能により、反射や拡大などの興味深い視覚効果を生成できます。 次の例では、<xref:System.Windows.Media.VisualBrush>を使用して、複数<xref:System.Windows.Controls.Border>の要素を含む をリフレクションとして作成します。 次の図は、この例で生成される出力を示しています。  
  
 ![反映された Visual オブジェクト](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映された Visual オブジェクト  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 画面の一部を引き伸ばす方法と反射を作成する方法のその他の例については、「[VisualBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)」を参照してください。  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>TileBrush の機能  
 <xref:System.Windows.Media.ImageBrush>、、<xref:System.Windows.Media.DrawingBrush>および<xref:System.Windows.Media.VisualBrush>はオブジェクトの<xref:System.Windows.Media.TileBrush>タイプです。 <xref:System.Windows.Media.TileBrush>オブジェクトを使用すると、領域をイメージ、描画、またはビジュアルで塗りつぶす方法を制御できます。 たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。  
  
 A<xref:System.Windows.Media.TileBrush>には、コンテンツ、タイル、および出力領域の 3 つの主要なコンポーネントがあります。  
  
 ![TileBrush のコンポーネント](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
単一のタイルを持つタイルブラシのコンポーネント  
  
 ![タイル表示された TileBrush のコンポーネント](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
複数のタイルを使用する TileBrush のコンポーネント  
  
 オブジェクトのタイル機能の<xref:System.Windows.Media.TileBrush>詳細については、「 [TileBrush](tilebrush-overview.md)の概要 」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush の概要](tilebrush-overview.md)
- [WPF のブラシの概要](wpf-brushes-overview.md)
- [イメージングの概要](imaging-overview.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [不透明度マスクの概要](opacity-masks-overview.md)
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [ImageBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)

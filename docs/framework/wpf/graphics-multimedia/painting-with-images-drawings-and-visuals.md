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
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929610"
---
# <a name="painting-with-images-drawings-and-visuals"></a>イメージ、描画、およびビジュアルによる塗りつぶし
このトピックでは、、 <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>、および<xref:System.Windows.Media.VisualBrush>オブジェクトを使用して、イメージ、 <xref:System.Windows.Media.Drawing>、または<xref:System.Windows.Media.Visual>を使用して領域を塗りつぶす方法について説明します。  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] に用意されているさまざまな種類のブラシとその基本的な機能を理解している必要があります。 概要については、「[WPF のブラシの概要](wpf-brushes-overview.md)」を参照してください。  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>イメージで領域を塗りつぶす  
 は<xref:System.Windows.Media.ImageBrush> 、<xref:System.Windows.Media.ImageSource>を使用して領域を塗りつぶします。 で使用<xref:System.Windows.Media.ImageSource>する最も一般的な型<xref:System.Windows.Media.Imaging.BitmapImage>は、ビットマップグラフィックを表すです。<xref:System.Windows.Media.ImageBrush> を<xref:System.Windows.Media.DrawingImage>使用すると、 <xref:System.Windows.Media.Drawing>オブジェクトを使用して描画できますが、代わりにを<xref:System.Windows.Media.DrawingBrush>使用する方が簡単です。 <xref:System.Windows.Media.ImageSource>オブジェクトの詳細については、「[イメージングの概要](imaging-overview.md)」を参照してください。  
  
 を使用して<xref:System.Windows.Media.ImageBrush>描画するに<xref:System.Windows.Media.Imaging.BitmapImage>は、を作成し、それを使用してビットマップコンテンツを読み込みます。 次<xref:System.Windows.Media.Imaging.BitmapImage>に、を使用して<xref:System.Windows.Media.ImageBrush.ImageSource%2A> 、 <xref:System.Windows.Media.ImageBrush>のプロパティを設定します。 最後に、描画<xref:System.Windows.Media.ImageBrush>するオブジェクトにを適用します。  で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]は、を読み込むイメージのパス<xref:System.Windows.Media.ImageBrush.ImageSource%2A>を使用し<xref:System.Windows.Media.ImageBrush>て、のプロパティを設定することもできます。  
  
 <xref:System.Windows.Media.Brush> すべて<xref:System.Windows.Media.ImageBrush>のオブジェクトと同様に、を使用して、図形、パネル、コントロール、テキストなどのオブジェクトを塗りつぶすことができます。 次の図は、 <xref:System.Windows.Media.ImageBrush>で実現できるいくつかの効果を示しています。  
  
 ![Imagebrush の出力例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush で描画されたオブジェクト  
  
 既定では、 <xref:System.Windows.Media.ImageBrush>は描画される領域を完全に埋めるようにイメージを拡大します。描画された領域の縦横比がイメージよりも異なる場合は、イメージがゆがめられる可能性があります。 この動作を変更するには、 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティを既定値の<xref:System.Windows.Media.Stretch.Fill>から、 <xref:System.Windows.Media.Stretch.None> <xref:System.Windows.Media.Stretch.Uniform>、または<xref:System.Windows.Media.Stretch.UniformToFill>に変更します。 は<xref:System.Windows.Media.ImageBrush> の<xref:System.Windows.Media.TileBrush>一種であるため、イメージブラシが出力領域を塗りつぶす方法を正確に指定し、パターンを作成することもできます。 高度な<xref:System.Windows.Media.TileBrush>機能の詳細については、「[タイルブラシの概要](tilebrush-overview.md)」を参照してください。  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>例:ビットマップイメージを使用したオブジェクトの塗りつぶし  
 次の例では<xref:System.Windows.Media.ImageBrush> 、を使用<xref:System.Windows.Controls.Panel.Background%2A>して<xref:System.Windows.Controls.Canvas>のを描画します。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>描画を使用して領域を塗りつぶす  
 を<xref:System.Windows.Media.DrawingBrush>使用すると、図形、テキスト、画像、およびビデオを使用して領域を塗りつぶすことができます。 描画ブラシ内の図形自体は、純色、グラデーション、イメージ、または別<xref:System.Windows.Media.DrawingBrush>の図形で塗りつぶすことができます。 次の図は、のいくつか<xref:System.Windows.Media.DrawingBrush>の使用方法を示しています。  
  
 ![DrawingBrush の出力例](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush で塗りつぶされたオブジェクト  
  
 は<xref:System.Windows.Media.DrawingBrush> 、オブジェクトを<xref:System.Windows.Media.Drawing>使用して領域を塗りつぶします。 オブジェクト<xref:System.Windows.Media.Drawing>は、形状、ビットマップ、ビデオ、テキスト行など、表示される内容を記述します。 さまざまな種類の描画で、さまざまな種類のコンテンツを記述します。 次の一覧に、さまざまな種類の描画オブジェクトを示します。  
  
- <xref:System.Windows.Media.GeometryDrawing>–図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing>–イメージを描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>–テキストを描画します。  
  
- <xref:System.Windows.Media.VideoDrawing>–オーディオファイルまたはビデオファイルを再生します。  
  
- <xref:System.Windows.Media.DrawingGroup>–他の描画を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.Drawing>オブジェクトの詳細については、「 [Drawing オブジェクトの概要](drawing-objects-overview.md)」を参照してください。  
  
 と同様に、 <xref:System.Windows.Media.DrawingBrush>はを<xref:System.Windows.Media.DrawingBrush.Drawing%2A>拡大して出力領域を塗りつぶします。 <xref:System.Windows.Media.ImageBrush> この動作をオーバーライドするには、 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティをの既定の<xref:System.Windows.Media.Stretch.Fill>設定から変更します。 詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを参照してください。  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>例:描画によるオブジェクトの塗りつぶし  
 次の例は、3 つの楕円の描画によってオブジェクトを塗りつぶす方法を示しています。 <xref:System.Windows.Media.GeometryDrawing>は、省略記号を説明するために使用されます。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>ビジュアルで領域を塗りつぶす  
 すべてのブラシの最も汎用性と強力な機能で<xref:System.Windows.Media.VisualBrush>あるは、を<xref:System.Windows.Media.Visual>使用して領域を描画します。 <xref:System.Windows.Media.Visual>は、多くの便利なグラフィカルコンポーネントの先祖として機能する低レベルのグラフィック型です。 たとえば<xref:System.Windows.Window>、、 <xref:System.Windows.FrameworkElement>、および<xref:System.Windows.Controls.Control>の各クラスは、すべての<xref:System.Windows.Media.Visual>種類のオブジェクトです。 を使用すると[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 、ほとんどすべてのグラフィックオブジェクトを使用して領域を塗りつぶすことができます。<xref:System.Windows.Media.VisualBrush>  
  
> [!NOTE]
> はオブジェクトの<xref:System.Windows.Freezable>型ですが、 <xref:System.Windows.Media.VisualBrush.Visual%2A>プロパティが以外`null`の値に設定されている場合、固定 (読み取り専用) にすることはできません。 <xref:System.Windows.Media.VisualBrush>  
  
 の<xref:System.Windows.Media.VisualBrush.Visual%2A>コンテンツを指定するには、 <xref:System.Windows.Media.VisualBrush>2 つの方法があります。  
  
- 新しい<xref:System.Windows.Media.Visual>を作成し、 <xref:System.Windows.Media.VisualBrush>それを使用し<xref:System.Windows.Media.VisualBrush.Visual%2A>てのプロパティを設定します。 例については、 [次の例を参照してください。次のビジュアル](#examplevisualbrush1)セクションでオブジェクトを塗りつぶします。  
  
- 既存<xref:System.Windows.Media.Visual>のを使用します。これにより、ターゲット<xref:System.Windows.Media.Visual>のイメージが複製されます。 その後、を使用<xref:System.Windows.Media.VisualBrush>して、反射や拡大などの興味深い効果を作成できます。 例については、 [次の例を参照してください。リフレクション](#examplevisualbrush2)セクションを作成します。  
  
 <xref:System.Windows.UIElement> ( <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.VisualBrush> `true`パネルやコントロール<xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A>など<xref:System.Windows.Media.VisualBrush.Visual%2A> ) の新しいを定義すると、プロパティがに設定されている場合、とその子要素でレイアウトシステムが実行されます。<xref:System.Windows.UIElement> ただし、ルート<xref:System.Windows.UIElement>は基本的にシステムの残りの部分から分離されており、外部レイアウトはこの境界をはことはできません。 したがって、ルート<xref:System.Windows.UIElement>のサイズを明示的に指定する必要があります。これは、唯一の<xref:System.Windows.Media.VisualBrush>親がであるため、描画される領域に自動的にサイズを変更することはできないためです。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのレイアウトの詳細については、「[レイアウト](../advanced/layout.md)」を参照してください。  
  
 と<xref:System.Windows.Media.ImageBrush>同様<xref:System.Windows.Media.DrawingBrush>に、 <xref:System.Windows.Media.VisualBrush>は、その内容を出力領域に合わせて拡大します。 この動作をオーバーライドするには、 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティをの既定の<xref:System.Windows.Media.Stretch.Fill>設定から変更します。 詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを参照してください。  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>例:ビジュアルを使用してオブジェクトを塗りつぶす  
 次の例では、さまざまなコントロールとパネルを使用して四角形を塗りつぶします。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>例:反射を作成する  
 前の例では、背景とし<xref:System.Windows.Media.Visual>て使用するために新しいを作成する方法を示しました。 また、を使用し<xref:System.Windows.Media.VisualBrush>て既存のビジュアルを表示することもできます。この機能により、反射や拡大などの興味深い視覚効果を生み出すことができます。 次の例では<xref:System.Windows.Media.VisualBrush> 、を使用して、 <xref:System.Windows.Controls.Border>複数の要素を含むのリフレクションを作成します。 次の図は、この例で生成される出力を示しています。  
  
 ![反映されたビジュアルオブジェクト](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映された Visual オブジェクト  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 画面の一部を引き伸ばす方法と反射を作成する方法のその他の例については、「[VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)」を参照してください。  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush の機能  
 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、および<xref:System.Windows.Media.VisualBrush>は、オブジェクト<xref:System.Windows.Media.TileBrush>の型です。 <xref:System.Windows.Media.TileBrush>オブジェクトを使用すると、イメージ、描画、またはビジュアルを使用して領域を塗りつぶす方法を細かく制御できます。 たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。  
  
 に<xref:System.Windows.Media.TileBrush>は、コンテンツ、タイル、および出力領域という3つの主要コンポーネントがあります。  
  
 ![タイルブラシコンポーネント](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
1つのタイルを持つタイルブラシのコンポーネント  
  
 ![タイル化したタイルブラシのコンポーネント](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
複数のタイルを使用する TileBrush のコンポーネント  
  
 オブジェクトの<xref:System.Windows.Media.TileBrush>タイル機能の詳細については、「[タイルブラシの概要](tilebrush-overview.md)」を参照してください。  
  
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
- [ImageBrush サンプル](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)

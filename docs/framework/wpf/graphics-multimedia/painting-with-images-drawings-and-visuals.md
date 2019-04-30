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
ms.openlocfilehash: 826c5a0656a9a7e7cff0e96fc6755c5c9c717993
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002288"
---
# <a name="painting-with-images-drawings-and-visuals"></a>イメージ、描画、およびビジュアルによる塗りつぶし
このトピックでは、使用する方法を説明します<xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、および<xref:System.Windows.Media.VisualBrush>イメージで領域を塗りつぶすオブジェクト、 <xref:System.Windows.Media.Drawing>、または<xref:System.Windows.Media.Visual>します。  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] に用意されているさまざまな種類のブラシとその基本的な機能を理解している必要があります。 概要については、「[WPF のブラシの概要](wpf-brushes-overview.md)」を参照してください。  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>イメージで領域を塗りつぶす  
 <xref:System.Windows.Media.ImageBrush>で領域を塗りつぶす、<xref:System.Windows.Media.ImageSource>します。 最も一般的な種類<xref:System.Windows.Media.ImageSource>で使用する、<xref:System.Windows.Media.ImageBrush>は、 <xref:System.Windows.Media.Imaging.BitmapImage>、ビットマップ グラフィックについて説明します。 使用することができます、<xref:System.Windows.Media.DrawingImage>を使用して描画する、<xref:System.Windows.Media.Drawing>が、オブジェクトが使いやすく、<xref:System.Windows.Media.DrawingBrush>代わりにします。 詳細については<xref:System.Windows.Media.ImageSource>、オブジェクトを参照してください、[イメージングの概要](imaging-overview.md)します。  
  
 描画に使用する、 <xref:System.Windows.Media.ImageBrush>、作成、<xref:System.Windows.Media.Imaging.BitmapImage>ビットマップ コンテンツの読み込みに使用します。 次に、使用、<xref:System.Windows.Media.Imaging.BitmapImage>を設定する、<xref:System.Windows.Media.ImageBrush.ImageSource%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>します。 最後に、適用、<xref:System.Windows.Media.ImageBrush>を描画するオブジェクト。  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、だけでも設定することができます、<xref:System.Windows.Media.ImageBrush.ImageSource%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>読み込む画像のパスを使用します。  
  
 などのすべて<xref:System.Windows.Media.Brush>、オブジェクト、<xref:System.Windows.Media.ImageBrush>図形、パネル、コントロール、およびテキストなどのオブジェクトの描画に使用できます。 次の図に、いくつかの効果を達成できる、<xref:System.Windows.Media.ImageBrush>します。  
  
 ![ImageBrush の出力例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush で描画されたオブジェクト  
  
 既定で、<xref:System.Windows.Media.ImageBrush>領域がいっぱいにするには、そのイメージで描画される端まで拡大、イメージを引き伸ばして、描画領域のイメージよりも異なる縦横比がある場合。 この動作を変更するには変更することで、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティの既定値から<xref:System.Windows.Media.Stretch.Fill>に<xref:System.Windows.Media.Stretch.None>、 <xref:System.Windows.Media.Stretch.Uniform>、または<xref:System.Windows.Media.Stretch.UniformToFill>。 <xref:System.Windows.Media.ImageBrush>の種類は、 <xref:System.Windows.Media.TileBrush>、正確にイメージ ブラシが出力領域を塗りつぶす方法を指定し、パターンを作成することもできます。 詳細設定の詳細については<xref:System.Windows.Media.TileBrush>については、「、 [TileBrush の概要](tilebrush-overview.md)します。  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>例:ビットマップ イメージによるオブジェクトを塗りつぶし  
 次の例では、<xref:System.Windows.Media.ImageBrush>を描画する、<xref:System.Windows.Controls.Panel.Background%2A>の<xref:System.Windows.Controls.Canvas>します。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>描画を使用して領域を塗りつぶす  
 A<xref:System.Windows.Media.DrawingBrush>すると、図形、テキスト、イメージ、およびビデオで領域を塗りつぶすことができます。 描画ブラシ内の図形が自体を描画する純色、グラデーション、イメージを別または<xref:System.Windows.Media.DrawingBrush>します。 次の図は、のいくつかの使用を示しています、<xref:System.Windows.Media.DrawingBrush>します。  
  
 ![DrawingBrush の出力例](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush で塗りつぶされたオブジェクト  
  
 A<xref:System.Windows.Media.DrawingBrush>で領域を塗りつぶす、<xref:System.Windows.Media.Drawing>オブジェクト。 A<xref:System.Windows.Media.Drawing>オブジェクトには、図形、ビットマップ、ビデオ、または行のテキストなど、表示されるコンテンツがについて説明します。 さまざまな種類の描画で、さまざまな種類のコンテンツを記述します。 次の一覧に、さまざまな種類の描画オブジェクトを示します。  
  
- <xref:System.Windows.Media.GeometryDrawing> – 図形を描画します。  
  
- <xref:System.Windows.Media.ImageDrawing> – イメージを描画します。  
  
- <xref:System.Windows.Media.GlyphRunDrawing> – テキストを描画します。  
  
- <xref:System.Windows.Media.VideoDrawing> – オーディオまたはビデオ ファイルを再生します。  
  
- <xref:System.Windows.Media.DrawingGroup> – 他の描画を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください、 [Drawing オブジェクトの概要](drawing-objects-overview.md)します。  
  
 ように、 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>拡大その<xref:System.Windows.Media.DrawingBrush.Drawing%2A>出力領域に挿入します。 この動作をオーバーライドするには、変更することで、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティの既定の設定から<xref:System.Windows.Media.Stretch.Fill>します。 詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを参照してください。  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>例:描画によるオブジェクトの塗りつぶし  
 次の例は、3 つの楕円の描画によってオブジェクトを塗りつぶす方法を示しています。 A<xref:System.Windows.Media.GeometryDrawing>省略記号を記述するために使用します。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>ビジュアルで領域を塗りつぶす  
 最も汎用性の高いで、すべてのブラシの強力な<xref:System.Windows.Media.VisualBrush>で領域を塗りつぶす、<xref:System.Windows.Media.Visual>します。 A<xref:System.Windows.Media.Visual>は多くの便利なグラフィカルなコンポーネントの親として機能する低レベルのグラフィカル型です。 たとえば、 <xref:System.Windows.Window>、 <xref:System.Windows.FrameworkElement>、および<xref:System.Windows.Controls.Control>クラスは、すべての種類の<xref:System.Windows.Media.Visual>オブジェクト。 使用して、 <xref:System.Windows.Media.VisualBrush>、ほぼすべての領域を塗りつぶすことができます[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グラフィカル オブジェクト。  
  
> [!NOTE]
>  <xref:System.Windows.Media.VisualBrush>の種類は、<xref:System.Windows.Freezable>オブジェクト、それを固定することはできません (読み取り専用に) とその<xref:System.Windows.Media.VisualBrush.Visual%2A>プロパティが以外の値に設定されて`null`します。  
  
 2 つの方法を指定する、<xref:System.Windows.Media.VisualBrush.Visual%2A>のコンテンツを<xref:System.Windows.Media.VisualBrush>します。  
  
- 新規作成<xref:System.Windows.Media.Visual>に設定して、<xref:System.Windows.Media.VisualBrush.Visual%2A>のプロパティ、<xref:System.Windows.Media.VisualBrush>します。 例については、次を参照してください。、[例。ビジュアルを使用してオブジェクトのペイント](#examplevisualbrush1)以下のセクション。  
  
- 既存の使用<xref:System.Windows.Media.Visual>、ターゲットの重複するイメージを作成する<xref:System.Windows.Media.Visual>します。 使用することができますし、<xref:System.Windows.Media.VisualBrush>反射や拡大などの興味深い効果を作成します。 例については、次を参照してください。、[例。反射を作成する](#examplevisualbrush2)セクション。  
  
 新しいを定義するとき<xref:System.Windows.Media.VisualBrush.Visual%2A>の<xref:System.Windows.Media.VisualBrush>と<xref:System.Windows.Media.Visual>は、 <xref:System.Windows.UIElement> (パネルやコントロール) など、レイアウト システムがで実行、<xref:System.Windows.UIElement>とその子要素と、<xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A>プロパティに設定されて`true`。 ただし、ルート<xref:System.Windows.UIElement>は基本的に、システムの残りの部分から分離されます。 スタイル、および外部のレイアウトは、この境界を超えることはできません。 そのため、ルートのサイズを指定する必要があります明示的に<xref:System.Windows.UIElement>はの唯一の親であるため、<xref:System.Windows.Media.VisualBrush>し、そのため、できませんサイズを自動的に塗りつぶされる領域にします。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのレイアウトの詳細については、「[レイアウト](../advanced/layout.md)」を参照してください。  
  
 ような<xref:System.Windows.Media.ImageBrush>と<xref:System.Windows.Media.DrawingBrush>、<xref:System.Windows.Media.VisualBrush>出力領域に挿入するには、そのコンテンツを拡大します。 この動作をオーバーライドするには、変更することで、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティの既定の設定から<xref:System.Windows.Media.Stretch.Fill>します。 詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを参照してください。  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>例:ビジュアルを使用してオブジェクトを塗りつぶし  
 次の例では、さまざまなコントロールとパネルを使用して四角形を塗りつぶします。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>例:反射を作成する  
 前の例では、新しいを作成する方法を示しました<xref:System.Windows.Media.Visual>を背景として使用します。 使用することも、<xref:System.Windows.Media.VisualBrush>既存のビジュアルを表示するこの機能では、反射や拡大などの興味深い視覚効果を生成することができます。 次の例では、<xref:System.Windows.Media.VisualBrush>の反射を作成、<xref:System.Windows.Controls.Border>いくつかの要素を格納しています。 次の図は、この例で生成される出力を示しています。  
  
 ![A がビジュアル オブジェクトを反映](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映された Visual オブジェクト  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 画面の一部を引き伸ばす方法と反射を作成する方法のその他の例については、「[VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)」を参照してください。  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush の機能  
 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、および<xref:System.Windows.Media.VisualBrush>種類<xref:System.Windows.Media.TileBrush>オブジェクト。 <xref:System.Windows.Media.TileBrush> オブジェクトを提供する非常に大量のイメージ、描画、またはビジュアルで領域を塗りつぶす方法を制御します。 たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。  
  
 A<xref:System.Windows.Media.TileBrush>が 3 つの主要なコンポーネント: コンテンツ、タイル、および出力領域。  
  
 ![TileBrush コンポーネント](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
1 つのタイルを使用する TileBrush のコンポーネント  
  
 ![並べて表示された TileBrush のコンポーネント](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
複数のタイルを使用する TileBrush のコンポーネント  
  
 タイル表示機能の詳細については<xref:System.Windows.Media.TileBrush>、オブジェクトを参照してください、 [TileBrush の概要](tilebrush-overview.md)します。  
  
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
- [ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)

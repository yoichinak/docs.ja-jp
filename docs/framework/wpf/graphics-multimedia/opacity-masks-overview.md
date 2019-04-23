---
title: 不透明度マスクの概要
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 84525e58487ce9b0bc26f77ff8dbced734bc90a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080086"
---
# <a name="opacity-masks-overview"></a>不透明度マスクの概要
不透明度マスクを使用すると、要素またはビジュアルの一部を透明にするか、部分的に透明にすることができます。 適用する不透明度マスクを作成する、<xref:System.Windows.Media.Brush>を<xref:System.Windows.UIElement.OpacityMask%2A>要素のプロパティまたは<xref:System.Windows.Media.Visual>します。  ブラシが要素またはビジュアルにマップされ、ブラシの各ピクセルの不透明度値を使用して、要素またはビジュアルの対応する各ピクセルの不透明度が決まります。  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 この概要に精通していることを前提としています。<xref:System.Windows.Media.Brush>オブジェクト。 ブラシの使用方法の概要については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。 について<xref:System.Windows.Media.ImageBrush>と<xref:System.Windows.Media.DrawingBrush>を参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>不透明度マスクを使用した視覚効果の作成  
 不透明度マスクは、要素またはビジュアルにその内容をマッピングすることによって機能します。 各ブラシのピクセルのアルファ チャネルを使用して、要素またはビジュアルの対応するピクセルの最終的な不透明度が決定され、ブラシの実際の色は無視されます。 ブラシの特定の部分が透明な場合、要素またはビジュアルの対応する部分は透明になります。 ブラシの特定の部分が不透明な場合、要素またはビジュアルの対応する部分は変化しません。 不透明度マスクによって指定された不透明度は、要素またはビジュアルに指定されている不透明度の設定と組み合わされます。 たとえば、要素の不透明度が 25% であるときに、完全に不透明な状態から完全に透明な状態に遷移する不透明度マスクが適用された場合、要素は、25% の不透明度から完全に透明な状態に遷移します。  
  
> [!NOTE]
>  不透明度マスクは任意の要素に適用できますが、この概要の例では、イメージ要素に対する不透明度マスクの使用を示すため、または<xref:System.Windows.Media.Visual>パネルとコントロールを含め、します。  
  
 不透明度マスクは、徐々に消えていくイメージやボタンの作成、要素へのテクスチャの追加、グラデーションと組み合わせたガラスのような表面の生成などの注意を引き付ける視覚効果を作成するために使用します。 次の図は、不透明度マスクの使用例を示しています。 チェックの背景を使用して、マスクの透明な部分を表示しています。  
  
 ![LinearGradientBrush 不透明度マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
不透明度マスクの例  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>不透明度マスクの作成  
 作成する不透明度マスクを作成する、<xref:System.Windows.Media.Brush>に適用し、<xref:System.Windows.UIElement.OpacityMask%2A>要素またはビジュアルのプロパティ。 任意の型を使用する<xref:System.Windows.Media.Brush>不透明度マスクとして。  
  
-   <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>:要素またはビジュアルから徐々 に使用されます。  
  
     次の図は、<xref:System.Windows.Media.LinearGradientBrush>不透明度マスクとして使用します。  
  
     ![LinearGradientBrush 不透明度マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
LinearGradientBrush 不透明度マスクの例  
  
-   <xref:System.Windows.Media.ImageBrush>:テクスチャおよびエッジ効果のぼかしや破棄を作成するために使用します。  
  
     次の図は、<xref:System.Windows.Media.ImageBrush>不透明度マスクとして使用します。  
  
     ![ImageBrush 不透明度マスクを含むオブジェクト](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
LinearGradientBrush 不透明度マスクの例  
  
-   <xref:System.Windows.Media.DrawingBrush>:図形、イメージ、およびグラデーションのパターンから複雑な不透明度マスクを作成するために使用します。  
  
     次の図は、<xref:System.Windows.Media.DrawingBrush>不透明度マスクとして使用します。  
  
     ![DrawingBrush 不透明マスクを持つオブジェクト](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
DrawingBrush 不透明度マスクの例  
  
 グラデーション ブラシ (<xref:System.Windows.Media.LinearGradientBrush>と<xref:System.Windows.Media.RadialGradientBrush>)、不透明度マスクとして使用するため特に適しています。 <xref:System.Windows.Media.SolidColorBrush>均一色で領域を塗りつぶし、不透明度をようにマスク; を使用して、<xref:System.Windows.Media.SolidColorBrush>要素またはビジュアルの設定と同じには、<xref:System.Windows.UIElement.OpacityMask%2A>プロパティ。  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>不透明度マスクとしてのグラデーションの使用  
 グラデーション塗りつぶしを作成するには、2 つ以上のグラデーションの分岐点を指定します。 各グラデーションの分岐点には、カラーと位置を記述します (グラデーションの作成と使用の詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください)。 プロセスは、グラデーションを不透明度マスクとして使用するときと同じですが、不透明度マスクのグラデーションでは、カラーをブレンドするのではなく、アルファ チャネル値をブレンドします。 したがって、グラデーションのコンテンツの実際の色は問題になりません。重要なのは、それぞれのカラーのアルファ チャネル (不透明度) です。 次に例を示します。  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>不透明度マスクのグラデーションの分岐点の指定  
 前の例では、システム定義の色で<xref:System.Windows.Media.Colors.Black%2A>グラデーションの開始色として使用されます。 ため、すべての色の<xref:System.Windows.Media.Colors>クラスを除く<xref:System.Windows.Media.Colors.Transparent%2A>が完全に不透明で、単にグラデーション不透明度マスクの開始色を定義できます。  
  
 不透明度マスクを定義するときに、アルファ値をさらに制御を使用して色のアルファ チャネルを指定できます[!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)]マークアップを使用してまたは 16 進数表記、<xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType>メソッド。  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" でのカラーの不透明度の指定  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、[!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] の 16 進表記を使用して、個々の色の不透明度を指定します。 [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] の 16 進表記では、次の構文を使用します。  
  
 `#` **aa** *rrggbb*  
  
 前の行の *aa* は、カラーの不透明度を指定するために使用する 2 桁の 16 進値を表します。 *rr*、*gg*、および *bb* は、それぞれ、カラーの赤、緑、および青の量を指定するために使用される 2 桁の 16 進値を表します。 各 16 進数には、0 ～ 9 または A ～ F の値を指定できます。 0 は最小値であり、F は最大値です。 アルファ値 00 は完全に透明なカラーを指定し、アルファ値 FF は完全に不透明なカラーを指定します。  次の例では、[!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] の 16 進表記を使用して、2 つのカラーを指定しています。 1 つ目のカラーは完全に透明であり、2 つ目のカラーは完全に不透明です。  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>不透明度マスクとしてのイメージの使用  
 不透明度マスクとしてイメージを使用することもできます。 次のイメージは一例を示しています。 チェックの背景を使用して、マスクの透明な部分を表示しています。  
  
 ![ImageBrush 不透明度マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
不透明度マスクの例  
  
 不透明度マスクとしてイメージを使用する、<xref:System.Windows.Media.ImageBrush>イメージを格納します。 不透明度マスクとして使用するイメージを作成したら、複数のレベルの透過性をサポートする形式 ([!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]など) で保存します。 次の例は、前の図を作成するために使用するコード例を示しています。  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>不透明度マスクとしてタイル イメージを使用する  
 他の次の例では、同じイメージが使用される<xref:System.Windows.Media.ImageBrush>がブラシのタイル機能は、イメージ 50 ピクセルの正方形のタイルを生成するために使用されます。  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>描画からの不透明度マスクの作成  
 不透明度マスクとして描画を使用できます。 描画内の図形自体を、グラデーション、純色、イメージ、または他の描画で塗りつぶすことができます。 次のイメージは、不透明度マスクとして使用される描画の例です。 チェックの背景を使用して、マスクの透明な部分を表示しています。  
  
 ![DrawingBrush 不透明マスクを持つオブジェクト](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
DrawingBrush 不透明度マスクの例  
  
 不透明度マスクとして描画を使用する、<xref:System.Windows.Media.DrawingBrush>に描画します。 次の例は、前の図を作成するために使用するコード例を示しています。  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>不透明度マスクとしてタイル描画を使用する  
 ように、 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>描画をタイルに行んだことができます。 次の例では、描画ブラシを使用して、タイル表示される不透明マスクを作成できます。  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>関連項目

- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)

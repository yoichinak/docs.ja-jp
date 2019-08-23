---
title: 不透明度マスクの概要
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: d0fea1aac4efb17811404ce45769615bb2e7234f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929655"
---
# <a name="opacity-masks-overview"></a>不透明度マスクの概要
不透明度マスクを使用すると、要素またはビジュアルの一部を透明にするか、部分的に透明にすることができます。 不透明度マスクを作成するには<xref:System.Windows.Media.Brush> 、要素<xref:System.Windows.UIElement.OpacityMask%2A>または<xref:System.Windows.Media.Visual>のプロパティにを適用します。  ブラシが要素またはビジュアルにマップされ、ブラシの各ピクセルの不透明度値を使用して、要素またはビジュアルの対応する各ピクセルの不透明度が決まります。  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 この概要では、オブジェクトについ<xref:System.Windows.Media.Brush>て理解していることを前提としています。 ブラシの使用方法の概要については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。 およびの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)」を参照してください。 <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.ImageBrush>  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>不透明度マスクを使用した視覚効果の作成  
 不透明度マスクは、要素またはビジュアルにその内容をマッピングすることによって機能します。 各ブラシのピクセルのアルファ チャネルを使用して、要素またはビジュアルの対応するピクセルの最終的な不透明度が決定され、ブラシの実際の色は無視されます。 ブラシの特定の部分が透明な場合、要素またはビジュアルの対応する部分は透明になります。 ブラシの特定の部分が不透明な場合、要素またはビジュアルの対応する部分は変化しません。 不透明度マスクによって指定された不透明度は、要素またはビジュアルに指定されている不透明度の設定と組み合わされます。 たとえば、要素の不透明度が 25% であるときに、完全に不透明な状態から完全に透明な状態に遷移する不透明度マスクが適用された場合、要素は、25% の不透明度から完全に透明な状態に遷移します。  
  
> [!NOTE]
> この概要の例では、イメージ要素の不透明マスクの使用方法を示していますが、不透明度マスクは<xref:System.Windows.Media.Visual>、パネルやコントロールを含む任意の要素またはに適用できます。  
  
 不透明度マスクは、徐々に消えていくイメージやボタンの作成、要素へのテクスチャの追加、グラデーションと組み合わせたガラスのような表面の生成などの注意を引き付ける視覚効果を作成するために使用します。 次の図は、不透明度マスクの使用例を示しています。 チェックの背景を使用して、マスクの透明な部分を表示しています。  
  
 ![System.windows.media.lineargradientbrush> opacity マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
不透明度マスクの例  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>不透明度マスクの作成  
 不透明度マスクを作成するには<xref:System.Windows.Media.Brush> 、を作成して<xref:System.Windows.UIElement.OpacityMask%2A> 、要素またはビジュアルのプロパティに適用します。 の任意の<xref:System.Windows.Media.Brush>型を不透明度マスクとして使用できます。  
  
- <xref:System.Windows.Media.LinearGradientBrush>、<xref:System.Windows.Media.RadialGradientBrush>:要素またはビジュアルをビューからフェードさせるために使用します。  
  
     次の図は、 <xref:System.Windows.Media.LinearGradientBrush>不透明度マスクとして使用されるを示しています。  
  
     ![System.windows.media.lineargradientbrush> opacity マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
LinearGradientBrush 不透明度マスクの例  
  
- <xref:System.Windows.Media.ImageBrush>:テクスチャ、ソフト、または破損したエッジ効果を作成するために使用されます。  
  
     次の図は、 <xref:System.Windows.Media.ImageBrush>不透明度マスクとして使用されるを示しています。  
  
     ![ImageBrush 不透明マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
LinearGradientBrush 不透明度マスクの例  
  
- <xref:System.Windows.Media.DrawingBrush>:図形、画像、およびグラデーションのパターンから複雑な不透明度マスクを作成するために使用します。  
  
     次の図は、 <xref:System.Windows.Media.DrawingBrush>不透明度マスクとして使用されるを示しています。  
  
     ![DrawingBrush opacity マスクを持つオブジェクト](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
DrawingBrush 不透明度マスクの例  
  
 グラデーションブラシ (<xref:System.Windows.Media.LinearGradientBrush>および<xref:System.Windows.Media.RadialGradientBrush>) は、不透明度マスクとして使用する場合に特に適しています。 は、 <xref:System.Windows.Media.SolidColorBrush>均一な色で領域を塗りつぶすため、不透明マスクが不適切になり<xref:System.Windows.Media.SolidColorBrush>ます。を使用することは、要素の<xref:System.Windows.UIElement.OpacityMask%2A>プロパティまたはビジュアルのプロパティを設定することと同じです。  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>不透明度マスクとしてのグラデーションの使用  
 グラデーション塗りつぶしを作成するには、2 つ以上のグラデーションの分岐点を指定します。 各グラデーションの分岐点には、カラーと位置を記述します (グラデーションの作成と使用の詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください)。 プロセスは、グラデーションを不透明度マスクとして使用するときと同じですが、不透明度マスクのグラデーションでは、カラーをブレンドするのではなく、アルファ チャネル値をブレンドします。 したがって、グラデーションのコンテンツの実際の色は問題になりません。重要なのは、それぞれのカラーのアルファ チャネル (不透明度) です。 次に例を示します。  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>不透明度マスクのグラデーションの分岐点の指定  
 前の例では、システム定義色<xref:System.Windows.Media.Colors.Black%2A>がグラデーションの開始色として使用されています。 を除き<xref:System.Windows.Media.Colors> <xref:System.Windows.Media.Colors.Transparent%2A>、クラスのすべての色は完全に不透明であるため、グラデーション不透明度マスクの開始色を定義するために使用できます。  
  
 不透明度マスクを定義するときにアルファ値をさらに制御するには、マークアップで ARGB 16 進表記を使用する<xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType>か、メソッドを使用して、色のアルファチャネルを指定します。  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" でのカラーの不透明度の指定  
 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]は、ARGB 16 進表記を使用して、個々の色の不透明度を指定します。 ARGB 16 進数表記では、次の構文を使用します。  
  
 `#` **aa** *rrggbb*  
  
 前の行の *aa* は、カラーの不透明度を指定するために使用する 2 桁の 16 進値を表します。 *rr*、*gg*、および *bb* は、それぞれ、カラーの赤、緑、および青の量を指定するために使用される 2 桁の 16 進値を表します。 各 16 進数には、0 ～ 9 または A ～ F の値を指定できます。 0 は最小値であり、F は最大値です。 アルファ値 00 は完全に透明なカラーを指定し、アルファ値 FF は完全に不透明なカラーを指定します。  次の例では、16進数の ARGB 表記を使用して2つの色を指定しています。 1 つ目のカラーは完全に透明であり、2 つ目のカラーは完全に不透明です。  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>不透明度マスクとしてのイメージの使用  
 不透明度マスクとしてイメージを使用することもできます。 次のイメージは一例を示しています。 チェックの背景を使用して、マスクの透明な部分を表示しています。  
  
 ![ImageBrush 不透明マスクを持つオブジェクト](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
不透明度マスクの例  
  
 イメージを不透明度マスクとして使用するに<xref:System.Windows.Media.ImageBrush>は、を使用してイメージを格納します。 不透明度マスクとして使用するイメージを作成する場合は、PNG (Portable Network Graphics) などの複数レベルの透明度をサポートする形式で画像を保存します。 次の例は、前の図を作成するために使用するコード例を示しています。  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>不透明度マスクとしてタイル イメージを使用する  
 次の例では、同じイメージが別<xref:System.Windows.Media.ImageBrush>のイメージと共に使用されますが、ブラシのタイル機能を使用して、イメージ50ピクセルの正方形のタイルが生成されます。  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>描画からの不透明度マスクの作成  
 不透明度マスクとして描画を使用できます。 描画内の図形自体を、グラデーション、純色、イメージ、または他の描画で塗りつぶすことができます。 次のイメージは、不透明度マスクとして使用される描画の例です。 チェックの背景を使用して、マスクの透明な部分を表示しています。  
  
 ![DrawingBrush opacity マスクを持つオブジェクト](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
DrawingBrush 不透明度マスクの例  
  
 描画を不透明度マスクとして使用するに<xref:System.Windows.Media.DrawingBrush>は、を使用して描画を格納します。 次の例は、前の図を作成するために使用するコード例を示しています。  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>不透明度マスクとしてタイル描画を使用する  
 と同様に、 <xref:System.Windows.Media.DrawingBrush>描画を並べて表示することができます。 <xref:System.Windows.Media.ImageBrush> 次の例では、描画ブラシを使用して、タイル表示される不透明マスクを作成できます。  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>関連項目

- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)

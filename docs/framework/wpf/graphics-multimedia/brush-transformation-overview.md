---
title: ブラシの変換の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186525"
---
# <a name="brush-transformation-overview"></a>ブラシの変換の概要
Brush クラスには、2 つの<xref:System.Windows.Media.Brush.Transform%2A>変換<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティと の 2 つの変換プロパティがあります。 これらのプロパティを使うと、ブラシの内容を回転、拡大縮小、傾斜、移動できます。 このトピックでは、これら 2 つのプロパティの違いについて説明し、それらの使用例を示します。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、変換するブラシの機能を理解している必要があります。 および<xref:System.Windows.Media.LinearGradientBrush><xref:System.Windows.Media.RadialGradientBrush>については、「 および[グラデーションの塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。 または の<xref:System.Windows.Media.ImageBrush>場合<xref:System.Windows.Media.VisualBrush>は、「 イメージ[、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。 <xref:System.Windows.Media.DrawingBrush> また、「[変換の概要](transforms-overview.md)」で説明されている 2D 変換についても理解しておく必要があります。  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform プロパティと RelativeTransform プロパティの違い  
 ブラシの<xref:System.Windows.Media.Brush.Transform%2A>プロパティに変換を適用する場合、ブラシの中心に関するブラシの内容を変換する場合は、ペイント領域のサイズを知る必要があります。 描画領域の幅が 200 デバイス独立ピクセル、高さが 150 ピクセルであるものとします。  ブラシの<xref:System.Windows.Media.RotateTransform>出力を中心に 45 度回転させた場合は、100 の<xref:System.Windows.Media.RotateTransform>a<xref:System.Windows.Media.RotateTransform.CenterX%2A>と 75 を<xref:System.Windows.Media.RotateTransform.CenterY%2A>与えます。  
  
 ブラシの<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに変換を適用すると、その変換はブラシに適用されてから、その出力がペイントされた領域にマップされます。 次の一覧では、ブラシの内容が処理および変換される順序を説明します。  
  
1. ブラシの内容を処理します。 の場合<xref:System.Windows.Media.GradientBrush>、グラデーション領域を決定します。 <xref:System.Windows.Media.TileBrush>の場合<xref:System.Windows.Media.TileBrush.Viewbox%2A>は、 が にマップ<xref:System.Windows.Media.TileBrush.Viewport%2A>されます。 これがブラシの出力になります。  
  
2. ブラシの出力を 1 x 1 の変換四角形に投影します。  
  
3. ブラシが<xref:System.Windows.Media.Brush.RelativeTransform%2A>ある場合は、ブラシを適用します。  
  
4. 変換された出力を描画領域に投影します。  
  
5. ブラシが<xref:System.Windows.Media.Transform>ある場合は、ブラシを適用します。  
  
 ブラシの<xref:System.Windows.Media.Brush.RelativeTransform%2A>出力が 1 x 1 の四角形にマップされている間に が適用されるため、変換の中心とオフセットの値は相対的に見えます。 たとえば、a<xref:System.Windows.Media.RotateTransform>を使用してブラシの出力を中心の 45 度回転させた場合、0.5、0.5 の<xref:System.Windows.Media.RotateTransform>a<xref:System.Windows.Media.RotateTransform.CenterY%2A><xref:System.Windows.Media.RotateTransform.CenterX%2A>を指定します。  
  
 次の図は、 プロパティと プロパティを使用して 45 度回転した複数<xref:System.Windows.Media.Brush.RelativeTransform%2A>の<xref:System.Windows.Media.Brush.Transform%2A>ブラシの出力を示しています。  
  
 ![RelativeTransform プロパティと Transform プロパティ](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>TileBrush での RelativeTransform の使用  
 タイル ブラシは他のブラシよりも複雑であるため、a<xref:System.Windows.Media.Brush.RelativeTransform%2A>を適用すると予期しない結果が生じる可能性があります。 たとえば、次のようなイメージについて考えます。  
  
 ![ソース イメージ](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 次の例では、<xref:System.Windows.Media.ImageBrush>を使用して、前のイメージで四角形の領域を描画します。 オブジェクト<xref:System.Windows.Media.RotateTransform>の<xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに a を適用し、その<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティを<xref:System.Windows.Media.Stretch.UniformToFill>に設定します。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 この例の結果は、次のようになります。  
  
 ![変換された出力](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 ブラシが に設定<xref:System.Windows.Media.TileBrush.Stretch%2A>されていても、イメージがゆがんでいる点に<xref:System.Windows.Media.Stretch.UniformToFill>注意してください。 これは、ブラシが の相対変換がブラシにマップされた後<xref:System.Windows.Media.TileBrush.Viewbox%2A>に適用されるためです<xref:System.Windows.Media.TileBrush.Viewport%2A>。 次の一覧では、処理の各ステップについて説明します。  
  
1. ブラシの<xref:System.Windows.Media.TileBrush.Stretch%2A>設定を使用して、<xref:System.Windows.Media.TileBrush.Viewbox%2A>ブラシの内容 ( )<xref:System.Windows.Media.TileBrush.Viewport%2A>を基本タイル ( ) に投影します。  
  
     ![ビューポートに合わせて Viewbox を拡大](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. 基本タイルを 1 x 1 の変換四角形に投影します。  
  
     ![ビューポートを変換四角形に割り当て](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. を適用<xref:System.Windows.Media.RotateTransform>します。  
  
     ![相対変換の適用](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. 変換された基本タイルを描画領域に投影します。  
  
     ![変換されたブラシを出力領域に反映](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>例: ImageBrush を 45 度回転する  
 次の例では、<xref:System.Windows.Media.RotateTransform>の<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに<xref:System.Windows.Media.ImageBrush>a を適用します。 オブジェクト<xref:System.Windows.Media.RotateTransform>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティは<xref:System.Windows.Media.RotateTransform.CenterX%2A>、コンテンツの中心点の相対座標である 0.5 に設定されます。 その結果、ブラシの内容は中心の周りに回転されます。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>に<xref:System.Windows.Media.ImageBrush>a も適用<xref:System.Windows.Media.Brush.Transform%2A>しますが、プロパティ<xref:System.Windows.Media.Brush.RelativeTransform%2A>の代わりにプロパティを使用します。 ブラシを中心に回転させるには、オブジェクトの<xref:System.Windows.Media.RotateTransform>を回転<xref:System.Windows.Media.RotateTransform.CenterX%2A>させる必要<xref:System.Windows.Media.RotateTransform.CenterY%2A>があります。 ブラシによって描画される四角形は 175 x 90 ピクセルなので、その中心点は (87.5, 45) です。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 次の図は、トランスフォームのないブラシ、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに適用された変換、およびプロパティに適用された変換を<xref:System.Windows.Media.Brush.Transform%2A>示しています。  
  
 ![ブラシ RelativeTransform と変換の設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 この例は、さらに大きなサンプルの一部です。 完全なサンプルについては、[ブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)を参照してください。 ブラシについて詳しくは、「[WPF のブラシの概要](wpf-brushes-overview.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [変換の概要](transforms-overview.md)

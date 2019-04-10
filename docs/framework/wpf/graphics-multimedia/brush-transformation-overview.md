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
ms.openlocfilehash: 39b3ad9bebfc56002f77ad6e9026a4446c95455b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298332"
---
# <a name="brush-transformation-overview"></a>ブラシの変換の概要
Brush クラスには 2 つの変換プロパティ:<xref:System.Windows.Media.Brush.Transform%2A>と<xref:System.Windows.Media.Brush.RelativeTransform%2A>します。 これらのプロパティを使うと、ブラシの内容を回転、拡大縮小、傾斜、移動できます。 このトピックでは、これら 2 つのプロパティの違いについて説明し、それらの使用例を示します。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、変換するブラシの機能を理解している必要があります。 <xref:System.Windows.Media.LinearGradientBrush>と<xref:System.Windows.Media.RadialGradientBrush>を参照してください、[純色およびグラデーション概要](painting-with-solid-colors-and-gradients-overview.md)します。 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>を参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。 また、「[変換の概要](transforms-overview.md)」で説明されている 2D 変換についても理解しておく必要があります。  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform プロパティと RelativeTransform プロパティの違い  
 ブラシの変換を適用する<xref:System.Windows.Media.Brush.Transform%2A>プロパティ、その中心の周りのブラシの内容を変換する場合は、塗りつぶされる領域のサイズを把握する必要があります。 描画領域の幅が 200 デバイス独立ピクセル、高さが 150 ピクセルであるものとします。  使用した場合、<xref:System.Windows.Media.RotateTransform>ブラシの回転の中心の周りに 45 度を出力、指定、 <xref:System.Windows.Media.RotateTransform> 、 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 と<xref:System.Windows.Media.RotateTransform.CenterY%2A>75 の。  
  
 ブラシの変換を適用する<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティ、その出力が塗りつぶされる領域にマップされる前に、その変換がブラシに適用されます。 次の一覧では、ブラシの内容が処理および変換される順序を説明します。  
  
1. ブラシの内容を処理します。 <xref:System.Windows.Media.GradientBrush>、これは、グラデーションの領域を決定することを意味します。 <xref:System.Windows.Media.TileBrush>、<xref:System.Windows.Media.TileBrush.Viewbox%2A>にマップされて、<xref:System.Windows.Media.TileBrush.Viewport%2A>します。 これがブラシの出力になります。  
  
2. ブラシの出力を 1 x 1 の変換四角形に投影します。  
  
3. ブラシの適用<xref:System.Windows.Media.Brush.RelativeTransform%2A>があるいずれかの場合。  
  
4. 変換された出力を描画領域に投影します。  
  
5. ブラシの適用<xref:System.Windows.Media.Transform>があるいずれかの場合。  
  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>ブラシの出力は 1 x 1 サイズの四角形、変換の中心にマップされ、相対オフセット値が表示されるときに適用されます。 使用した場合など、<xref:System.Windows.Media.RotateTransform>ブラシの回転の中心の周りに 45 度を出力、指定、 <xref:System.Windows.Media.RotateTransform> 、 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0.5 と<xref:System.Windows.Media.RotateTransform.CenterY%2A>0.5 の。  
  
 次の図は、使って 45 度回転されたいくつかのブラシの出力、<xref:System.Windows.Media.Brush.RelativeTransform%2A>と<xref:System.Windows.Media.Brush.Transform%2A>プロパティ。  
  
 ![RelativeTransform プロパティと Transform プロパティ](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>TileBrush での RelativeTransform の使用  
 タイル ブラシは、その他のブラシより複雑であるために適用、<xref:System.Windows.Media.Brush.RelativeTransform%2A>いずれかに予期しない結果が生じる可能性があります。 たとえば、次のようなイメージについて考えます。  
  
 ![ソース イメージ](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 次の例では、<xref:System.Windows.Media.ImageBrush>上の図で四角形の領域を描画します。 適用される、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.ImageBrush>オブジェクトの<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティ、およびセットの<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティを<xref:System.Windows.Media.Stretch.UniformToFill>、四角形を完全にいっぱいに拡大、ときに、イメージの縦横比を保持する必要があります。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 ![変換された出力](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 イメージがゆがんで、たとえに注意してください、ブラシの<xref:System.Windows.Media.TileBrush.Stretch%2A>に設定された<xref:System.Windows.Media.Stretch.UniformToFill>します。 相対変換がブラシの後に適用されるためです<xref:System.Windows.Media.TileBrush.Viewbox%2A>にマップされてその<xref:System.Windows.Media.TileBrush.Viewport%2A>します。 次の一覧では、処理の各ステップについて説明します。  
  
1. ブラシの内容をプロジェクト (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) 基本タイルに (<xref:System.Windows.Media.TileBrush.Viewport%2A>) ブラシを使用して<xref:System.Windows.Media.TileBrush.Stretch%2A>設定します。  
  
     ![Viewport に合わせて Viewbox を拡大する](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. 基本タイルを 1 x 1 の変換四角形に投影します。  
  
     ![Viewport を変換四角形にマップする](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. 適用、<xref:System.Windows.Media.RotateTransform>します。  
  
     ![相対変換を適用する](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. 変換された基本タイルを描画領域に投影します。  
  
     ![変換されたブラシを出力領域に投影する](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>例:ImageBrush の回転 45 度  
 次の例では、適用、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.Brush.RelativeTransform%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>します。 <xref:System.Windows.Media.RotateTransform>オブジェクトの<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティが両方とも設定である 0.5 に、コンテンツの中心の相対座標にポイントします。 その結果、ブラシの内容は中心の周りに回転されます。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 次の例でも適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.ImageBrush>が使用して、<xref:System.Windows.Media.Brush.Transform%2A>プロパティの代わりに、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティ。 ブラシを中央の周りを回転させる、<xref:System.Windows.Media.RotateTransform>オブジェクトの<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>絶対座標を設定する必要があります。 ブラシによって描画される四角形は 175 x 90 ピクセルなので、その中心点は (87.5, 45) です。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 次の図は、ブラシに適用される変換の変換をせず、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに適用される変換を使用して、<xref:System.Windows.Media.Brush.Transform%2A>プロパティ。  
  
 ![ブラシの RelativeTransform と Transform の設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 この例は、さらに大きなサンプルの一部です。 完全なサンプルについては、「[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)」をご覧ください。 ブラシについて詳しくは、「[WPF のブラシの概要](wpf-brushes-overview.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [変換の概要](transforms-overview.md)

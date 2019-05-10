---
title: 変換の概要
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: 7f5fad56d00e9a7e33843222a81593a90bf7e733
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651903"
---
# <a name="transforms-overview"></a>変換の概要
このトピックでは、使用する方法を説明します、 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform>クラスには、回転、拡大縮小、移動 (平行移動)、および傾斜させる<xref:System.Windows.FrameworkElement>オブジェクト。  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>変換とは  
 A<xref:System.Windows.Media.Transform>マップ、または、1 つの座標空間から別の座標空間へのポインターに変換する方法を定義します。 このマッピングは、変換によって記述<xref:System.Windows.Media.Matrix>、3 つの行の 3 つの列のコレクションである<xref:System.Double>値。  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) は、行優先の行列を使用します。 ベクターは、列ベクターではなく行ベクターとして表されます。  
  
 次の表は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 行列の構造を示したものです。  
  
### <a name="a-2-d-transformation-matrix"></a>2-D 変換行列  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 既定:1|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 既定:0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 既定:0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 既定:1|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 既定:0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 既定:0.0|1|  
  
 行列の値を操作することで、オブジェクトを回転、拡大縮小、傾斜、移動 (平行移動) させることができます。 たとえば、3 番目の行の最初の列の値を変更する場合 (、<xref:System.Windows.Media.Matrix.OffsetX%2A>値) を 100 を使用できます、オブジェクトの 100 単位 x 軸に沿って移動します。 2 番目の行の 2 列目の値を 3 に変更すると、オブジェクトの高さを現在の 3 倍に拡張できます。 両方の値を変更した場合は、オブジェクトが x 軸に沿って 100 単位移動し、高さが 3 倍に拡張されます。 Windows Presentation Foundation (WPF) は、アフィン変換のみをサポートするため、右側の列の値は常に 0, 0, 1。  
  
 Windows Presentation Foundation (WPF) では、行列の値を直接操作することができます、また、いくつか<xref:System.Windows.Media.Transform>基になる行列構造体を構成する方法を知らなくてもオブジェクトを変換するためのクラス。 たとえば、<xref:System.Windows.Media.ScaleTransform>クラスでは、オブジェクトを設定して拡大縮小できます。 その<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>変換行列を操作するのではなく、プロパティ。 同様に、<xref:System.Windows.Media.RotateTransform>クラスでは、設定するだけでオブジェクトを回転できます。 その<xref:System.Windows.Media.RotateTransform.Angle%2A>プロパティ。  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>変換クラス  
 Windows Presentation Foundation (WPF) は、次を提供します。 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform>一般的な変換操作用のクラス。  
  
|クラス|説明|例|図|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|指定した要素を回転させます<xref:System.Windows.Media.RotateTransform.Angle%2A>します。|[オブジェクトを回転させる](how-to-rotate-an-object.md)|![回転の図](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|指定した要素を拡大または縮小<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>金額。|[要素を拡大縮小する](how-to-scale-an-element.md)|![拡大縮小の図](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|指定した要素を傾斜<xref:System.Windows.Media.SkewTransform.AngleX%2A>と<xref:System.Windows.Media.SkewTransform.AngleY%2A>金額。|[要素を傾斜させる](how-to-skew-an-element.md)|![傾斜の図](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|移動 (平行移動)、指定した要素<xref:System.Windows.Media.TranslateTransform.X%2A>と<xref:System.Windows.Media.TranslateTransform.Y%2A>金額。|[要素を平行移動する](how-to-translate-an-element.md)|![平行移動の図](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 複雑な変換を作成するには、に対しては、Windows Presentation Foundation (WPF) は、次の 2 つのクラスを提供します。  
  
|クラス|説明|例|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|複数のグループ<xref:System.Windows.Media.TransformGroup>オブジェクト、1 つに<xref:System.Windows.Media.Transform>し変換プロパティに適用することができます。|[オブジェクトに複数の変換を適用する](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|その他は提供されないカスタム変換を作成します。<xref:System.Windows.Media.Transform>クラス。 使用すると、<xref:System.Windows.Media.MatrixTransform>マトリックスを直接操作することです。|[MatrixTransform を使用してカスタム変換を作成する](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) も用意されています。[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]変換します。 詳細については、<xref:System.Windows.Media.Media3D.Transform3D> クラスを参照してください。  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>一般的な変換プロパティ  
 オブジェクトを変換する方法の 1 つは、適切な宣言が<xref:System.Windows.Media.Transform>を入力し、オブジェクトの変換プロパティに適用します。 オブジェクトの型ごとに、異なる型の変換プロパティがあります。 次の表は、いくつかのよく使用される Windows Presentation Foundation (WPF) 型とその変換プロパティを示します。  
  
|型|変換プロパティ|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>変換と座標系  
 オブジェクトを変換する場合は、単にオブジェクトを変換するのではなく、そのオブジェクトが存在する座標空間を変換することになります。 既定では、変換は、ターゲット オブジェクトの座標系の原点を注視中央に配置します。(0,0). 唯一の例外は<xref:System.Windows.Media.TranslateTransform>。 つまり、 <xref:System.Windows.Media.TranslateTransform> center プロパティを、変換の結果が中央に配置場所に関係なく同じであるために設定がありません。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>を回転する、<xref:System.Windows.Shapes.Rectangle>要素、型の<xref:System.Windows.FrameworkElement>、45 度、既定の中心 (0, 0)。 次の図は、回転の結果を示したものです。  
  
 ![FrameworkElement は 45 度を回転&#40;0, 0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
ポイント (0, 0) を軸に 45 度回転した四角形要素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 既定では、要素は左上隅 (0, 0) を軸に回転します。 <xref:System.Windows.Media.RotateTransform>、 <xref:System.Windows.Media.ScaleTransform>、および<xref:System.Windows.Media.SkewTransform>クラスは、変換を適用するポイントを指定するための CenterX および CenterY プロパティを提供します。  
  
 また次の例では、<xref:System.Windows.Media.RotateTransform>を回転する、<xref:System.Windows.Shapes.Rectangle>要素を 45 度; ただし、この時間、<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティが設定ように、<xref:System.Windows.Media.RotateTransform>の中心が (25, 25)。 次の図は、回転の結果を示したものです。  
  
 ![回転した Geometry 45 度&#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
ポイント (25, 25) を軸に 45 度回転した四角形要素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>FrameworkElement の変換  
 変換を適用する、 <xref:System.Windows.FrameworkElement>、作成、<xref:System.Windows.Media.Transform>し、2 つのプロパティのいずれかに適用する、<xref:System.Windows.FrameworkElement>クラスを提供します。  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A> – レイアウト パスの前に適用される変換。 変換が適用されると、レイアウト システムは変換後のサイズと要素の位置を処理します。  
  
- <xref:System.Windows.UIElement.RenderTransform%2A> – 要素の外観を変更しますが、レイアウト パスが完了した後に適用する変換。 使用して、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティの代わりに、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>プロパティ、パフォーマンス上の利点を取得することができます。  
  
 どちらのプロパティを使用すればよいのでしょうか。 により、パフォーマンス上の利点が提供する、使用、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティを使用する場合は特に、可能なアニメーションを実行するたびに<xref:System.Windows.Media.Transform>オブジェクト。 使用して、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>拡大縮小、回転、または傾斜するプロパティとは、要素の親要素の変換後のサイズに合わせて調整する必要があります。 併用すると、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>プロパティ、<xref:System.Windows.Media.TranslateTransform>要素に効果がないオブジェクトが表示されます。 これは、レイアウト システムがその処理の一環として、変換後の要素を元の位置に返すためです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのレイアウトに関する追加情報については、[レイアウト](../advanced/layout.md)の概要をご覧ください。  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>例:FrameworkElement の回転 45 度  
 次の例では、<xref:System.Windows.Media.RotateTransform>をボタンを時計回りに 45 度回転させます。 ボタンが含まれている、<xref:System.Windows.Controls.StackPanel>を持つその他の 2 つのボタン。  
  
 既定で、<xref:System.Windows.Media.RotateTransform>点 (0, 0) の周りを回転します。 この例では中心の値を指定していないので、ボタンは左上隅のポイント (0, 0) を軸に回転します。 <xref:System.Windows.Media.RotateTransform>に適用される、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ。 次の図は、変換の結果を示したものです。  
  
 ![RenderTransform を使用して変換されたボタン](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
左上隅を軸とした、時計回り 45 度の回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 次の例を使用しても、<xref:System.Windows.Media.RotateTransform>もがボタンを時計回りに 45 度の回転を設定、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>するボタンの (0.5, 0.5)。 値、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティは、ボタンのサイズを基準とします。 その結果、回転は左上隅ではなく、ボタンの中心に適用されています。 次の図は、変換の結果を示したものです。  
  
 ![中心の周りに変換されたボタン](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
中心を軸とした、時計回り 45 度の回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 次の例では、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>プロパティの代わりに、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティをボタンを回転します。  そのため、変換がボタンのレイアウトに影響し、レイアウト システムによるフル パスがトリガーされています。 その結果、ボタンが回転された後、位置が変更されています。これは、サイズが変更されたためです。 次の図は、変換の結果を示したものです。  
  
 ![LayoutTransform を使用して変換されたボタン](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform を使用したボタンの回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>変換のアニメーション化  
 継承するため、<xref:System.Windows.Media.Animation.Animatable>クラス、<xref:System.Windows.Media.Transform>クラスをアニメーション化することができます。 アニメーション化する、 <xref:System.Windows.Media.Transform>、互換性のある型のアニメーションをアニメーション化するプロパティに適用します。  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard>と<xref:System.Windows.Media.Animation.DoubleAnimation>で、<xref:System.Windows.Media.RotateTransform>させる、<xref:System.Windows.Controls.Button>スピンがクリックされたときに有効です。  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 完全なサンプルについては、「[2-D 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。 アニメーション化について詳しくは、「[アニメーションの概要](animation-overview.md)」をご覧ください。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 機能  
 継承するため、<xref:System.Windows.Freezable>クラス、<xref:System.Windows.Media.Transform>クラスがいくつかの特別な機能を提供:<xref:System.Windows.Media.Transform>オブジェクトとして宣言できます[リソース](../advanced/xaml-resources.md)、向上させるために読み取り専用の複数のオブジェクト間で共有パフォーマンス、複製され、スレッド セーフです。 によって提供されるさまざまな機能の詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [方法トピック](transformations-how-to-topics.md)
- [2-D 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)

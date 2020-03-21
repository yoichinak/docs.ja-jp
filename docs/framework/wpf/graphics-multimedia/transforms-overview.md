---
title: 変換の概要
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2D transform
- transform classes [WPF], 2D
- 2D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: c5f29404a301eb023ff24b2890531dede6440ec4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111960"
---
# <a name="transforms-overview"></a>変換の概要
このトピックでは、2D<xref:System.Windows.Media.Transform>クラスを使用してオブジェクトを回転、拡大縮小、移動 (移動<xref:System.Windows.FrameworkElement>)、および傾斜する方法について説明します。  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>変換とは  
 A<xref:System.Windows.Media.Transform>は、ある座標空間から別の座標空間へのポイントをマップまたは変換する方法を定義します。 このマッピングは、3 つの<xref:System.Windows.Media.Matrix>列の<xref:System.Double>値を持つ 3 つの行のコレクションである変換によって記述されます。  
  
> [!NOTE]
> Windows プレゼンテーション ファウンデーション (WPF) では、行メジャー行列を使用します。 ベクターは、列ベクターではなく行ベクターとして表されます。  
  
 次の表は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 行列の構造を示したものです。  
  
### <a name="a-2d-transformation-matrix"></a>2D 変換行列  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 既定値: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 既定値: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 既定値: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 既定値: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 既定値: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 既定値: 0.0|1.0|  
  
 行列の値を操作することで、オブジェクトを回転、拡大縮小、傾斜、移動 (平行移動) させることができます。 たとえば、3 行目の最初の列 (値) の値を<xref:System.Windows.Media.Matrix.OffsetX%2A>100 に変更した場合、その値を使用して、X 軸に沿ってオブジェクトを 100 単位移動できます。 2 番目の行の 2 列目の値を 3 に変更すると、オブジェクトの高さを現在の 3 倍に拡張できます。 両方の値を変更した場合は、オブジェクトが x 軸に沿って 100 単位移動し、高さが 3 倍に拡張されます。 Windows プレゼンテーション ファンデーション (WPF) はアフィン変換のみをサポートするため、右側の列の値は常に 0、 0、1 です。  
  
 Windows プレゼンテーションファンデーション (WPF) では、マトリックス値を直接操作できますが<xref:System.Windows.Media.Transform>、基になるマトリックス構造の構成方法を知らなくてもオブジェクトを変換できるクラスもいくつか用意されています。 たとえば、<xref:System.Windows.Media.ScaleTransform>このクラスでは、変換行列を操作する代わりに、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>オブジェクト<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>とプロパティを設定してオブジェクトをスケーリングできます。 同様に、<xref:System.Windows.Media.RotateTransform>クラスでは、オブジェクトのプロパティを設定するだけでオブジェクトを<xref:System.Windows.Media.RotateTransform.Angle%2A>回転できます。  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>変換クラス  
 Windows プレゼンテーション ファンデーション (WPF)<xref:System.Windows.Media.Transform>では、一般的な変換操作に関する次の 2D クラスが用意されています。  
  
|クラス|説明|例|図|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|指定した<xref:System.Windows.Media.RotateTransform.Angle%2A>.|[オブジェクトを回転させる](how-to-rotate-an-object.md)|![図の回転](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|指定した<xref:System.Windows.Media.ScaleTransform.ScaleX%2A><xref:System.Windows.Media.ScaleTransform.ScaleY%2A>量で要素をスケールします。|[要素を拡大縮小する](how-to-scale-an-element.md)|![図のスケーリング](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|指定した<xref:System.Windows.Media.SkewTransform.AngleX%2A><xref:System.Windows.Media.SkewTransform.AngleY%2A>量で要素を傾斜します。|[要素を傾斜させる](how-to-skew-an-element.md)|![図の傾斜](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|指定された<xref:System.Windows.Media.TranslateTransform.X%2A><xref:System.Windows.Media.TranslateTransform.Y%2A>量で要素を移動 (変換) します。|[要素を平行移動する](how-to-translate-an-element.md)|![図の変換](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 より複雑な変換を作成するために、Windows プレゼンテーション ファンデーション (WPF) には、次の 2 つのクラスが用意されています。  
  
|クラス|説明|例|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|複数の<xref:System.Windows.Media.TransformGroup>オブジェクトを 1<xref:System.Windows.Media.Transform>つにグループ化し、プロパティを変換するために適用できます。|[オブジェクトに複数の変換を適用する](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|他<xref:System.Windows.Media.Transform>のクラスで提供されていないカスタム変換を作成します。 を使用する場合<xref:System.Windows.Media.MatrixTransform>、マトリックスを直接操作します。|[MatrixTransform を使用してカスタム変換を作成する](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows プレゼンテーション ファンデーション (WPF) では、3D 変換も提供されます。 詳細については、<xref:System.Windows.Media.Media3D.Transform3D> クラスを参照してください。  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>一般的な変換プロパティ  
 オブジェクトを変換する方法の 1 つは、<xref:System.Windows.Media.Transform>適切な型を宣言し、オブジェクトの変換プロパティに適用することです。 オブジェクトの型ごとに、異なる型の変換プロパティがあります。 次の表は、よく使用される Windows プレゼンテーション ファンデーション (WPF) 型とその変換プロパティの一覧です。  
  
|Type|変換プロパティ|  
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
 オブジェクトを変換する場合は、単にオブジェクトを変換するのではなく、そのオブジェクトが存在する座標空間を変換することになります。 既定では、ターゲット オブジェクトの座標系の原点が変換の中心になります: (0, 0)。 唯一の例外<xref:System.Windows.Media.TranslateTransform>は です。a<xref:System.Windows.Media.TranslateTransform>には、移動効果が中央に配置されている場所に関係なく同じであるため、設定する中心プロパティはありません。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>要素を<xref:System.Windows.Shapes.Rectangle>既定の<xref:System.Windows.FrameworkElement>中心 (0, 0) を中心に 45 度回転します。 次の図は、回転の結果を示したものです。  
  
 ![&#40;0,0&#41; を軸に 45 度回転した FrameworkElement](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
ポイント (0, 0) を軸に 45 度回転した四角形要素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 既定では、要素は左上隅 (0, 0) を軸に回転します。 クラス<xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ScaleTransform>、および<xref:System.Windows.Media.SkewTransform>クラスは、変換が適用される点を指定できる CenterX および CenterY プロパティを提供します。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>要素を<xref:System.Windows.Shapes.Rectangle>45 度回転する場合にも使用します。ただし、今回のプロパティ<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティは、中心が<xref:System.Windows.Media.RotateTransform>(25, 25) になるように設定されます。 次の図は、回転の結果を示したものです。  
  
 ![&#40;25, 25&#41; を軸に 45 度回転した Geometry](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
ポイント (25, 25) を軸に 45 度回転した四角形要素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>FrameworkElement の変換  
 変換を に適用するには<xref:System.Windows.FrameworkElement>、 を<xref:System.Windows.Media.Transform>作成し、クラスで提供される 2 つの<xref:System.Windows.FrameworkElement>プロパティのいずれかに変換を適用します。  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– レイアウトパスの前に適用される変換。 変換が適用されると、レイアウト システムは変換後のサイズと要素の位置を処理します。  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– 要素の外観を変更するが、レイアウト パスが完了した後に適用される変換。 プロパティの代<xref:System.Windows.UIElement.RenderTransform%2A>わりにプロパティを使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>すると、パフォーマンス上の利点を得ることができます。  
  
 どちらのプロパティを使用すればよいのでしょうか。 パフォーマンス上の利点があるため、アニメーション化<xref:System.Windows.UIElement.RenderTransform%2A><xref:System.Windows.Media.Transform>されたオブジェクトを使用する場合は、可能な限りこのプロパティを使用します。 このプロパティ<xref:System.Windows.FrameworkElement.LayoutTransform%2A>は、スケーリング、回転、または傾斜を行うときに使用し、要素の親を要素の変換サイズに合わせる必要があります。 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>プロパティと共に使用すると、<xref:System.Windows.Media.TranslateTransform>オブジェクトは要素に影響を与えないことに注意してください。 これは、レイアウト システムがその処理の一環として、変換後の要素を元の位置に返すためです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのレイアウトに関する追加情報については、[レイアウト](../advanced/layout.md)の概要をご覧ください。  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>例: FrameworkElement を 45 度回転させる  
 次の例では、<xref:System.Windows.Media.RotateTransform>を使用してボタンを時計回りに 45 度回転します。 ボタンは、他の<xref:System.Windows.Controls.StackPanel>2 つのボタンがある に含まれています。  
  
 デフォルトでは、点<xref:System.Windows.Media.RotateTransform>(0, 0)を中心に回転します。 この例では中心の値を指定していないので、ボタンは左上隅のポイント (0, 0) を軸に回転します。 <xref:System.Windows.Media.RotateTransform>はプロパティに適用されます<xref:System.Windows.UIElement.RenderTransform%2A>。 次の図は、変換の結果を示したものです。  
  
 ![RenderTransform を使用して変換されたボタン](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
左上隅を軸とした、時計回り 45 度の回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>を使用してボタンを時計回りに 45 度回転します<xref:System.Windows.UIElement.RenderTransformOrigin%2A>が、ボタンのを (0.5, 0.5) に設定します。 プロパティの<xref:System.Windows.UIElement.RenderTransformOrigin%2A>値は、ボタンのサイズに対する相対値です。 その結果、回転は左上隅ではなく、ボタンの中心に適用されています。 次の図は、変換の結果を示したものです。  
  
 ![中心を軸に変換されたボタン](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
中心を軸とした、時計回り 45 度の回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 次の例では、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>ボタンを回転するために<xref:System.Windows.UIElement.RenderTransform%2A>プロパティの代わりにプロパティを使用します。  そのため、変換がボタンのレイアウトに影響し、レイアウト システムによるフル パスがトリガーされています。 その結果、ボタンが回転された後、位置が変更されています。これは、サイズが変更されたためです。 次の図は、変換の結果を示したものです。  
  
 ![LayoutTransform を使用して変換されたボタン](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform を使用したボタンの回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>変換のアニメーション化  
 <xref:System.Windows.Media.Animation.Animatable>クラスから継承するため、クラスを<xref:System.Windows.Media.Transform>アニメーション化できます。 アニメーションを作成するには、<xref:System.Windows.Media.Transform>アニメーション化するプロパティに互換性のある型のアニメーションを適用します。  
  
 次の例では、 <xref:System.Windows.Media.Animation.Storyboard> a<xref:System.Windows.Media.Animation.DoubleAnimation>と<xref:System.Windows.Media.RotateTransform>a<xref:System.Windows.Controls.Button>を使用して、クリックされたときにスピンを所定の位置に置きます。  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 完全なサンプルについては[、2D 変換のサンプルを](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)参照してください。 アニメーション化について詳しくは、「[アニメーションの概要](animation-overview.md)」をご覧ください。  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable 機能  
 クラスから継承<xref:System.Windows.Media.Transform>されるため、このクラスには、[オブジェクトをリソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)として宣言したり、複数のオブジェクト間で共有したり、読み取り専用にしてパフォーマンスを向上させたり、クローンを作成したり、スレッドセーフにしたりできる、いくつかの特別な機能が用意されています。 <xref:System.Windows.Freezable> <xref:System.Windows.Media.Transform> オブジェクトによって<xref:System.Windows.Freezable>提供されるさまざまな機能の詳細については、 [[ フリーザブル オブジェクトの概要](../advanced/freezable-objects-overview.md)] を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [ハウツートピック](transformations-how-to-topics.md)
- [2D 変換のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)

---
title: パス アニメーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181868"
---
# <a name="path-animations-overview"></a>パス アニメーションの概要
<a name="introduction"></a>このトピックでは、ジオメトリック パスを使用して出力値を生成できるパス アニメーションの概要を説明します。 パス アニメーションは、複雑なパスに沿ってオブジェクトを移動および回転させるときに便利です。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、アニメーション機能について[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]理解している必要があります。 アニメーション機能の概要については、「 アニメーションの[概要](animation-overview.md)」を参照してください。  
  
 オブジェクトを<xref:System.Windows.Media.PathGeometry>使用してパス アニメーションを定義するため、さまざまな種類の<xref:System.Windows.Media.PathGeometry><xref:System.Windows.Media.PathSegment>オブジェクトについても理解しておく必要があります。 詳細については、「[ジオメトリの概要](geometry-overview.md)」を参照してください。  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>パス アニメーションとは  
 パス アニメーションは、入力として<xref:System.Windows.Media.Animation.AnimationTimeline>を<xref:System.Windows.Media.PathGeometry>使用する一種のアニメーションです。 From、To、By プロパティ (From/To/By アニメーションの場合と同様) を設定したり、キー フレームを使用したりするのではなく、ジオメトリック パスを定義し、それを使用してパス アニメーションの`PathGeometry`プロパティを設定します。 パス アニメーションが進むとき、パスから x、y、および角度情報を読み取り、その情報を使用して、出力を生成します。  
  
 パス アニメーションは、複雑なパスに沿ってオブジェクトをアニメーション化するのに便利です。 パスに沿ってオブジェクトを移動する方法の 1<xref:System.Windows.Media.MatrixTransform>つは、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>と を使用して複雑なパスに沿ってオブジェクトを変換することです。 オブジェクトを使用してこの手法を使用して、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>のプロパティをアニメーション化<xref:System.Windows.Media.MatrixTransform.Matrix%2A>する例を<xref:System.Windows.Media.MatrixTransform>次に示します。 <xref:System.Windows.Media.MatrixTransform>ボタンに適用され、曲線パスに沿って移動します。 プロパティが<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>に`true`設定されているため、四角形はパスの接線に沿って回転します。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]この例で使用されているパス構文の詳細については、「[パス マークアップ構文](path-markup-syntax.md)の概要」を参照してください。 完全なサンプルについては、「[パス アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)」を参照してください。  
  
 in<xref:System.Windows.Media.Animation.Storyboard>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]と code を使用するか、コード内でメソッドを使用して、プロパティに<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>パス アニメーションを適用できます。 パス アニメーションを使用して 作成し、1 つまたは複数の<xref:System.Windows.Media.Animation.AnimationClock>プロパティに適用することもできます。 アニメーションを適用するためのさまざまな方法の詳細については、「[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)」を参照してください。  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>パス アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 を受け取<xref:System.Double>るプロパティ ( の<xref:System.Windows.Media.TranslateTransform.X%2A>プロパティなど<xref:System.Windows.Media.TranslateTransform>) をアニメーション化するには、値を生成<xref:System.Double>するアニメーションを使用します。 を取るプロパティをアニメーション化するには<xref:System.Windows.Point>、値を生成<xref:System.Windows.Point>するアニメーションを使用します。  
  
 パス アニメーション クラスは<xref:System.Windows.Media.Animation>名前空間に属し、次の命名規則を使用します。  
  
 *\<タイプ>*`AnimationUsingPath`  
  
 [*\<タイプ>* は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次のパス アニメーション クラスが用意されています。  
  
|プロパティの種類|対応するパス アニメーション クラス|例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>は<xref:System.Windows.Media.Matrix>、 から<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>値を生成します。 と共に<xref:System.Windows.Media.MatrixTransform>使用すると、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>はパスに沿ってオブジェクトを移動できます。 のプロパティ<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>`true`を設定すると、パスの曲線に沿ってオブジェクトも回転します。  
  
 は<xref:System.Windows.Media.Animation.PointAnimationUsingPath>、<xref:System.Windows.Point>その X 座標と Y 座標から値<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>を生成します。 を<xref:System.Windows.Media.Animation.PointAnimationUsingPath>使用して値を取得<xref:System.Windows.Point>するプロパティをアニメーション化することで、パスに沿ってオブジェクトを移動できます。 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>はオブジェクトを回転できません。  
  
 A<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>は<xref:System.Double>、 から<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>値を生成します。 プロパティを<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>設定することにより、パスの x<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>座標、y 座標、または角度を出力として使用するかどうかを指定できます。 を<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>使用してオブジェクトを回転したり、X 軸または Y 軸に沿って移動することができます。  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>パス アニメーションの入力  
 各パス アニメーション クラス<xref:System.Windows.Media.PathGeometry>には、入力を指定するためのプロパティが用意されています。 パス アニメーションでは、<xref:System.Windows.Media.PathGeometry>を使用して出力値が生成されます。 この<xref:System.Windows.Media.PathGeometry>クラスでは、円弧、曲線、および線で構成される複数の複雑な図形を記述できます。  
  
 a の中心にある<xref:System.Windows.Media.PathGeometry>のはオブジェクトの<xref:System.Windows.Media.PathFigure>コレクションです。これらのオブジェクトは、各図が の不連続な図形を表<xref:System.Windows.Media.PathGeometry>すため、名前が付けられています。 各<xref:System.Windows.Media.PathFigure>オブジェクトは 1<xref:System.Windows.Media.PathSegment>つ以上のオブジェクトで構成され、各オブジェクトは図の 1 つのセグメントを表します。  
  
 多くの種類のセグメントがあります。  
  
|セグメントの種類|説明|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの点の間の楕円の円弧を作成します。|  
|<xref:System.Windows.Media.BezierSegment>|2 つの点の間の 3 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.LineSegment>|2 つの点を結ぶ直性を作成します。|  
|<xref:System.Windows.Media.PolyBezierSegment>|一連の 3 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.PolyLineSegment>|一続きの直線を作成します。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一連の 2 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|  
  
 a 内のセグメント<xref:System.Windows.Media.PathFigure>は、1 つのジオメトリック形状に結合され、次のセグメントの始点としてセグメントの終点が使用されます。 の<xref:System.Windows.Media.PathFigure.StartPoint%2A><xref:System.Windows.Media.PathFigure>プロパティは、最初のセグメントが描画されるポイントを指定します。 後続の各セグメントは、前のセグメントの終点から開始します。 たとえば、`10,50`から垂直な線を`10,150`定義するには、 プロパティを<xref:System.Windows.Media.PathFigure.StartPoint%2A>に`10,50`設定し、<xref:System.Windows.Media.LineSegment>プロパティ<xref:System.Windows.Media.LineSegment.Point%2A>の設定`10,150`を .  
  
 オブジェクトの<xref:System.Windows.Media.PathGeometry>詳細については、「[ジオメトリの概要](geometry-overview.md)」を参照してください。  
  
 では[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、特別な省略構文を使用して プロパティを<xref:System.Windows.Media.PathGeometry.Figures%2A>設定することもできます。 <xref:System.Windows.Media.PathGeometry> 詳細については、「パス[マークアップ構文の](path-markup-syntax.md)概要」を参照してください。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]この例で使用されているパス構文の詳細については、「[パス マークアップ構文](path-markup-syntax.md)の概要」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [パス アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [パス マークアップ構文](path-markup-syntax.md)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
- [アニメーションの概要](animation-overview.md)
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)

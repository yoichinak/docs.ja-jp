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
ms.openlocfilehash: 195af217ddf3a78a0ef1bb54957a65b6ce62deae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008216"
---
# <a name="path-animations-overview"></a>パス アニメーションの概要
<a name="introduction"></a>このトピックでは、ジオメトリック パスを使用して出力値を生成できるパス アニメーションの概要を説明します。 パス アニメーションは、複雑なパスに沿ってオブジェクトを移動および回転させるときに便利です。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するのには理解しておく[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーション機能。 アニメーションの機能の概要については、次を参照してください。、[アニメーションの概要](animation-overview.md)します。  
  
 使用するため、<xref:System.Windows.Media.PathGeometry>オブジェクトをパス アニメーションを定義する知識も必要<xref:System.Windows.Media.PathGeometry>とさまざまな種類の<xref:System.Windows.Media.PathSegment>オブジェクト。 詳細については、次を参照してください。、[ジオメトリの概要](geometry-overview.md)します。  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>パス アニメーションとは  
 パス アニメーションの種類は、<xref:System.Windows.Media.Animation.AnimationTimeline>を使用して、<xref:System.Windows.Media.PathGeometry>として入力します。 To、From を設定する代わりに、または By プロパティ (な From/に/By の場合とアニメーション) か、(キー フレーム アニメーションを使用すると)、キー フレームを使用して、ジオメトリック パスを定義し、設定を使用する、`PathGeometry`パス アニメーションのプロパティ。 パス アニメーションが進むとき、パスから x、y、および角度情報を読み取り、その情報を使用して、出力を生成します。  
  
 パス アニメーションは、複雑なパスに沿ってオブジェクトをアニメーション化するのに便利です。 使用して、パスに沿ってオブジェクトが移動する方法の 1 つ、<xref:System.Windows.Media.MatrixTransform>と<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>複雑なパスに沿ってオブジェクトを変換します。 次の例では、この手法を示しますを使用して、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティを<xref:System.Windows.Media.MatrixTransform>します。 <xref:System.Windows.Media.MatrixTransform>ボタンに適用され、曲線のパスに沿って移動します。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>プロパティに設定されて`true`パスの接線に沿って四角形が回転します。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 使用されるパスの構文の詳細については、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を参照してください、[パス マークアップ構文](path-markup-syntax.md)の概要。 サンプル全体については、次を参照してください。[パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)します。  
  
 パス アニメーションをプロパティに適用するにを使用して、<xref:System.Windows.Media.Animation.Storyboard>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とコード、またはを使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>コード内のメソッド。 作成するパス アニメーションを使用することもできます、<xref:System.Windows.Media.Animation.AnimationClock>を 1 つまたは複数のプロパティに適用します。 アニメーションを適用するためのさまざまな方法の詳細については、次を参照してください。[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)します。  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>パス アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 受け取るプロパティをアニメーション化する、 <xref:System.Double> (など、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティを<xref:System.Windows.Media.TranslateTransform>)、生成するアニメーションを使用する<xref:System.Double>値。 受け取るプロパティをアニメーション化する、<xref:System.Windows.Point>を生成するアニメーションを使用する<xref:System.Windows.Point>値、という具合です。  
  
 パス アニメーション クラスが属している、<xref:System.Windows.Media.Animation>名前空間と、次の名前付け規則。  
  
 *\<Type>* `AnimationUsingPath`  
  
 ここで、*\<Type>* は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次のパス アニメーション クラスが用意されています。  
  
|プロパティの型|対応するパス アニメーション クラス|例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>生成<xref:System.Windows.Media.Matrix>値からその<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>します。 使用すると、 <xref:System.Windows.Media.MatrixTransform>、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>パスに沿ってオブジェクトを移動できます。 設定した場合、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>のプロパティ、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>に`true`パスの曲線に沿ってオブジェクトが回転します。  
  
 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>生成<xref:System.Windows.Point>値から、x 座標と y 座標の<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>します。 使用して、<xref:System.Windows.Media.Animation.PointAnimationUsingPath>を受け取るプロパティをアニメーション化<xref:System.Windows.Point>値、パスに沿ってオブジェクトを移動することができます。 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>オブジェクトを回転させることはできません。  
  
 A<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>生成<xref:System.Double>値からその<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>します。 設定して、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>プロパティを指定できるかどうか、 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> x 座標、y 座標、またはパスの角度を出力として使用します。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>オブジェクトを回転させるか、x 軸または y 軸に沿って移動します。  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>パス アニメーションの入力  
 各パス アニメーション クラスが提供する<xref:System.Windows.Media.PathGeometry>をその入力を指定するプロパティ。 パス アニメーションを使用して、<xref:System.Windows.Media.PathGeometry>その出力値を生成します。 <xref:System.Windows.Media.PathGeometry>クラスでは、円弧、曲線、および行で構成される複数の複雑な図形を記述することができます。  
  
 中核を<xref:System.Windows.Media.PathGeometry>のコレクションは、<xref:System.Windows.Media.PathFigure>オブジェクト。 これらのオブジェクトは、各図形で個別の図形を記述する、<xref:System.Windows.Media.PathGeometry>します。 各<xref:System.Windows.Media.PathFigure>1 つまたは複数から成る<xref:System.Windows.Media.PathSegment>オブジェクト、それぞれの図形のセグメントをについて説明します。  
  
 多くの種類のセグメントがあります。  
  
|セグメントの種類|説明|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの点を結ぶ楕円の円弧を作成します。|  
|<xref:System.Windows.Media.BezierSegment>|2 つの点を結ぶ 3 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.LineSegment>|2 つの点を結ぶ直性を作成します。|  
|<xref:System.Windows.Media.PolyBezierSegment>|一続きの 3 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.PolyLineSegment>|一続きの直線を作成します。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一続きの 2 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|  
  
 内のセグメントを<xref:System.Windows.Media.PathFigure>に 1 つの幾何学図形を次のセグメントの開始点として、セグメントの終点を使用して結合されます。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>のプロパティを<xref:System.Windows.Media.PathFigure>最初のセグメントの描画元となるポイントを指定します。 後続の各セグメントは、前のセグメントの終点から始まります。 垂直線など`10,50`に`10,150`を設定して定義できます、<xref:System.Windows.Media.PathFigure.StartPoint%2A>プロパティを`10,50`を作成して、<xref:System.Windows.Media.LineSegment>で、<xref:System.Windows.Media.LineSegment.Point%2A>プロパティの設定`10,150`。  
  
 詳細については<xref:System.Windows.Media.PathGeometry>、オブジェクトを参照してください、[ジオメトリの概要](geometry-overview.md)します。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、設定する特別な省略構文を使用することもできます、<xref:System.Windows.Media.PathGeometry.Figures%2A>のプロパティを<xref:System.Windows.Media.PathGeometry>します。 詳細については、次を参照してください。[パス マークアップ構文](path-markup-syntax.md)の概要。  
  
 使用されるパスの構文の詳細については、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を参照してください、[パス マークアップ構文](path-markup-syntax.md)の概要。  
  
## <a name="see-also"></a>関連項目

- [パス アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160028)
- [パス マークアップ構文](path-markup-syntax.md)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
- [アニメーションの概要](animation-overview.md)
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)

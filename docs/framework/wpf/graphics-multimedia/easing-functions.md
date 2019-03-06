---
title: イージング関数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 456308e37bddc1df86b49085139a3810c4959a58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354506"
---
# <a name="easing-functions"></a>イージング関数
イージング関数を使うと、独自の数式をアニメーションに適用することができます。 たとえば、オブジェクトをリアルにバウンドさせたり、バネに乗っているように動作させたりすることができます。 キー フレーム アニメーションや From/To/By アニメーションを使ってこれらの効果を近似することもできますが、大量の作業が必要であり、アニメーションは数式を使うほど正確ではありません。  
  
 継承することによって、独自のカスタム イージング関数を作成するだけでなく<xref:System.Windows.Media.Animation.EasingFunctionBase>、ランタイムによって提供されるいくつかのイージング関数のいずれかを使用して、一般的な効果を作成することができます。  
  
-   <xref:System.Windows.Media.Animation.BackEase>:指定されたパスのアニメーションを開始する前に、少しアニメーションの動きは取り消します。  
  
-   <xref:System.Windows.Media.Animation.BounceEase>:バウンド効果を作成します。  
  
-   <xref:System.Windows.Media.Animation.CircleEase>:円関数を使って加速および減速するアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.CubicEase>:数式を使って加速および減速するアニメーションを作成します。 *f*(*t*) = *t*<sup>3</sup>します。  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>:スプリングが伸び縮みし静止するまでのようなアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>:指数の式を使って加速および減速するアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.PowerEase>:数式を使って加速および減速するアニメーションを作成します*f*(*t*) = *t*<sup>p</sup> p は、 <xref:System.Windows.Media.Animation.PowerEase.Power%2A>。プロパティ。  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>:数式を使って加速および減速するアニメーションを作成します。 *f*(*t*) = *t*<sup>2</sup>します。  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>:数式を使って加速および減速するアニメーションを作成します。 *f*(*t*) = *t*<sup>4</sup>します。  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>:数式を使って加速および減速するアニメーションを作成する*f*(*t*) = *t*<sup>5</sup>します。  
  
-   <xref:System.Windows.Media.Animation.SineEase>:正弦公式を使って加速および減速するアニメーションを作成します。  
  
 アニメーションにイージング関数を適用するには、使用、`EasingFunction`アニメーションのプロパティがアニメーションに適用するイージング関数を指定します。 次の例では、適用、<xref:System.Windows.Media.Animation.BounceEase>イージング関数を<xref:System.Windows.Media.Animation.DoubleAnimation>バウンド効果を作成します。  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 前の例では、イージング関数を From/To/By アニメーションに適用しました。 キー フレーム アニメーションにこれらのイージング関数を適用することもできます。 次の例では、キー フレームとそれらに関連付けられたイージング関数を使って、四角形が上方に縮まり、遅くなり、下方に延び (落下するように)、停止するアニメーションを作成します。  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 使用することができます、<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>イージング関数の動作方法は、変更するプロパティがアニメーションの補間方法を変更します。 3 つの値を与えることができますがある<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>:補間では、イージング関数に関連付けられた数式に従います。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>:イージング関数に関連付けられた数式の出力を引いた値 100% の補間を補間に依存します。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>:補間は<xref:System.Windows.Media.Animation.EasingMode.EaseIn>アニメーションの前半と<xref:System.Windows.Media.Animation.EasingMode.EaseOut>後半。  
  
 以下のグラフのさまざまな値を示す<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>場所*f*(*x*) アニメーションの進行状況を表すと*t*時間を表します。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode のグラフ。](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode のグラフ。](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode のグラフ。](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode のグラフ。](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![異なる EasingMode の ElasticEase のグラフ。](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![異なる EasingMode の ExponentialEase のグラフ。](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![異なる EasingMode の QuarticEase のグラフ。](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![異なる EasingMode の QuadraticEase のグラフ。](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![異なる EasingMode の QuarticEase のグラフ。](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![異なる EasingMode の QuinticEase のグラフ。](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![異なる EasingMode 値の SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  使用することができます<xref:System.Windows.Media.Animation.PowerEase>と同じ動作を作成する<xref:System.Windows.Media.Animation.CubicEase>、 <xref:System.Windows.Media.Animation.QuadraticEase>、 <xref:System.Windows.Media.Animation.QuarticEase>、および<xref:System.Windows.Media.Animation.QuinticEase>を使用して、<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティ。 たとえば、使用する<xref:System.Windows.Media.Animation.PowerEase>の代わりに<xref:System.Windows.Media.Animation.CubicEase>を指定、 <xref:System.Windows.Media.Animation.PowerEase.Power%2A> 3 の値。  
  
 継承することによって、独自のカスタム イージング関数を作成するだけでなく、実行時に含まれるイージング関数を使用して、<xref:System.Windows.Media.Animation.EasingFunctionBase>します。 次の例では、簡単なカスタム イージング関数を作成する方法を示します。 イージング関数の動作をオーバーライドすることで、独自の数値演算ロジックを追加することができます、<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>メソッド。   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

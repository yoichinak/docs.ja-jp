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
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965732"
---
# <a name="easing-functions"></a>イージング関数
イージング関数を使うと、独自の数式をアニメーションに適用することができます。 たとえば、オブジェクトをリアルにバウンドさせたり、バネに乗っているように動作させたりすることができます。 キー フレーム アニメーションや From/To/By アニメーションを使ってこれらの効果を近似することもできますが、大量の作業が必要であり、アニメーションは数式を使うほど正確ではありません。  
  
 から<xref:System.Windows.Media.Animation.EasingFunctionBase>継承することによって独自のカスタムイージング関数を作成するだけでなく、ランタイムによって提供されるいくつかのイージング関数の1つを使用して、一般的な効果を作成できます。  
  
- <xref:System.Windows.Media.Animation.BackEase> :指定されたパスでアニメーション化を開始する前に、アニメーションのモーションを少し取り消します。  
  
- <xref:System.Windows.Media.Animation.BounceEase>:バウンス効果を作成します。  
  
- <xref:System.Windows.Media.Animation.CircleEase> :循環関数を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.CubicEase> :数式*f*(*t*) = *t*<sup>3</sup>を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.ElasticEase>:残りの部分に戻るまで、スプリングの不安定さに似たアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.ExponentialEase> :指数式を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.PowerEase> :式*f*(*t*) = *t*<sup>p</sup> (p が<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティと等しい) を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>:数式*f*(*t*) = *t*<sup>2</sup>を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.QuarticEase>:数式*f*(*t*) = *t*<sup>4</sup>を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.QuinticEase>:数式*f*(*t*) = *t*<sup>5</sup>を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.SineEase>:サイン式を使用して加速または減速するアニメーションを作成します。  
  
 イージング関数をアニメーションに適用するには、アニメーション`EasingFunction`のプロパティを使用して、アニメーションに適用するイージング関数を指定します。 次の例では<xref:System.Windows.Media.Animation.BounceEase> 、にイージング関数<xref:System.Windows.Media.Animation.DoubleAnimation>を適用して、バウンス効果を作成します。  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 前の例では、イージング関数を From/To/By アニメーションに適用しました。 キー フレーム アニメーションにこれらのイージング関数を適用することもできます。 次の例では、キー フレームとそれらに関連付けられたイージング関数を使って、四角形が上方に縮まり、遅くなり、下方に延び (落下するように)、停止するアニメーションを作成します。  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>プロパティを使用して、イージング関数の動作方法を変更したり、アニメーションの補間方法を変更したりできます。 次の3つの値を<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>指定できます。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>:補間は、イージング関数に関連付けられている数式に従います。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>:補間は、イージング関数に関連付けられた数式の出力を差し引いた 100% 補間に従います。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>:補間<xref:System.Windows.Media.Animation.EasingMode.EaseIn>は、アニメーションの最初の半分と<xref:System.Windows.Media.Animation.EasingMode.EaseOut> 2 番目の半分に使用されます。  
  
 次<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>のグラフでは、 *f*(*x*) がアニメーションの進行状況を表し、 *t*が時間を表すという異なる値を示しています。  
  
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
> を使用<xref:System.Windows.Media.Animation.PowerEase>すると<xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuinticEase> 、プロパティを<xref:System.Windows.Media.Animation.PowerEase.Power%2A>使用して、、、およびと同じ動作を作成できます。 <xref:System.Windows.Media.Animation.QuarticEase> <xref:System.Windows.Media.Animation.CubicEase> たとえば、を使用しての<xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.CubicEase>代わりにを使用する場合は<xref:System.Windows.Media.Animation.PowerEase.Power%2A> 、値を3に指定します。  
  
 ランタイムに含まれるイージング関数を使用するだけでなく、から継承することで、独自の<xref:System.Windows.Media.Animation.EasingFunctionBase>カスタムイージング関数を作成することもできます。 次の例では、簡単なカスタム イージング関数を作成する方法を示します。 <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>メソッドをオーバーライドすることにより、イージング関数の動作について独自の数学的ロジックを追加できます。   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

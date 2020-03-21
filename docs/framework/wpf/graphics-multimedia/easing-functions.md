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
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186500"
---
# <a name="easing-functions"></a>イージング関数
イージング関数を使うと、独自の数式をアニメーションに適用することができます。 たとえば、オブジェクトをリアルにバウンドさせたり、バネに乗っているように動作させたりすることができます。 キー フレーム アニメーションや From/To/By アニメーションを使ってこれらの効果を近似することもできますが、大量の作業が必要であり、アニメーションは数式を使うほど正確ではありません。  
  
 継承<xref:System.Windows.Media.Animation.EasingFunctionBase>によって独自のカスタム イージング関数を作成する以外に、ランタイムによって提供される複数のイージング関数のいずれかを使用して、共通の効果を作成できます。  
  
- <xref:System.Windows.Media.Animation.BackEase>: アニメーションの動きを少し後退してから、指定されたパスでアニメーションを開始します。  
  
- <xref:System.Windows.Media.Animation.BounceEase>: バウンス効果を作成します。  
  
- <xref:System.Windows.Media.Animation.CircleEase>: 円形関数を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.CubicEase>: *f*(*t*) = *t*<sup>3</sup>を使用して加速および減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: 休むまで前後に振動するばねのようなアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: 指数式を使用して加速または減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.PowerEase>: p がプロパティに等しい場合に式*f*(*t*) = *t*<sup>p</sup>を使用して<xref:System.Windows.Media.Animation.PowerEase.Power%2A>加速および減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: *f*(*t*) = *t*<sup>2</sup>を使用して加速および減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: *f*(*t*) = *t*<sup>4</sup>を使用して加速および減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: *f*(*t*) = *t*<sup>5</sup>を使用して加速および減速するアニメーションを作成します。  
  
- <xref:System.Windows.Media.Animation.SineEase>: sine 式を使用して加速または減速するアニメーションを作成します。  
  
 アニメーションにイージング関数を適用するには、アニメーションの`EasingFunction`プロパティを使用して、アニメーションに適用するイージング関数を指定します。 次の例では、<xref:System.Windows.Media.Animation.BounceEase>イージング関数を<xref:System.Windows.Media.Animation.DoubleAnimation>に適用して、バウンス効果を作成します。  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 前の例では、イージング関数を From/To/By アニメーションに適用しました。 キー フレーム アニメーションにこれらのイージング関数を適用することもできます。 次の例では、キー フレームとそれらに関連付けられたイージング関数を使って、四角形が上方に縮まり、遅くなり、下方に延び (落下するように)、停止するアニメーションを作成します。  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 このプロパティを<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>使用して、イージング関数の動作を変更したり、アニメーションの補間方法を変更したりすることができます。 次の 3 つの値を指定<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>できます。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: 補間はイージング関数に関連付けられた数式に従います。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: 補間は、100% の補間からイージング関数に関連付けられた数式の出力を引いた値です。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: 補間は<xref:System.Windows.Media.Animation.EasingMode.EaseIn>、アニメーションの前半と<xref:System.Windows.Media.Animation.EasingMode.EaseOut>後半に使用されます。  
  
 以下のグラフは *、f*( <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> *x*) がアニメーションの進行状況を表し *、t*が時間を表す場所の値を示しています。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode のグラフ。](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode のグラフ](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode のグラフ](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode のグラフ](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![異なる EasingMode の ElasticEase のグラフ](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![異なる EasingMode の ExponentialEase のグラフ。](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![異なる EasingMode の QuarticEase のグラフ](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![異なるイージングモードのグラフで二次的な動作](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![異なる EasingMode の QuarticEase のグラフ](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![異なる EasingMode の QuinticEase のグラフ](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![異なる EasingMode 値の SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> プロパティを使用<xref:System.Windows.Media.Animation.PowerEase>して<xref:System.Windows.Media.Animation.CubicEase>、 、 <xref:System.Windows.Media.Animation.QuadraticEase>、および<xref:System.Windows.Media.Animation.QuarticEase>と<xref:System.Windows.Media.Animation.QuinticEase>同じ動作を<xref:System.Windows.Media.Animation.PowerEase.Power%2A>作成できます。 たとえば、<xref:System.Windows.Media.Animation.PowerEase><xref:System.Windows.Media.Animation.CubicEase>を使用して を置換する場合は、値<xref:System.Windows.Media.Animation.PowerEase.Power%2A>3 を指定します。  
  
 ランタイムに含まれるイージング関数を使用するだけでなく、 から<xref:System.Windows.Media.Animation.EasingFunctionBase>継承して独自のカスタム イージング関数を作成することもできます。 次の例では、簡単なカスタム イージング関数を作成する方法を示します。 メソッドをオーバーライドすることで、イージング関数の動作に関する独自の数学ロジックを<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>追加できます。
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

---
title: キー フレーム アニメーションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: 8eb590b07eae3b76b3a206b9731997a6bc2c90d7
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344900"
---
# <a name="key-frame-animations-overview"></a>キー フレーム アニメーションの概要
このトピックでは、キー フレーム アニメーションの概要を説明します。 キー フレーム アニメーションでは、3 つ以上のターゲット値を使用してアニメーション化することができ、アニメーションの補間方式を制御できます。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>前提条件  
 この概要を理解するのには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アニメーションとタイムラインを理解しておく必要があります。 アニメーションの概要については、「[アニメーションの概要](animation-overview.md)」を参照してください。 さらに、From/To/By アニメーションについて理解しておくと役に立ちます。 詳細については、「From/To/By アニメーションの概要」を参照してください。  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>キー フレーム アニメーションとは  
 From/To/By アニメーションと同じように、キー フレーム アニメーションも、ターゲット プロパティの値をアニメーション化します。 ターゲット値の間に遷移を作成<xref:System.Windows.Media.Animation.Timeline.Duration%2A>します。 ただし、From/To/By アニメーションは 2 つの値の間の遷移を作成しますが、キー フレーム アニメーションは、任意の数のターゲット値の間の遷移を作成できます。 From/To/By アニメーションとは異なり、キー フレーム アニメーションには、ターゲット値を設定する From、To、または By プロパティはありません。 キー フレーム アニメーションのターゲット値は、キー フレーム オブジェクトを使用して記述されます (このため、"キー フレーム アニメーション" という用語が使用されます)。 アニメーションのターゲット値を指定するには、キーフレーム オブジェクトを作成し、アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>コレクションに追加します。 アニメーションを実行すると、アニメーションが指定したフレームの間で遷移します。  
  
 複数のターゲット値のサポートに加え、一部のキー フレーム メソッドでは、複数の補間方式もサポートします。 アニメーションの補間方式は、1 つの値から次の値にどのように遷移するかを定義します。 補間には、離散、線形、およびスプラインの 3 つの種類があります。  
  
 キー フレーム アニメーションをアニメーション化するには、次の手順を完了します。  
  
- アニメーションを宣言し、アニメーション<xref:System.Windows.Media.Animation.Timeline.Duration%2A>の From/to/by アニメーションの場合と同様に、アニメーションを指定します。  
  
- 各ターゲット値に対して、適切な型のキー フレームを作成し、<xref:System.Windows.Media.Animation.KeyTime>その値を設定して、アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>コレクションに追加します。  
  
- From/To/By アニメーションと同じように、アニメーションをプロパティに関連付けます。 ストーリーボードを使用したアニメーションのプロパティへの適用の詳細については、「[ストーリー ボードの概要](storyboards-overview.md)」を参照してください。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を使用して要素<xref:System.Windows.Shapes.Rectangle>を 4 つの異なる位置にアニメーション化します。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 From/To/By アニメーションと同様に、キー フレーム アニメーションは、マークアップおよびコード内の<xref:System.Windows.Media.Animation.Storyboard>を使用するか、コード内で<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してプロパティに適用できます。 また、キーフレーム アニメーションを使用して 作成し、1 つまたは複数の<xref:System.Windows.Media.Animation.AnimationClock>プロパティに適用することもできます。 アニメーションを適用するためのさまざまなメソッドの詳細については、「[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)」を参照してください。  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>キー フレーム アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 を受け取るプロパティ<xref:System.Double>(要素の<xref:System.Windows.FrameworkElement.Width%2A>プロパティなど) をアニメーション化するには、値を生成<xref:System.Double>するアニメーションを使用します。 を取るプロパティをアニメーション化するには<xref:System.Windows.Point>、値を生成<xref:System.Windows.Point>するアニメーションを使用します。  
  
 キー フレーム アニメーション クラスは<xref:System.Windows.Media.Animation>名前空間に属し、次の命名規則に従います。  
  
 *\<タイプ>*`AnimationUsingKeyFrames`  
  
 [*\<タイプ>* は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、次のキー フレーム アニメーション クラスを提供します。  
  
|プロパティの種類|対応するFrom/To/By アニメーションのクラス|サポートされる補間方式|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|離散、線形、スプライン|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>ターゲット値 (キー フレーム) とキー時刻  
 さまざまな種類のプロパティをアニメーション化するための多様な種類のキー フレーム アニメーションがあるように、さまざまな種類のキー フレーム オブジェクトがあります (アニメーション化される値の型とサポートされる補間方式ごとに 1 種類のオブジェクト)。 キー フレームの種類は、次の名前付け規則に従います。  
  
 *補間メソッド>\<型>\<*`KeyFrame`  
  
 補*\<間メソッド>* は、キー フレームが使用する補間メソッドであり、*\<型>* はクラスがアニメーション化する値の型です。 3 つの補間方式のすべてをサポートするキー フレーム アニメーションでは、3 種類のキー フレームを使用できます。 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>たとえば、 、 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>、 、および<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame><xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>を持つ 3 つのキー フレーム型を使用できます。 (補間方式については、後のセクションで詳しく説明します)。  
  
 キー フレームの主な目的は、 および<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A><xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>を指定することです。 すべての種類のキー フレームには、次の 2 つのプロパティがあります。  
  
- プロパティ<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>は、そのキー フレームのターゲット値を指定します。  
  
- プロパティ<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>は、(アニメーション内<xref:System.Windows.Media.Animation.Timeline.Duration%2A>で)キー フレーム<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>に達するタイミングを指定します。  
  
 キー フレーム アニメーションが開始されると、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>そのキー フレームをプロパティで定義された順序で反復処理します。  
  
- タイム 0 にキー フレームがない場合、アニメーションはターゲット プロパティの現在の値と最初のキー<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>フレームの間の遷移を作成します。それ以外の場合、アニメーションの出力値は最初のキー フレームの値になります。  
  
- アニメーションは、2 番目<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>のキー フレームで指定された補間方法を使用して、最初のキー フレームと 2 番目のキー フレームの間に遷移を作成します。 切り替えは最初のキー フレームから<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>開始し、2 番目のキー<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>フレームに達すると終了します。  
  
- アニメーションは、前後のキー フレームの間の遷移を作成しながら続行されます。  
  
- 最後に、アニメーションはキー フレームの値に遷移し、キー時間がアニメーションの値と同じかそれより小さい<xref:System.Windows.Media.Animation.Timeline.Duration%2A>かのキータイムを持ちます。  
  
 アニメーションのが<xref:System.Windows.Media.Animation.Timeline.Duration%2A><xref:System.Windows.Duration.Automatic%2A>、最後<xref:System.Windows.Media.Animation.Timeline.Duration%2A>のキー フレームの時間と等しい場合、アニメーションは終了します。 それ以外の場合、アニメーションが<xref:System.Windows.Duration>最後のキー フレームのキータイムよりも大きい場合、アニメーションはキー フレームの値を<xref:System.Windows.Duration>保持し、そのキー フレームの最後に達するまで保持します。 すべてのアニメーションと同様に、キー フレーム アニメーションは<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>、そのプロパティを使用して、アクティブな期間の終わりに達したときに最終的な値を保持するかどうかを判断します。 詳細については、「[タイミング動作の概要](timing-behaviors-overview.md)」を参照してください。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>前の例で定義したオブジェクトを使用して、 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティと プロパティの動作を示します。  
  
- 最初のキー フレームは、アニメーションの出力値をただちに 0 に設定します。  
  
- 2 番目のキー フレームは、0 から 350 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 0 秒)、2 秒間再生され、時刻 = 0:0:2 で終わります。  
  
- 3 番目のキー フレームは、350 から 50 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 2 秒)、5 秒間再生され、時刻 = 0:0:7 で終わります。  
  
- 4 番目のキー フレームは、50 から 200 までアニメーション化されます。 3 番目のキー フレームが終わった時点で開始され (時刻 = 7 秒)、1 秒間再生され、時刻 = 0:0:8 で終わります。  
  
- アニメーションの<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティが 10 秒に設定されているため、アニメーションは、2 秒間、最後の値を保持し、その後、時間 = 0:0:10 で終了します。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>補間方式  
 前のセクションで、一部のキー フレーム アニメーションでは複数の補間方式がサポートされることに言及しました。 アニメーションの補間は、その継続時間中にアニメーションがどのように遷移するかを表します。 アニメーションで使用するキー フレームの種類を選択することで、そのキー フレーム セグメントの補間方式を定義できます。 補間方式には、線形、離散、およびスプラインの 3 つの種類があります。  
  
### <a name="linear-interpolation"></a>線形補間  
 線形補間では、アニメーションは、セグメントの継続期間中、一定の率で進行します。 たとえば、キー フレーム セグメントが 5 秒間で 0 から 10 に遷移する場合、アニメーションは、指定された時間に次の値を出力します。  
  
|Time|出力値|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>離散補間  
 離散補間では、アニメーション関数は、1 つの値から次の値に補間なしでジャンプします。 キー フレーム セグメントが 5 秒間で 0 から 10 に遷移する場合、アニメーションは、指定された時間で次の値を出力します。  
  
|Time|出力値|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 アニメーションの出力値は、セグメント期間の最後の最後に達するまで変化しないことに注意してください。  
  
 スプライン補間はさらに複雑です。 次のセクションで説明します。  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>スプライン補間  
 スプライン補間を使用して、リアルなタイミング効果を実現できます。 アニメーションは現実世界で起こる効果を模倣するために使用されることが多いため、開発者は、オブジェクトの加速と減速を細かく制御し、タイミング セグメントを緻密に操作することが必要になる場合があります。 スプライン キーフレームでは、スプライン補間を使用してアニメーション化できます。 その他のキー フレームでは、 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>および を指定します。 スプライン キー フレームでは、 も指定<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>します。 次の例は、 の単一のスプライン<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>キー フレームを示しています。 プロパティに<xref:System.Windows.Media.Animation.KeySpline>注意してください。スプライン キー フレームが他のタイプのキー フレームと異なるのは、この方法です。  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 3 次ベジエ曲線は、開始点、終点、および 2 つの制御点によって定義されます。 スプ<xref:System.Windows.Media.Animation.KeySpline>ライン キー フレームのプロパティは、(0,0) から (1,1) に伸びるベジェ曲線の 2 つのコントロール ポイントを定義します。 最初の制御点は、ベジエ曲線の前半分の曲率を制御し、2 つ目の制御点は、後半分の曲率を制御します。 結果として得られる曲線は、そのスプライン キー フレームの変化率を表します。 曲線が急であればあるほど、キー フレームの値は急激に変化します。 曲線が平坦になると、キー フレームの値は緩やかに変化します。  
  
 落下水や<xref:System.Windows.Media.Animation.KeySpline>バウンドボールなどの物理的な軌道をシミュレートしたり、他の「イーズイン」エフェクトや「イーズアウト」エフェクトをモーションアニメーションに適用したりするために使用できます。 背景のフェードやコントロール ボタンの復帰などのユーザー操作効果では、スプライン補間を適用して、アニメーションの変化率を特定の方法で加速したり減速したりできます。  
  
 次<xref:System.Windows.Media.Animation.KeySpline>の例では、0,1 1,0 を指定し、次のベジェ曲線を作成します。  
  
 ![ベジエ曲線](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
制御点が (0.0, 1.0) および (1.0, 0.0) のキー スプライン  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 このキー フレームは、開始されると速いスピードでアニメーション化され、その後スピードが低下し、終了前に再びスピードが上がります。  
  
 次<xref:System.Windows.Media.Animation.KeySpline>の例では、0.5,0.25 0.75,1.0 を指定し、次のベジェ曲線を作成します。  
  
 ![ベジエ曲線](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
制御点が (0.25, 0.5) および (0.75, 1.0) のキー スプライン  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 ベジエ曲線の曲率がほとんど変化しないため、このキー フレームは、ほぼ一定の率でアニメーション化され、最後の最後にわずかに減速します。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を使用して四角形の位置をアニメーション化します。 オブジェクトを<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>使用<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>するため、各キーフレーム値間の遷移ではスプライン補間が使用されます。  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 スプライン補間は理解するのが難しいことがあります。さまざまな設定で実験すると理解しやすくなります。 [キー スプライン アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)を使用して、キー スプライン値を変更し、その結果をアニメーションで確認することができます。  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>補間方式の組み合わせ  
 補間の種類が異なるキー フレームを 1 つのキー フレーム アニメーションで使用できます。 補間の種類が異なる 2 つのキー フレーム アニメーションが連続する場合は、2 番目のキー フレームの補間方式を使用して、最初の値から 2 番目の値への遷移が作成されます。  
  
 次の例では、線形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>、スプライン、および不連続の補間を使用する a が作成されます。  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>継続時間とキー時刻の詳細  
 他のアニメーションと同様に、キー フレーム アニメーション<xref:System.Windows.Duration>にもプロパティがあります。 アニメーションの<xref:System.Windows.Duration>を指定する以外に、各キーフレームに対してその継続時間のどの部分を指定するかを指定する必要があります。 アニメーションの各キー フレームについて<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>を記述します。 各キー フレームは<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>、そのキー フレームがいつ終了するかを指定します。  
  
 この<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティでは、キーの再生時間を指定しません。 キー フレームが再生される時間の長さは、そのキー フレームの終了時刻、前のキー フレームの終了時刻、およびアニメーションの継続時間によって決まります。 キー時刻は、時間値、パーセント値、または特殊値<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>で指定できます。  
  
 次の一覧で、キー時刻を指定するさまざまな方法について説明します。  
  
### <a name="timespan-values"></a>TimeSpan 値  
 値を使用<xref:System.TimeSpan>して を指定<xref:System.Windows.Media.Animation.KeyTime>することができます。 値は、0 以上、アニメーションの継続時間以下にする必要があります。 次の例は、継続時間が 10 秒で、キー時刻が時刻値として指定されている 4 つのキー フレームがあるアニメーションを示しています。  
  
- 最初のキー フレームは、最初の 3 秒間で基準値から 100 までアニメーション化され、時刻 = 0:0:03 で終わります。  
  
- 2 番目のキー フレームは、100 から 200 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 3 秒)、5 秒間再生され、時刻 = 0:0:8 で終わります。  
  
- 3 番目のキー フレームは、200 から 500 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 8 秒)、1 秒間再生され、時刻 = 0:0:9 で終わります。  
  
- 4 番目のキー フレームは、500 から 600 までアニメーション化されます。 3 番目のキー フレームが終わった時点で開始され (時刻 = 9 秒)、1 秒間再生され、時刻 = 0:0:10 で終わります。  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>パーセント値  
 パーセンテージ値は、キー フレームがアニメーションの一定の割合で終了することを<xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、後ろに `%` 記号が付いた数値として指定します。 コードでは、メソッドを<xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A>使用し、パーセンテージを示<xref:System.Double>す a を渡します。 値は、0 以上、100 パーセント以下にする必要があります。 次の例は、継続時間が 10 秒で、キー時刻がパーセントとして指定されている 4 つのキー フレームがあるアニメーションを示しています。  
  
- 最初のキー フレームは、最初の 3 秒間で基準値から 100 までアニメーション化され、時刻 = 0:0:3 で終わります。  
  
- 2 番目のキー フレームは、100 から 200 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 3 秒)、5 秒間再生され、時刻 = 0:0:8 (0.8 * 10 = 8) で終わります。  
  
- 3 番目のキー フレームは、200 から 500 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 8 秒)、1 秒間再生され、時刻 = 0:0:9 (0.9 * 10 = 9) で終わります。  
  
- 4 番目のキー フレームは、500 から 600 までアニメーション化されます。 3 番目のキー フレームが終わった時点で開始され (時刻 = 9 秒)、1 秒間再生され、時刻 = 0:0:10 (1 * 10 = 10)で終わります。  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>特殊な値 Uniform  
 各<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>キー フレームに同じ時間を割く場合は、タイミングを使用します。  
  
 キー<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>タイムは、使用可能な時間をキー フレーム数で均等に割って、各キー フレームの終了時刻を決定します。 次の例は、10 秒の期間を持つアニメーションと、キータイムが として指定<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>された 4 つのキー フレームを示しています。  
  
- 最初のキー フレームは、最初の 2.5 秒間で基準値から 100 までアニメーション化され、時刻 = 0:0:2.5 で終わります。  
  
- 2 番目のキー フレームは、100 から 200 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 0:0:2.5 秒)、2.5 秒間再生され、時刻 = 0:0:5 で終わります。  
  
- 3 番目のキー フレームは、200 から 500 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 5 秒)、2.5 秒間再生され、時刻 = 0:0:7.5 で終わります。  
  
- 4 番目のキー フレームは、500 から 600 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 7.5 秒)、2.5 秒間再生され、時刻 = 0:0:10 で終わります。  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>特殊な値 Paced  
 一<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>定の速度でアニメーションを作成するタイミングを使用します。  
  
 キー<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>時間は、各フレームの長さに応じて使用可能な時間を割り当て、各フレームの継続時間を決定します。  これにより、アニメーションの速さ (ペース) を一定に保つ動作が提供されます。  次の例は、10 秒の期間と、キータイムが として指定された 3<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>つのキー フレームを持つアニメーションを示しています。  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 最後のキー フレームのキー時刻が または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>の場合、解決されたキー時間は 100% に設定されます。 マルチ フレーム アニメーションの最初のキー フレームが Paced の場合、解決されたキー時刻は 0 に設定されます  (キー フレーム コレクションにキー フレームが 1 つだけ含まれているときに、それが Paced が設定されたキー フレームの場合は、解決されたキー時刻は 100% に設定されます)。  
  
 1 つのキー フレーム アニメーション内の異なるキー フレームで異なるキー時刻を使用できます。  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>キー時刻と順不同のキー フレームの組み合わせ  
 同じアニメーションで、異なる<xref:System.Windows.Media.Animation.KeyTime>値型のキー フレームを使用できます。 さらに、キー フレームは再生する順序で追加することをお勧めしますが、それは必須ではありません。 アニメーションとタイミング システムは、順不同のキー フレームを解決できます。 キー時刻が無効なキー フレームは無視されます。  
  
 キー フレーム アニメーションのキー フレームのキー時刻が解決される手順を次に示します。  
  
1. 値<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>を解決します。  
  
2. アニメーションの*合計補間時間*を決定します。これは、キー フレーム アニメーションが順方向の反復を完了するまでにかかる合計時間です。  
  
    1. アニメーション<xref:System.Windows.Media.Animation.Timeline.Duration%2A>が<xref:System.Windows.Duration.Automatic%2A><xref:System.Windows.Duration.Forever%2A>または でない場合、合計補間時間はアニメーションのプロパティの値になります<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
    2. それ以外の場合、合計補間時間は、<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>キー フレームの中で指定される最大値になります (存在する場合)。  
  
    3. それ以外の場合、合計補間時間は 1 秒間です。  
  
3. 値を解決<xref:System.Windows.Media.Animation.KeyTimeType.Percent><xref:System.Windows.Media.Animation.KeyTime>するには、合計補間時間の値を使用します。  
  
4. 前の手順で解決されていなければ、最後のキー フレームを解決します。 最後の<xref:System.Windows.Media.Animation.KeyTime>キー フレームの が<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime.Paced%2A>または の場合、その解決時間は合計補間時間と等しくなります。  
  
     最初の<xref:System.Windows.Media.Animation.KeyTime>キー フレームの が<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>、このアニメーションのキー フレームの数が 0<xref:System.Windows.Media.Animation.KeyTime>以上である場合は、その値を 0 に解決します。キー フレームが 1 つだけで<xref:System.Windows.Media.Animation.KeyTime>、その<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>値が の場合は、前の手順で説明したように、合計補間時間に解決されます。  
  
5. 残りの<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>値を解決する: それぞれの値に、使用可能な時間の等しい分けが与えられます。  このプロセスの間、未解決<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>の値は一時的に<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>値として扱われ、一時的に解決された時間を取得します。  
  
6. 解決された<xref:System.Windows.Media.Animation.KeyTime>値を持つ最も近いキー フレームを使用して、キー フレームの値<xref:System.Windows.Media.Animation.KeyTime>を指定されていないキー時間で解決します。  
  
7. 残りの<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>値を解決します。 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>隣接キー<xref:System.Windows.Media.Animation.KeyTime>フレームの値を使用して、解決された時間を決定します。  目標は、アニメーションの速度がこのキー フレームの解決時間近くで一定であることを保証することです。  
  
8. キー フレームを解決された時間 (主キー) の順に並べ替え、宣言の順序 (2 番目のキー) 、つまり、<xref:System.Windows.Media.Animation.KeyTime>解決されたキー フレーム値に基づいて安定した並べ替えを使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [キー スプライン アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [キー フレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
- [タイミング動作の概要](timing-behaviors-overview.md)

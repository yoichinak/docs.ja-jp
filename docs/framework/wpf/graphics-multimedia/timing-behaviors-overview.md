---
title: タイミング動作の概要
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145398"
---
# <a name="timing-behaviors-overview"></a>タイミング動作の概要
このトピックでは、アニメーションおよびその他<xref:System.Windows.Media.Animation.Timeline>のオブジェクトのタイミング動作について説明します。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、基本的なアニメーション機能に精通している必要があります。 詳細については、「 アニメーションの[概要](animation-overview.md)」を参照してください。  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>タイムラインの型  
 A<xref:System.Windows.Media.Animation.Timeline>は時間のセグメントを表します。 用意されているプロパティを使用して、そのセグメントの長さ、開始時間、繰り返し回数、時間の進行の速度などを指定できます。  
  
 Timeline クラスを継承するクラスには、アニメーションやメディアの再生などの追加機能が用意されています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、次<xref:System.Windows.Media.Animation.Timeline>の型が用意されています。  
  
|タイムラインの型|説明|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|プロパティのアニメーション化<xref:System.Windows.Media.Animation.Timeline>の出力値を生成するオブジェクトの抽象基本クラス。|  
|<xref:System.Windows.Media.MediaTimeline>|メディア ファイルから出力を生成します。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|子<xref:System.Windows.Media.Animation.Timeline>オブジェクトを<xref:System.Windows.Media.Animation.TimelineGroup>グループ化および制御する型。|  
|<xref:System.Windows.Media.Animation.Storyboard>|含まれている<xref:System.Windows.Media.Animation.ParallelTimeline>Timeline オブジェクトのターゲット情報を提供するタイプのタイプ。|  
|<xref:System.Windows.Media.Animation.Timeline>|タイミング動作を定義する抽象基本クラス。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|他<xref:System.Windows.Media.Animation.Timeline>のオブジェクト<xref:System.Windows.Media.Animation.Timeline>を含むことができるオブジェクトの抽象クラス。|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>タイムラインの長さを制御するプロパティ  
 A<xref:System.Windows.Media.Animation.Timeline>は時間のセグメントを表し、タイムラインの長さはさまざまな方法で表現できます。 タイムラインの長さを示すいくつかの用語の定義を次の表に示します。  
  
|期間|説明|Properties||||  
|----------|-----------------|----------------|-|-|-|  
|単純継続時間|タイムラインが順方向の反復を 1 回完了するのに要する時間の長さ。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|1 回の繰り返し|タイムラインが 1 回前に再生され、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティが true の場合は 1 回逆方向に再生されるまでの時間。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|アクティブ期間|タイムラインが<xref:System.Windows.Media.Animation.RepeatBehavior>プロパティで指定されたすべての繰り返しを完了するまでにかかる時間。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>Duration プロパティ  
 既に述べたように、タイムラインは時間のセグメントを表します。 セグメントの長さはタイムラインの<xref:System.Windows.Media.Animation.Timeline.Duration%2A>. タイムラインは、期間の最後に到達すると、再生を停止します。 タイムラインに子タイムラインがある場合は、子も再生を停止します。 アニメーションの場合、 は<xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションの開始値から終了値に移行するまでの時間を指定します。 タイムラインの継続時間は、単一の反復の継続時間と繰り返しを含むアニメーションの再生時間の合計長を区別するために、*その期間を単純な期間*と呼ぶこともあります。 期間は、有限時間値または特殊値<xref:System.Windows.Duration.Automatic%2A>を<xref:System.Windows.Duration.Forever%2A>使用して指定できます。 アニメーションの継続時間は値に解決され<xref:System.Windows.Duration.TimeSpan%2A>、値間を遷移させることができます。  
  
 次の例は、5 <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.Duration%2A>秒の a を示しています。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 や<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.ParallelTimeline>などのコンテナー タイムラインには、既定の<xref:System.Windows.Duration.Automatic%2A>期間が設定されています。 次の例は、<xref:System.Windows.Media.Animation.Storyboard>解決<xref:System.Windows.Media.Animation.Timeline.Duration%2A>が 5 秒に、すべての子<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトが完了するまでの時間を示しています。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 コンテナタイムラインの<xref:System.Windows.Media.Animation.Timeline.Duration%2A>を<xref:System.Windows.Duration.TimeSpan%2A>値に設定すると、子<xref:System.Windows.Media.Animation.Timeline>オブジェクトが再生するよりも長く再生するか、短く再生できます。 をコンテナー タイムライン<xref:System.Windows.Media.Animation.Timeline.Duration%2A>の子<xref:System.Windows.Media.Animation.Timeline>オブジェクトの長さより小さい値に設定すると、コンテナタイムラインが終了すると子<xref:System.Windows.Media.Animation.Timeline>オブジェクトの再生が停止します。 次の例では、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>前の<xref:System.Windows.Media.Animation.Storyboard>例の を 3 秒に設定します。 その結果、最初の四<xref:System.Windows.Media.Animation.DoubleAnimation>角形の幅が 60 にアニメーション化されると、最初の処理は 3 秒後に進行を停止します。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>RepeatBehavior プロパティ  
 プロパティ<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>は、<xref:System.Windows.Media.Animation.Timeline>その単純な継続時間を繰り返す回数を制御します。 プロパティを<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>使用して、タイムライン再生回数 (反復<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) または再生時間の合計時間 (繰り返し<xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>) を指定できます。 いずれの場合も、アニメーションは、要求されたカウントまたは期間を満たすのに必要な回数だけ実行を繰り返します。 デフォルトでは、タイムラインの反復回数は`1.0`、1 回再生され、まったく繰り返されません。  
  
 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>このプロパティを使用<xref:System.Windows.Media.Animation.DoubleAnimation>して、反復回数を指定して、単純な時間の 2 倍の再生を行います。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを使用して<xref:System.Windows.Media.Animation.DoubleAnimation>、半分の単純な期間のプレイを作成します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 の<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>プロパティを に<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>設定すると、<xref:System.Windows.Media.Animation.Timeline>対話式またはタイミング システムによって停止するまで繰り返されます。 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>このプロパティを使用<xref:System.Windows.Media.Animation.DoubleAnimation>して、再生を無期限に行います。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 その他の例については、「[アニメーションを繰り返す](how-to-repeat-an-animation.md)」を参照してください。  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>AutoReverse プロパティ  
 プロパティ<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>は、各前方<xref:System.Windows.Media.Animation.Timeline>反復の終了時に a が逆方向に再生するかどうかを指定します。 次の例では、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> to<xref:System.Windows.Media.Animation.DoubleAnimation>のプロパティ`true`を設定します。その結果、0 から 100 まで、100 からゼロまでアニメーション化されます。 合計 10 秒間再生されます。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>の値を使用して、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>のプロパティを<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>指定すると、1<xref:System.Windows.Media.Animation.Timeline>回`true`の繰り返しは、1 つの順方向反復と、逆方向の反復で構成されます。  次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>前の<xref:System.Windows.Media.Animation.DoubleAnimation>例の を 2<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>の a に設定します。 その結果<xref:System.Windows.Media.Animation.DoubleAnimation>、20秒間再生されます:5秒間前進し、5秒間後方に、再び5秒間前進し、5秒間後方に戻ります。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 コンテナタイムラインに子<xref:System.Windows.Media.Animation.Timeline>オブジェクトがある場合、コンテナタイムラインが逆になります。 その他の例については、「[タイムラインを自動的に反転させるかどうかを指定する](how-to-specify-whether-a-timeline-automatically-reverses.md)」を参照してください。  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>BeginTime プロパティ  
 この<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>プロパティを使用すると、タイムラインの開始タイミングを指定できます。  タイムラインの開始時間は、親タイムラインを基準とした相対値になります。 開始時間を 0 秒に設定すると、タイムラインはその親が開始されると直ちに開始されます。その他の値に設定すると、親タイムラインの再生開始時点と子タイムラインの再生時点の間のオフセットが作成されます。 たとえば、開始時間を 2 秒に設定すると、タイムラインは、その親が 2 秒の時点に到達すると再生を開始します。 既定では、すべてのタイムラインの開始時間は 0 秒です。 タイムラインの開始時刻を に`null`設定すると、タイムラインが開始されなくなります。 では[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 [x:Null マークアップ拡張](../../../desktop-wpf/xaml-services/xnull-markup-extension.md)を使用して null を指定します。  
  
 設定が原因でタイムラインが繰り返されるたびに開始時間が適用されないことに<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>注意してください。 10 秒のアニメーション<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>を作成し、<xref:System.Windows.Media.Animation.RepeatBehavior><xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>のアニメーションを作成する場合、アニメーションが最初に再生されるまでに 10 秒の遅延が発生しますが、連続する各繰り返しに対しては 10 秒の遅延が発生します。 ただし、アニメーションの親タイムラインの再開または繰り返しが行われた場合は、10 秒の遅延が発生します。  
  
 この<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>プロパティは、タイムラインをずらす場合に便利です。 2 つの子<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトを持つ を作成する例を次に示します。 最初のアニメーションは<xref:System.Windows.Media.Animation.Timeline.Duration%2A>5 秒、2 番目<xref:System.Windows.Media.Animation.Timeline.Duration%2A>のアニメーションは 3 秒です。 この例では、2<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>番目<xref:System.Windows.Media.Animation.DoubleAnimation>のを 5 秒に設定し、最初<xref:System.Windows.Media.Animation.DoubleAnimation>の終了後に再生を開始します。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>FillBehavior プロパティ  
 a<xref:System.Windows.Media.Animation.Timeline>がアクティブな合計期間の終わりに達すると<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>、プロパティは最後の値を停止するか保持するかを指定します。 のアニメーションの出力<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>値<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>を保持するアニメーション:アニメーション化中のプロパティは、アニメーションの最後の値を保持します。 値の<xref:System.Windows.Media.Animation.FillBehavior.Stop>値は、アニメーションが終了した後にターゲット プロパティに影響を与えなくなる原因です。  
  
 2 つの子<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトを持つ を作成する例を次に示します。 両方<xref:System.Windows.Media.Animation.DoubleAnimation><xref:System.Windows.FrameworkElement.Width%2A>のオブジェクトは、0 から<xref:System.Windows.Shapes.Rectangle>100 の a をアニメーション化します。 これらの<xref:System.Windows.Shapes.Rectangle>要素には、500 [デバイスに依存しないピクセル] のアニメーション化されていない<xref:System.Windows.FrameworkElement.Width%2A>値があります。  
  
- 最初<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A><xref:System.Windows.Media.Animation.DoubleAnimation>のプロパティは、既定値に<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>設定されます。 その結果、長方形の幅は終了後も 100 のままです<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
- 2<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>番目<xref:System.Windows.Media.Animation.DoubleAnimation>のプロパティは<xref:System.Windows.Media.Animation.FillBehavior.Stop>に設定されます。 その結果、2<xref:System.Windows.FrameworkElement.Width%2A>番目<xref:System.Windows.Shapes.Rectangle>のののは、終了後に 500 に戻ります<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>タイムラインの速度を制御するプロパティ  
 この<xref:System.Windows.Media.Animation.Timeline>クラスには、速度を指定するための 3 つのプロパティがあります。  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– その速度を、その親に対して相対的に、その時間が<xref:System.Windows.Media.Animation.Timeline>進むを指定します。 1 より大きい値を設定すると<xref:System.Windows.Media.Animation.Timeline>、 とその<xref:System.Windows.Media.Animation.Timeline>子オブジェクトの速度が上がります。0 と 1 の間の値は、それを遅くします。 値が 1 の<xref:System.Windows.Media.Animation.Timeline>場合は、親と同じ速度で進行することを示します。 コンテナ<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>タイムラインの設定は、そのすべての子<xref:System.Windows.Media.Animation.Timeline>オブジェクトにも影響します。  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– タイムラインの加速に<xref:System.Windows.Media.Animation.Timeline.Duration%2A>費やされた割合を指定します。 例については、「[方法: アニメーションを加速または減速する」を](how-to-accelerate-or-decelerate-an-animation.md)参照してください。
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- タイムラインの減速に<xref:System.Windows.Media.Animation.Timeline.Duration%2A>費やされた割合を指定します。 例については、「[方法: アニメーションを加速または減速する」を](how-to-accelerate-or-decelerate-an-animation.md)参照してください。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [タイミング イベントの概要](timing-events-overview.md)
- [ハウツートピック](animation-and-timing-how-to-topics.md)
- [アニメーションのタイミング動作のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)

---
title: タイミング動作の概要
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: c3403a8602cc874e993bd649851b77d7bf652cce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129598"
---
# <a name="timing-behaviors-overview"></a>タイミング動作の概要
このトピックでは、アニメーション、およびその他のタイミング動作を説明します。<xref:System.Windows.Media.Animation.Timeline>オブジェクト。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、基本的なアニメーション機能に精通している必要があります。 詳細については、次を参照してください。、[アニメーションの概要](animation-overview.md)します。  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>タイムラインの型  
 A<xref:System.Windows.Media.Animation.Timeline>時間のセグメントを表します。 用意されているプロパティを使用して、そのセグメントの長さ、開始時間、繰り返し回数、時間の進行の速度などを指定できます。  
  
 Timeline クラスを継承するクラスには、アニメーションやメディアの再生などの追加機能が用意されています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 次は、<xref:System.Windows.Media.Animation.Timeline>型。  
  
|タイムラインの型|説明|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|抽象基本クラス<xref:System.Windows.Media.Animation.Timeline>プロパティをアニメーション化するための出力値を生成するオブジェクト。|  
|<xref:System.Windows.Media.MediaTimeline>|メディア ファイルから出力を生成します。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|型<xref:System.Windows.Media.Animation.TimelineGroup>そのグループやコントロールの子<xref:System.Windows.Media.Animation.Timeline>オブジェクト。|  
|<xref:System.Windows.Media.Animation.Storyboard>|型<xref:System.Windows.Media.Animation.ParallelTimeline>が含まれている Timeline オブジェクトの対象とする情報を提供します。|  
|<xref:System.Windows.Media.Animation.Timeline>|タイミング動作を定義する抽象基本クラス。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|抽象クラス<xref:System.Windows.Media.Animation.Timeline>他を含めることができるオブジェクト<xref:System.Windows.Media.Animation.Timeline>オブジェクト。|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>タイムラインの長さを制御するプロパティ  
 A<xref:System.Windows.Media.Animation.Timeline>表しますが、時間のセグメントと、タイムラインの長さは、さまざまな方法で記述できます。 タイムラインの長さを示すいくつかの用語の定義を次の表に示します。  
  
|用語|説明|プロパティ||||  
|----------|-----------------|----------------|-|-|-|  
|単純継続時間|タイムラインが順方向の反復を 1 回完了するのに要する時間の長さ。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|1 回の繰り返し|タイムラインにする場合とすると、再生にかかる時間の長さ、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティが true の場合、旧バージョンと 1 回再生します。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|アクティブ期間|タイムラインで指定されたすべての繰り返しを完了するにかかる時間の長さ、<xref:System.Windows.Media.Animation.RepeatBehavior>プロパティ。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>、 <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration プロパティ  
 既に述べたように、タイムラインは時間のセグメントを表します。 そのセグメントの長さはタイムラインのによって決まります<xref:System.Windows.Media.Animation.Timeline.Duration%2A>します。 タイムラインは、期間の最後に到達すると、再生を停止します。 タイムラインに子タイムラインがある場合は、子も再生を停止します。 アニメーションの場合は、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションにかかる時間の遷移の終了値をその開始値から指定します。 タイムラインの継続時間とも呼ばれますその*単純継続時間*、1 つのイテレーションの期間と繰り返しを含む、アニメーションの再生に要する時間の長さの合計とを区別します。 有限の時間値または特殊な値を使用して期間を指定することができます<xref:System.Windows.Duration.Automatic%2A>または<xref:System.Windows.Duration.Forever%2A>します。 アニメーションの継続時間に解決する必要があります、<xref:System.Windows.Duration.TimeSpan%2A>値、値の間を遷移できるようにします。  
  
 次の例は、<xref:System.Windows.Media.Animation.DoubleAnimation>で、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 秒間です。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 コンテナー タイムラインなど<xref:System.Windows.Media.Animation.Storyboard>と<xref:System.Windows.Media.Animation.ParallelTimeline>の既定の時間が指定されて<xref:System.Windows.Duration.Automatic%2A>、つまり、これらは、最後の子が停止したときに自動的に終了します。 次の例は、<xref:System.Windows.Media.Animation.Storyboard>が<xref:System.Windows.Media.Animation.Timeline.Duration%2A>5 秒間、すべての子にかかる時間の長さに解決される<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトが完了します。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 設定して、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>をコンテナー タイムラインの<xref:System.Windows.Duration.TimeSpan%2A>値、その子でなかったりの再生を強制できます<xref:System.Windows.Media.Animation.Timeline>オブジェクトで再生します。 設定した場合、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>をコンテナー タイムラインの子の長さよりも小さい値に<xref:System.Windows.Media.Animation.Timeline>オブジェクト、子<xref:System.Windows.Media.Animation.Timeline>オブジェクトが場合は、コンテナー タイムラインの再生を停止します。 次の例のセット、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>の<xref:System.Windows.Media.Animation.Storyboard>を 3 秒に前の例から。 その結果、最初の<xref:System.Windows.Media.Animation.DoubleAnimation>ターゲットの四角形の幅を 60 にアニメーション化すると、3 秒後に処理を停止します。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior プロパティ  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティを<xref:System.Windows.Media.Animation.Timeline>単純継続時間が繰り返される回数を制御します。 使用して、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティ、何回、タイムラインの再生を指定することができます (イテレーション<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) または再生時間の長さの合計 (繰り返し<xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>)。 いずれの場合も、アニメーションは、要求されたカウントまたは期間を満たすのに必要な回数だけ実行を繰り返します。 既定では、タイムラインがあるの反復カウント`1.0`つまり、1 回再生され、まったく、繰り返されない。  
  
 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>反復カウントを指定することで、単純な期間 2 倍の再生します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>単純継続時間を半分を再生します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 設定した場合、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティを<xref:System.Windows.Media.Animation.Timeline>に<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>、<xref:System.Windows.Media.Animation.Timeline>対話形式で、またはタイミング システムによって停止されるまで繰り返されます。 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>無限に再生します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 たとえば、次を参照してください。[アニメーションを反復する](how-to-repeat-an-animation.md)します。  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse プロパティ  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティを指定するかどうかを<xref:System.Windows.Media.Animation.Timeline>各順方向の反復の最後に逆方向に再生されます。 次の例の設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>のプロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>に`true`; その結果、0 から 100、し、100 0 からまでアニメーション化されます。 合計 10 秒間再生されます。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 使用する場合、<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>を指定する値、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>の<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティを<xref:System.Windows.Media.Animation.Timeline>は`true`、1 つの 1 つの繰り返しには内を後方に向かって反復処理のいずれかが、順方向の反復が続きます。  次の例のセット、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>の<xref:System.Windows.Media.Animation.DoubleAnimation>を前の例から、<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>の 2 つです。 結果として、 <xref:System.Windows.Media.Animation.DoubleAnimation> 20 秒間再生され: 順方向に再度、5 秒間に、5 秒の旧バージョンと、5 秒を転送し、5 秒の旧バージョンとします。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 コンテナー タイムラインに子<xref:System.Windows.Media.Animation.Timeline>オブジェクトの場合は、コンテナー タイムラインが反転します。 その他の例では、次を参照してください。[を指定するかどうか、タイムラインを自動的に反転](how-to-specify-whether-a-timeline-automatically-reverses.md)します。  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime プロパティ  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>プロパティでは、タイムラインの開始時に指定することができます。  タイムラインの開始時間は、親タイムラインを基準とした相対値になります。 開始時間を 0 秒に設定すると、タイムラインはその親が開始されると直ちに開始されます。その他の値に設定すると、親タイムラインの再生開始時点と子タイムラインの再生時点の間のオフセットが作成されます。 たとえば、開始時間を 2 秒に設定すると、タイムラインは、その親が 2 秒の時点に到達すると再生を開始します。 既定では、すべてのタイムラインの開始時間は 0 秒です。 タイムラインを設定することもできます。 開始時刻に`null`、タイムラインは開始されませんが。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して null を指定する、 [X:null マークアップ拡張機能](../../xaml-services/x-null-markup-extension.md)します。  
  
 開始時間がないので注意適用のため、タイムラインが繰り返されるたびにその<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設定します。 アニメーションを作成する場合、 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 秒間の<xref:System.Windows.Media.Animation.RepeatBehavior>の<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>、後続の各繰り返しではなく、最初のアニメーションが再生される前に、10 秒の遅延にするとします。 ただし、アニメーションの親タイムラインの再開または繰り返しが行われた場合は、10 秒の遅延が発生します。  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>プロパティは、タイムラインをずらす際に役立ちます。 次の例では、作成、 <xref:System.Windows.Media.Animation.Storyboard> 2 つの子を持つ<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクト。 最初のアニメーションが、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 、5 秒の 2 番目であり、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 3 秒。 例のセット、 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 、2 つ目の<xref:System.Windows.Media.Animation.DoubleAnimation>、5 秒間にそのためその it の再生が開始、最初より後<xref:System.Windows.Media.Animation.DoubleAnimation>が終了します。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior プロパティ  
 ときに、<xref:System.Windows.Media.Animation.Timeline>がその合計アクティブ期間の末尾に達すると、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、停止するかその最終的な値を保持しているかどうかを指定します。 アニメーション、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>出力値は「保持」: アニメーション化されているプロパティのアニメーションの最後の値を保持します。 値<xref:System.Windows.Media.Animation.FillBehavior.Stop>終了後、ターゲット プロパティに影響を与えるアニメーション stop に設定するとします。  
  
 次の例では、作成、 <xref:System.Windows.Media.Animation.Storyboard> 2 つの子を持つ<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクト。 両方<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトをアニメーション化する、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>0 ~ 100 です。 <xref:System.Windows.Shapes.Rectangle>要素がアニメーション化されていない<xref:System.Windows.FrameworkElement.Width%2A>500 [デバイス非依存ピクセル] の値。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>最初の<xref:System.Windows.Media.Animation.DoubleAnimation>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>既定値。 四角形の幅が 100 の後に保持する結果として、<xref:System.Windows.Media.Animation.DoubleAnimation>が終了します。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、2 つ目の<xref:System.Windows.Media.Animation.DoubleAnimation>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。 結果として、 <xref:System.Windows.FrameworkElement.Width%2A> 、2 つ目の<xref:System.Windows.Shapes.Rectangle>後 500 に戻ります、<xref:System.Windows.Media.Animation.DoubleAnimation>が終了します。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>タイムラインの速度を制御するプロパティ  
 <xref:System.Windows.Media.Animation.Timeline>クラスの速度を指定するための 3 つのプロパティを提供します。  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – の時間の進行を親に対する相対的な速度を指定します、<xref:System.Windows.Media.Animation.Timeline>します。 1 より大きい値の処理速度の向上、<xref:System.Windows.Media.Animation.Timeline>とその子<xref:System.Windows.Media.Animation.Timeline>オブジェクトは 0 から 1 までの値遅きます。 いずれかの値が示す<xref:System.Windows.Media.Animation.Timeline>その親と同じ速度で進行します。 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>コンテナー タイムラインの設定では、そのすべての子に影響<xref:System.Windows.Media.Animation.Timeline>オブジェクトもします。  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – の割合を指定します、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>タイムラインの加速に費やされたします。 例については、「[方法: 加速または減速するアニメーション](how-to-accelerate-or-decelerate-an-animation.md)します。 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -の割合を指定します、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>タイムラインの減速に費やされたします。 例については、「[方法: 加速または減速するアニメーション](how-to-accelerate-or-decelerate-an-animation.md)します。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [タイミング イベントの概要](timing-events-overview.md)
- [方法トピック](animation-and-timing-how-to-topics.md)
- [アニメーションのタイミング動作のサンプル](https://go.microsoft.com/fwlink/?LinkID=159970)

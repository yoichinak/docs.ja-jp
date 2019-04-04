---
title: アニメーションのヒントとテクニック
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
ms.openlocfilehash: e8b2a6b5386ec33ad8aa5281d808bb7089149764
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362436"
---
# <a name="animation-tips-and-tricks"></a>アニメーションのヒントとテクニック
アニメーションを扱うときに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ヒントがいくつか、およびアニメーションを実行できるテクニックはパフォーマンスを向上させ、不満を解消します。  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>一般的な問題  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>スクロール バーまたはスライダーの位置をアニメーション化するとフリーズする  
 スクロール バーまたはスライダーを持つアニメーションを使用しての位置をアニメーション化する場合、<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>(既定値) の場合は、ユーザーしなくなるスクロール バーまたはスライダーを移動できません。 原因は、アニメーションが終了しても、ターゲット プロパティの基底値をまだオーバーライドしているためです。 プロパティの現在の値を上書きするアニメーションを停止するには、削除するか、試して、<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。 詳細と例では、[を設定するプロパティの後アニメーション ストーリー ボードを](how-to-set-a-property-after-animating-it-with-a-storyboard.md)を参照してください。  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>アニメーションの出力のアニメーション化の効果がない  
 別のアニメーションの出力であるオブジェクトをアニメーション化することはできません。 使用する場合など、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>をアニメーション化する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>から、<xref:System.Windows.Media.RadialGradientBrush>を<xref:System.Windows.Media.SolidColorBrush>の任意のプロパティをアニメーション化することはできません、<xref:System.Windows.Media.RadialGradientBrush>または<xref:System.Windows.Media.SolidColorBrush>します。  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>プロパティをアニメーション化した後にその値を変更できない  
 場合によっては、アニメーションが完了した後でも、アニメーション化の後にプロパティの値を変更できないように見えることがあります。 原因は、アニメーションが終了しても、プロパティの基底値をまだオーバーライドしているためです。 プロパティの現在の値を上書きするアニメーションを停止するには、削除するか、試して、<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。 詳細と例では、[を設定するプロパティの後アニメーション ストーリー ボードを](how-to-set-a-property-after-animating-it-with-a-storyboard.md)を参照してください。  
  
### <a name="changing-a-timeline-has-no-effect"></a>タイムラインを変更しても効果がない  
 ただしほとんど<xref:System.Windows.Media.Animation.Timeline>プロパティはアニメーション化できる、データ バインドできるは、アクティブなプロパティ値を変更する<xref:System.Windows.Media.Animation.Timeline>効果がないようです。 です、<xref:System.Windows.Media.Animation.Timeline>はタイミング システムの開始のコピーを作成、<xref:System.Windows.Media.Animation.Timeline>を使用して作成し、<xref:System.Windows.Media.Animation.Clock>オブジェクト。 元を変更しても、システムのコピーには影響しません。  
  
 <xref:System.Windows.Media.Animation.Timeline>変更を反映するようにクロックする必要がありますが再生され、以前に作成されたクロックを置き換えるために使用します。 クロックは、自動的には再生成されません。 タイムラインの変更を適用するいくつかの方法を次に示します。  
  
-   タイムラインがまたはに属している場合、 <xref:System.Windows.Media.Animation.Storyboard>、そのストーリー ボードを使用して再適用して変更を反映することを行うことができます、<xref:System.Windows.Media.Animation.BeginStoryboard>または<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッド。 これには、アニメーションが再起動されるという副作用があります。 コードでは、使用することができます、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>メソッド、ストーリー ボードを前の位置にバックアップします。  
  
-   使用してプロパティに直接アニメーションを適用したかどうか、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを呼び出します、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを再度変更されたアニメーションを渡します。  
  
-   クロック レベルで直接操作している場合は、新しいクロック セットを作成して適用し、それらを使って、生成されたクロックの以前のセットを置換します。  
  
 詳細については、タイムラインとクロックは、[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)を参照してください。  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop が期待どおりに動作しない  
 あります設定するときに、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.FillBehavior.Stop>場合などの効果がないように見えるアニメーションを 1 つに「ハンドオフ」間があるため、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>の設定<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。  
  
 次の例では、作成、 <xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Shapes.Rectangle>と<xref:System.Windows.Media.TranslateTransform>します。 <xref:System.Windows.Media.TranslateTransform>を移動するアニメーションは、<xref:System.Windows.Shapes.Rectangle>の周囲、<xref:System.Windows.Controls.Canvas>します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 このセクションの例をいくつかのケースを示すために、前のオブジェクトを使用して、場所、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティが予想どおりに動作しません。  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>複数のアニメーションでの FillBehavior="Stop" と HandoffBehavior  
 思えますアニメーションを無視するよう、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティと 2 番目のアニメーションに置き換えられます。 次の例は、2 つ作成されますがかかる<xref:System.Windows.Media.Animation.Storyboard>オブジェクトし、同じをアニメーション化を使用して<xref:System.Windows.Media.TranslateTransform>前の例に示すようにします。  
  
 最初の<xref:System.Windows.Media.Animation.Storyboard>、 `B1`、アニメーション、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> 350 0、右側に四角形 350 ピクセルに移動します。 アニメーションがその継続時間の終わりに達したし、再生が停止するときに、<xref:System.Windows.Media.TranslateTransform.X%2A>プロパティは、元の値を 0 に戻ります。 その結果、四角形は右に 350 ピクセル移動し、元の位置に移動します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 2 番目の<xref:System.Windows.Media.Animation.Storyboard>、 `B2`、アニメーション化も、<xref:System.Windows.Media.TranslateTransform.X%2A>の同じプロパティ<xref:System.Windows.Media.TranslateTransform>します。 ため、のみ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>このアニメーションのプロパティ<xref:System.Windows.Media.Animation.Storyboard>がアニメーションでは、アニメーション化するプロパティの現在の値を使用して、その開始値として設定します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 最初の 2 番目のボタンをクリックすると<xref:System.Windows.Media.Animation.Storyboard>が再生するには、次の動作を期待可能性があります。  
  
1.  最初のストーリー ボードが終了し、アニメーションがあるため、元の位置に、四角形を送信する<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。  
  
2.  2 つ目のストーリーボードが反映され、現在位置である 0 から 500 にアニメーション化します。  
  
 **しかし、これは行われません。** 代わりに、四角形は戻らずに、右に移動し続けます。 その理由は、2 番目のアニメーションは最初のアニメーションの現在の値を開始値として使い、その値から 500 までアニメーション化するためです。 に 2 番目のアニメーションが最初を置換するときに、 <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior>を使用する、<xref:System.Windows.Media.Animation.FillBehavior>最初のアニメーションは重要ではありません。  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior と完了イベント  
 次の例では、別のシナリオの場合、 <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>効果がないようです。 例では、ストーリーを使用して、もう一度、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> 350 に 0 からです。 ただし、この時間を登録します、<xref:System.Windows.Media.Animation.Timeline.Completed>イベント。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed>イベント ハンドラーを起動別<xref:System.Windows.Media.Animation.Storyboard>を現在の値からの同じプロパティを 500 にアニメーション化します。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 次に、2 つ目を定義するマークアップ<xref:System.Windows.Media.Animation.Storyboard>リソースとして。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 実行すると、 <xref:System.Windows.Media.Animation.Storyboard>、想像、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> 、アニメーション化する 0 から 350 にし、元に戻すを 0 に完了した後 (があるため、<xref:System.Windows.Media.Animation.FillBehavior>の設定<xref:System.Windows.Media.Animation.FillBehavior.Stop>)、および 0 から 500 にアニメーション化します。 代わりに、 <xref:System.Windows.Media.TranslateTransform> 0 から 350、その後 500 にアニメーション化します。  
  
 あるため、順序[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]イベントを発生させ、プロパティが無効にしない限り、プロパティの値はキャッシュされないためが再計算されます。 <xref:System.Windows.Media.Animation.Timeline.Completed>ルート タイムラインによってトリガーされたために、最初に処理イベント (最初の<xref:System.Windows.Media.Animation.Storyboard>)。 この時点で、<xref:System.Windows.Media.TranslateTransform.X%2A>プロパティにまだ無効にされていないため、まだそのアニメーション化された値を返します。 2 番目の<xref:System.Windows.Media.Animation.Storyboard>その開始値として、キャッシュされた値を使用し、アニメーション化を開始します。  
  
<a name="performancesection"></a>   
## <a name="performance"></a>パフォーマンス  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>アニメーションがページからの移動後も実行され続ける  
 移動すると、<xref:System.Windows.Controls.Page>実行中のアニメーションを格納している、これらのアニメーションの再生までは引き続き、<xref:System.Windows.Controls.Page>はガベージ コレクトされます。 使っているナビゲーション システムによっては、離れた後のページが無期限にメモリに残り、その間、そのアニメーションでリソースが消費されることがあります。 これは、ページに常時実行 ("アンビエント") アニメーションが含まれる場合に最も顕著です。  
  
 このため、これを使用することをお勧め、<xref:System.Windows.FrameworkElement.Unloaded>ページから移動するときに、アニメーションを削除するイベントです。  
  
 アニメーションを削除する別の方法もあります。 属するアニメーションを削除する、次の手法を使用できます、<xref:System.Windows.Media.Animation.Storyboard>します。  
  
-   削除する、<xref:System.Windows.Media.Animation.Storyboard>イベント トリガーで開始したを参照してください[方法。ストーリー ボードを削除](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90))します。  
  
-   コードを使用して、削除する、<xref:System.Windows.Media.Animation.Storyboard>を参照してください、<xref:System.Windows.Media.Animation.Storyboard.Remove%2A>メソッド。  
  
 次の手法は、アニメーションの開始方法に関係なく使用できます。  
  
-   特定のプロパティからアニメーションを削除するには、使用、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>メソッド。 最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。 これにより、すべてのアニメーション クロックがプロパティから削除されます。  
  
 プロパティをアニメーション化するさまざまな方法の詳細については、[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)を参照してください。  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>HandoffBehavior を使うとシステム リソースが消費される  
 適用すると、 <xref:System.Windows.Media.Animation.Storyboard>、 <xref:System.Windows.Media.Animation.AnimationTimeline>、または<xref:System.Windows.Media.Animation.AnimationClock>を使用してプロパティを<xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>、any<xref:System.Windows.Media.Animation.Clock>以前そのプロパティに関連付けられているオブジェクトは引き続きシステム リソースを消費しますタイミング システムはありません。これらのクロックを自動的に削除します。  
  
 使用してクロックの数が多いを適用すると、パフォーマンスの問題を回避するために<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>、完了後に、アニメーション化されたプロパティから構成クロックを削除する必要があります。 クロックを削除する方法はいくつかあります。  
  
-   プロパティからすべてのクロックを削除するには、使用、<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29>または<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>アニメーション化されたオブジェクトのメソッド。 最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。 これにより、すべてのアニメーション クロックがプロパティから削除されます。  
  
-   特定を削除する<xref:System.Windows.Media.Animation.AnimationClock>クロックの一覧は、使用して、<xref:System.Windows.Media.Animation.Clock.Controller%2A>のプロパティ、<xref:System.Windows.Media.Animation.AnimationClock>を取得する、 <xref:System.Windows.Media.Animation.ClockController>、呼び出して、<xref:System.Windows.Media.Animation.ClockController.Remove%2A>のメソッド、<xref:System.Windows.Media.Animation.ClockController>します。 これは、通常、<xref:System.Windows.Media.Animation.Clock.Completed>クロックのイベント ハンドラー。 唯一のルート クロックを使用して制御できることに注意してください、 <xref:System.Windows.Media.Animation.ClockController>、<xref:System.Windows.Media.Animation.Clock.Controller%2A>子クロックのプロパティを返します`null`します。 なお、<xref:System.Windows.Media.Animation.Clock.Completed>クロックの有効期間が永久の場合、イベントは呼び出されません。  その場合は、ユーザーを呼び出すタイミングを決定する必要がある<xref:System.Windows.Media.Animation.ClockController.Remove%2A>します。  
  
 これは主に、有効期間が長いオブジェクトでのアニメーションの問題です。  オブジェクトがガベージ コレクションされる場合は、そのクロックも切断されて、ガベージ コレクションされます。  
  
 クロック オブジェクトの詳細については、[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)

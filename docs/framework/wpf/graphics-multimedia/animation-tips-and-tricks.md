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
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187647"
---
# <a name="animation-tips-and-tricks"></a>アニメーションのヒントとテクニック
WPF でアニメーションを操作する場合、アニメーションのパフォーマンスを向上させ、フラストレーションを抑えることができるヒントやテクニックが数多く用意されています。  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>一般的な問題  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>スクロール バーまたはスライダーの位置をアニメーション化するとフリーズする  
 の値を持つアニメーションを使用してスクロール バーまたはスライダー<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>位置をアニメーション化すると、ユーザーはスクロール バーまたはスライダーを移動できなくなります。 原因は、アニメーションが終了しても、ターゲット プロパティの基底値をまだオーバーライドしているためです。 アニメーションがプロパティの現在の値をオーバーライドしないようにするには、そのプロパティを削除するか、または<xref:System.Windows.Media.Animation.FillBehavior><xref:System.Windows.Media.Animation.FillBehavior.Stop>を a に指定します。 詳細と例については、「[ストーリーボードを使用してアニメーション化した後にプロパティを設定する](how-to-set-a-property-after-animating-it-with-a-storyboard.md)」を参照してください。  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>アニメーションの出力のアニメーション化の効果がない  
 別のアニメーションの出力であるオブジェクトをアニメーション化することはできません。 たとえば<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>、 を使用して から a の<xref:System.Windows.Shapes.Shape.Fill%2A>を<xref:System.Windows.Shapes.Rectangle>アニメーション<xref:System.Windows.Media.RadialGradientBrush><xref:System.Windows.Media.SolidColorBrush>化する場合、<xref:System.Windows.Media.RadialGradientBrush>または<xref:System.Windows.Media.SolidColorBrush>のプロパティをアニメーション化することはできません。  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>プロパティをアニメーション化した後にその値を変更できない  
 場合によっては、アニメーションが完了した後でも、アニメーション化の後にプロパティの値を変更できないように見えることがあります。 原因は、アニメーションが終了しても、プロパティの基底値をまだオーバーライドしているためです。 アニメーションがプロパティの現在の値をオーバーライドしないようにするには、そのプロパティを削除するか、または<xref:System.Windows.Media.Animation.FillBehavior><xref:System.Windows.Media.Animation.FillBehavior.Stop>を a に指定します。 詳細と例については、「[ストーリーボードを使用してアニメーション化した後にプロパティを設定する](how-to-set-a-property-after-animating-it-with-a-storyboard.md)」を参照してください。  
  
### <a name="changing-a-timeline-has-no-effect"></a>タイムラインを変更しても効果がない  
 ほとんどの<xref:System.Windows.Media.Animation.Timeline>プロパティはアニメート可能で、データ バインドできますが、アクティブ<xref:System.Windows.Media.Animation.Timeline>のプロパティ値を変更しても効果がないようです。 なぜなら、a が<xref:System.Windows.Media.Animation.Timeline>始まると、タイミングシステムは のコピーを作成<xref:System.Windows.Media.Animation.Timeline>し、それを使用してオブジェクトを作成<xref:System.Windows.Media.Animation.Clock>するためです。 元を変更しても、システムのコピーには影響しません。  
  
 変更<xref:System.Windows.Media.Animation.Timeline>を反映するには、そのクロックを再生成し、以前に作成したクロックを置き換えるために使用する必要があります。 クロックは、自動的には再生成されません。 タイムラインの変更を適用するいくつかの方法を次に示します。  
  
- タイムラインが<xref:System.Windows.Media.Animation.Storyboard>に属している場合、または メソッドを使用して<xref:System.Windows.Media.Animation.BeginStoryboard><xref:System.Windows.Media.Animation.Storyboard.Begin%2A>ストーリーボードを再適用することで、変更を反映させることができます。 これには、アニメーションが再起動されるという副作用があります。 コードでは、このメソッドを<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>使用して、ストーリーボードを以前の位置に戻すことができます。  
  
- メソッドを使用してプロパティにアニメーションを直接適用した<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>場合は、メソッド<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>を再度呼び出して、変更されたアニメーションを渡します。  
  
- クロック レベルで直接操作している場合は、新しいクロック セットを作成して適用し、それらを使って、生成されたクロックの以前のセットを置換します。  
  
 タイムラインとクロックの詳細については、「[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)」を参照してください。  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop が期待どおりに動作しない  
 プロパティを<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>設定しても<xref:System.Windows.Media.Animation.FillBehavior.Stop>効果がない場合があります。 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>  
  
 次の例では、 <xref:System.Windows.Controls.Canvas>a<xref:System.Windows.Shapes.Rectangle>および<xref:System.Windows.Media.TranslateTransform>a を作成します。 を<xref:System.Windows.Media.TranslateTransform><xref:System.Windows.Shapes.Rectangle>中心に動かすためにアニメーション化されます<xref:System.Windows.Controls.Canvas>。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 このセクションの例では、上記のオブジェクトを使用して、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティが期待どおりに動作しないいくつかのケースを示します。  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>複数のアニメーションでの FillBehavior="Stop" と HandoffBehavior  
 アニメーションが 2 番目のアニメーションに置<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>き換えられたときに、アニメーションのプロパティを無視する場合があります。 次の例では、2 つの<xref:System.Windows.Media.Animation.Storyboard>オブジェクトを作成し、それらのオブジェクトを使用して<xref:System.Windows.Media.TranslateTransform>、前の例に示したアニメーションを作成します。  
  
 1<xref:System.Windows.Media.Animation.Storyboard>つ`B1`目の は、0 <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> ~ 350 のプロパティをアニメーション化し、四角形を 350 ピクセル右に移動します。 アニメーションが継続時間の終わりに達して再生を停止すると、<xref:System.Windows.Media.TranslateTransform.X%2A>プロパティは元の値 0 に戻ります。 その結果、四角形は右に 350 ピクセル移動し、元の位置に移動します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 2<xref:System.Windows.Media.Animation.Storyboard>番目`B2`の プロパティは、同<xref:System.Windows.Media.TranslateTransform.X%2A>じ<xref:System.Windows.Media.TranslateTransform>プロパティもアニメーション化します。 アニメーションでは、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>アニメーション<xref:System.Windows.Media.Animation.Storyboard>のプロパティのみが設定されるため、アニメーションのアニメーションプロパティの現在の値が開始値として使用されます。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 最初<xref:System.Windows.Media.Animation.Storyboard>のボタンの再生中に 2 番目のボタンをクリックすると、次のような動作が予想されます。  
  
1. アニメーションには が を持つため、最初のストーリーボードは終了し、元の<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>位置<xref:System.Windows.Media.Animation.FillBehavior.Stop>に四角形を送り返します。  
  
2. 2 つ目のストーリーボードが反映され、現在位置である 0 から 500 にアニメーション化します。  
  
 **しかし、これは行われません。** 代わりに、四角形は戻らずに、右に移動し続けます。 その理由は、2 番目のアニメーションは最初のアニメーションの現在の値を開始値として使い、その値から 500 までアニメーション化するためです。 が使用されているため<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior>に 2 番目のアニメーションが最初<xref:System.Windows.Media.Animation.FillBehavior>のアニメーションを置き換える場合、最初のアニメーションのは関係ありません。  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior と完了イベント  
 次の例では、 が効果を<xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>持たないと思われる別のシナリオを示します。 この例では、ストーリーボードを使用して 0 ~ <xref:System.Windows.Media.TranslateTransform.X%2A> 350 のプロパティを<xref:System.Windows.Media.TranslateTransform>アニメーション化します。 ただし、今回の例では、イベントに登録<xref:System.Windows.Media.Animation.Timeline.Completed>します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 イベント<xref:System.Windows.Media.Animation.Timeline.Completed>ハンドラーは、<xref:System.Windows.Media.Animation.Storyboard>現在の値から 500 に同じプロパティをアニメーション化する別のプロパティを開始します。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 次に、2 番目<xref:System.Windows.Media.Animation.Storyboard>のリソースを定義するマークアップを示します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 <xref:System.Windows.Media.Animation.Storyboard>を実行すると<xref:System.Windows.Media.TranslateTransform.X%2A>、 の<xref:System.Windows.Media.TranslateTransform>プロパティが 0 から 350 までアニメーション化され、完了後に 0 に戻り (<xref:System.Windows.Media.Animation.FillBehavior>設定が []<xref:System.Windows.Media.Animation.FillBehavior.Stop>の場合) に戻り、0 ~ 500 のアニメーション化が行われる場合があります。 代わりに、<xref:System.Windows.Media.TranslateTransform>アニメーションは 0 から 350 まで、次に 500 にアニメーション化します。  
  
 これは、WPF がイベントを発生させる順序と、プロパティが無効にされない限りプロパティ値がキャッシュされ、再計算されないためです。 イベント<xref:System.Windows.Media.Animation.Timeline.Completed>は、ルートタイムライン (最初<xref:System.Windows.Media.Animation.Storyboard>の) によってトリガーされたため、最初に処理されます。 現時点では、<xref:System.Windows.Media.TranslateTransform.X%2A>まだ無効になっていないため、プロパティはアニメーション化された値を返します。 2<xref:System.Windows.Media.Animation.Storyboard>番目の値は、キャッシュされた値を開始値として使用し、アニメーションを開始します。  
  
<a name="performancesection"></a>
## <a name="performance"></a>パフォーマンス  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>アニメーションがページからの移動後も実行され続ける  
 実行中のアニメーションを含む<xref:System.Windows.Controls.Page>から離れると、これらのアニメーションは ガベージ コレクションが行われる<xref:System.Windows.Controls.Page>まで再生を続けます。 使っているナビゲーション システムによっては、離れた後のページが無期限にメモリに残り、その間、そのアニメーションでリソースが消費されることがあります。 これは、ページに常時実行 ("アンビエント") アニメーションが含まれる場合に最も顕著です。  
  
 このため、ページから移動するときに、イベントを<xref:System.Windows.FrameworkElement.Unloaded>使用してアニメーションを削除することをお勧めします。  
  
 アニメーションを削除する別の方法もあります。 次の方法を使用して、 に属するアニメーションを削除できます<xref:System.Windows.Media.Animation.Storyboard>。  
  
- イベント トリガ<xref:System.Windows.Media.Animation.Storyboard>で開始したイベントを削除するには、「[方法: ストーリーボードを削除する](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90))」を参照してください。  
  
- コードを使用して を<xref:System.Windows.Media.Animation.Storyboard>削除するには、<xref:System.Windows.Media.Animation.Storyboard.Remove%2A>メソッドを参照してください。  
  
 次の手法は、アニメーションの開始方法に関係なく使用できます。  
  
- 特定のプロパティからアニメーションを削除するには、 メソッド<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>を使用します。 アニメーション化するプロパティを最初のパラメータとして指定し`null`、2 番目のパラメータとして指定します。 これにより、すべてのアニメーション クロックがプロパティから削除されます。  
  
 プロパティをアニメーション化するさまざまな方法の詳細については、「[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)」を参照してください。  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>HandoffBehavior を使うとシステム リソースが消費される  
 を<xref:System.Windows.Media.Animation.Storyboard>使用して<xref:System.Windows.Media.Animation.AnimationTimeline><xref:System.Windows.Media.Animation.AnimationClock><xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.Clock>プロパティ に 、 、または を適用すると、そのプロパティに以前に関連付けられたオブジェクトは引き続きシステム リソースを消費します。 <xref:System.Windows.Media.Animation.HandoffBehavior>タイミングシステムは、これらのクロックを自動的に削除しません。  
  
 を使用して<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>多数のクロックを適用する場合にパフォーマンスの問題を回避するには、完了後にアニメーション化されたプロパティから構成クロックを削除する必要があります。 クロックを削除する方法はいくつかあります。  
  
- プロパティからすべてのクロックを削除するには、アニメーションオブジェクトの<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> or メソッドを使用します。 アニメーション化するプロパティを最初のパラメータとして指定し`null`、2 番目のパラメータとして指定します。 これにより、すべてのアニメーション クロックがプロパティから削除されます。  
  
- クロックのリストから<xref:System.Windows.Media.Animation.AnimationClock>特定のを削除するには、 の<xref:System.Windows.Media.Animation.Clock.Controller%2A>プロパティ<xref:System.Windows.Media.Animation.AnimationClock>を使用して<xref:System.Windows.Media.Animation.ClockController>を取得し、 の<xref:System.Windows.Media.Animation.ClockController.Remove%2A>メソッドを呼<xref:System.Windows.Media.Animation.ClockController>び出します。 これは通常、クロックの<xref:System.Windows.Media.Animation.Clock.Completed>イベント ハンドラーで行われます。 ルートクロックのみが、 によって<xref:System.Windows.Media.Animation.ClockController>制御できることに注意してください。子<xref:System.Windows.Media.Animation.Clock.Controller%2A>クロックのプロパティが戻ります`null`。 また、クロックの<xref:System.Windows.Media.Animation.Clock.Completed>有効時間が永久に続く場合は、イベントは呼び出されません。  その場合、ユーザーは、 を呼び出す<xref:System.Windows.Media.Animation.ClockController.Remove%2A>タイミングを決定する必要があります。  
  
 これは主に、有効期間が長いオブジェクトでのアニメーションの問題です。  オブジェクトがガベージ コレクションされる場合は、そのクロックも切断されて、ガベージ コレクションされます。  
  
 クロック オブジェクトの詳細については、「[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)

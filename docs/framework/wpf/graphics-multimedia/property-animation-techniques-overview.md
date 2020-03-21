---
title: プロパティ アニメーションの手法の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181844"
---
# <a name="property-animation-techniques-overview"></a>プロパティ アニメーションの手法の概要
このトピックでは、ストーリーボード、ローカル アニメーション、クロック、フレームごとのアニメーションなど、プロパティをアニメーション化するさまざまなアプローチについて説明します。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、「[アニメーションの概要](animation-overview.md)」で説明されている基本のアニメーション機能に精通している必要があります。  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>さまざまなアニメーション化方法  
 プロパティをアニメーション化するには多数のシナリオがあるため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ではプロパティをアニメーション化するいくつかの方法が提供されます。  
  
 それぞれの方法について、インスタンス単位、スタイル内、コントロール テンプレート内、またはデータ テンプレート内で使用できるかどうか、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で使用できるかどうか、およびアニメーションを対話的に制御できるかどうかを次の表に示します。  "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。  
  
|アニメーションの手法|シナリオ|XAML のサポート|対話的に制御可能|  
|-------------------------|---------------|-------------------|--------------------------------|  
|ストーリー ボード アニメーション|インスタンスごと、 <xref:System.Windows.Style> <xref:System.Windows.Controls.ControlTemplate>、 、<xref:System.Windows.DataTemplate>|はい|はい|  
|ローカル アニメーション|インスタンス単位|いいえ|いいえ|  
|クロック アニメーション|インスタンス単位|いいえ|はい|  
|フレーム単位のアニメーション|インスタンス単位|いいえ|該当なし|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>ストーリー ボード アニメーション  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]でアニメーション<xref:System.Windows.Media.Animation.Storyboard>を定義および適用する場合は、 アニメーションの開始後にアニメーションを対話的に制御したり、アニメーションの複雑なツリーを作成したり、 または で<xref:System.Windows.Controls.ControlTemplate>アニメーション<xref:System.Windows.Style>を作成<xref:System.Windows.DataTemplate>したりする場合に使用します。 によってアニメーション化<xref:System.Windows.Media.Animation.Storyboard>されるオブジェクトを、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>または を設定<xref:System.Windows.FrameworkElement>するためには、 または を使用する必要<xref:System.Windows.FrameworkContentElement>があります。 詳しくは、「[ストーリーボードの概要](storyboards-overview.md)」をご覧ください。  
  
 A<xref:System.Windows.Media.Animation.Storyboard>は、含まれているアニメーション<xref:System.Windows.Media.Animation.Timeline>のターゲット情報を提供する特殊な種類のコンテナーです。 でアニメーションを作成<xref:System.Windows.Media.Animation.Storyboard>するには、次の 3 つの手順を実行します。  
  
1. および<xref:System.Windows.Media.Animation.Storyboard>1 つ以上のアニメーションを宣言します。  
  
2. および<xref:System.Windows.Media.Animation.Storyboard.TargetProperty><xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>添付プロパティを使用して、各アニメーションのターゲット オブジェクトとプロパティを指定します。  
  
3. (コードのみ)または の を<xref:System.Windows.NameScope>定義します。 <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.FrameworkElement> オブジェクトの名前を登録して、そのオブジェクトをアニメーション化<xref:System.Windows.FrameworkElement>するか<xref:System.Windows.FrameworkContentElement>、または でアニメーション化します。  
  
4. を開始<xref:System.Windows.Media.Animation.Storyboard>します。  
  
 アニメーションを<xref:System.Windows.Media.Animation.Storyboard>開始してアニメーションを作成し、開始するプロパティに適用します。 開始<xref:System.Windows.Media.Animation.Storyboard>するには、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A><xref:System.Windows.Media.Animation.Storyboard>クラスで提供されるメソッドを使用するか、アクションを使用するかの 2 つの方法があります<xref:System.Windows.Media.Animation.BeginStoryboard>。 アニメーションを作成する唯一の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]方法は、アクションを<xref:System.Windows.Media.Animation.BeginStoryboard>使用することです。 アクション<xref:System.Windows.Media.Animation.BeginStoryboard>は<xref:System.Windows.EventTrigger>、 <xref:System.Windows.Trigger>、 プロパティ 、 または<xref:System.Windows.DataTrigger>で使用できます。  
  
 次の表は、各<xref:System.Windows.Media.Animation.Storyboard>開始テクニックがサポートされるさまざまな場所(インスタンス単位、スタイル、コントロール テンプレート、データ テンプレート)を示しています。  
  
|ストーリーボードが開始される場所|インスタンス単位|Style|コントロール テンプレート|データ テンプレート|例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>と<xref:System.Windows.EventTrigger>|はい|はい|はい|はい|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>そして、プロパティ<xref:System.Windows.Trigger>|いいえ|はい|はい|はい|[プロパティ値が変化したときにアニメーションをトリガーする](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>および<xref:System.Windows.DataTrigger>|いいえ|はい|はい|はい|[方法: データが変化したときにアニメーションをトリガーする](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|はい|いいえ|いいえ|いいえ|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 オブジェクトの<xref:System.Windows.Media.Animation.Storyboard>詳細については、「[ストーリーボードの概要](storyboards-overview.md)」を参照してください。  
  
## <a name="local-animations"></a>ローカル アニメーション  
 ローカル アニメーションを使用すると、任意のオブジェクトの依存関係プロパティをアニメーション化<xref:System.Windows.Media.Animation.Animatable>できます。 プロパティに適用するアニメーションが 1 つだけであり、アニメーションを開始後に対話的に制御する必要がない場合は、ローカル アニメーションを使用します。 アニメーションと<xref:System.Windows.Media.Animation.Storyboard>は異なり、ローカル アニメーションでは、<xref:System.Windows.FrameworkElement>または に関連付けられていないオブジェクトをアニメーション化<xref:System.Windows.FrameworkContentElement>できます。 また、この種類のアニメーションに対して<xref:System.Windows.NameScope>を定義する必要はありません。  
  
 ローカル アニメーションはコードだけで使用できます。スタイル、コントロール テンプレート、またはデータ テンプレート内では定義できません。 ローカル アニメーションは、開始後に対話的に制御できません。  
  
 ローカル アニメーションを使用してアニメーション化するには、次の手順を実行します。  
  
1. オブジェクトを<xref:System.Windows.Media.Animation.AnimationTimeline>作成します。  
  
2. アニメーション化<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>するオブジェクトのメソッドを使用して、指定したプロパティ<xref:System.Windows.Media.Animation.AnimationTimeline>に を適用します。  
  
 次の例は、 の幅と背景色をアニメーション化する方法を<xref:System.Windows.Controls.Button>示しています。  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>クロック アニメーション  
 オブジェクト<xref:System.Windows.Media.MediaPlayer.Clock%2A>を使用せずにアニメーション化する場合に、複雑な<xref:System.Windows.Media.Animation.Storyboard>タイミング ツリーを作成したり、開始後にアニメーションを対話的に制御したりする場合に使用します。 Clock オブジェクトを使用して、任意<xref:System.Windows.Media.Animation.Animatable>のオブジェクトの依存関係プロパティをアニメーション化できます。  
  
 <xref:System.Windows.Media.Animation.Clock>スタイル、コントロール テンプレート、またはデータ テンプレートでオブジェクトを直接アニメーション化することはできません。 (アニメーションとタイミング システムでは、実際<xref:System.Windows.Media.Animation.Clock>にはオブジェクトを使用してスタイル、コントロール テンプレート、およびデータ テンプレートをアニメーション化しますが<xref:System.Windows.Media.Animation.Clock>、これらのオブジェクトは<xref:System.Windows.Media.Animation.Storyboard>. オブジェクトとオブジェクトの関係<xref:System.Windows.Media.Animation.Storyboard>の詳細については、「<xref:System.Windows.Media.Animation.Clock>[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)」を参照してください)。  
  
 単一<xref:System.Windows.Media.Animation.Clock>のプロパティを適用するには、次の手順を実行します。  
  
1. オブジェクトを<xref:System.Windows.Media.Animation.AnimationTimeline>作成します。  
  
2. のメソッド<xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A>を<xref:System.Windows.Media.Animation.AnimationTimeline>使用して を作成<xref:System.Windows.Media.Animation.AnimationClock>します。  
  
3. アニメーション化<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>するオブジェクトのメソッドを使用して、指定したプロパティ<xref:System.Windows.Media.Animation.AnimationClock>に を適用します。  
  
 を作成し、2 つの類似<xref:System.Windows.Media.Animation.AnimationClock>したプロパティに適用する方法を次の例に示します。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 タイミング ツリーを作成し、これを使用してプロパティをアニメーション化するには、次の手順を実行します。  
  
1. タイミング<xref:System.Windows.Media.Animation.ParallelTimeline><xref:System.Windows.Media.Animation.AnimationTimeline>ツリーを作成するには、 と オブジェクトを使用します。  
  
2. ルート<xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A><xref:System.Windows.Media.Animation.ParallelTimeline>の を使用して を<xref:System.Windows.Media.Animation.ClockGroup>作成します。  
  
3. <xref:System.Windows.Media.Animation.ClockGroup.Children%2A>のを反復処理<xref:System.Windows.Media.Animation.ClockGroup>し、その子<xref:System.Windows.Media.Animation.Clock>オブジェクトを適用します。 子ごとに<xref:System.Windows.Media.Animation.AnimationClock>、アニメーション化する<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>オブジェクトのメソッドを使用して、指定したプロパティ<xref:System.Windows.Media.Animation.AnimationClock>に適用します。  
  
 Clock オブジェクトについて詳しくは、「[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)」をご覧ください。  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>フレーム単位アニメーション: アニメーションとタイミング システムのバイパス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要があるときは、この方法を使います。 この方法の 1 つのシナリオは、アニメーションの各ステップで、オブジェクトの最後の一連のやり取りに基づいてオブジェクトの再計算が必要になる物理アニメーションです。  
  
 フレーム単位アニメーションは、スタイル、コントロール テンプレート、またはデータ テンプレート内で定義できません。  
  
 フレームごとにアニメーションを作成するには、アニメーション化するオブジェクトを<xref:System.Windows.Media.CompositionTarget.Rendering>含むオブジェクトのイベントに登録します。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームのプレゼンテーション時間を取得するには、この<xref:System.EventArgs>イベントに関連付けられた をとして<xref:System.Windows.Media.RenderingEventArgs>キャストして、現在<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>のフレームのレンダリング時間を取得するために使用できるプロパティを提供します。  
  
 詳しくは、<xref:System.Windows.Media.CompositionTarget.Rendering> のページをご覧ください。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [依存関係プロパティの概要](../advanced/dependency-properties-overview.md)

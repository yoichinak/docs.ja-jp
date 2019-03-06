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
ms.openlocfilehash: b03c450b84a376de5c5c7d3582c01a31bc417a11
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366778"
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
|ストーリー ボード アニメーション|インスタンスごとの<xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、 <xref:System.Windows.DataTemplate>|[はい]|[はい]|  
|ローカル アニメーション|インスタンス単位|いいえ|いいえ|  
|クロック アニメーション|インスタンス単位|いいえ|[はい]|  
|フレーム単位のアニメーション|インスタンス単位|いいえ|N/A|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>ストーリー ボード アニメーション  
 使用して、<xref:System.Windows.Media.Animation.Storyboard>を定義し、アニメーションを適用する場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]対話形式で、開始、アニメーションの複雑なツリーを作成またはでアニメーション化した後に、アニメーションを制御、 <xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate>または<xref:System.Windows.DataTemplate>します。 によってアニメーション化するオブジェクトの<xref:System.Windows.Media.Animation.Storyboard>、する必要があります、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>、設定するために使用する必要がありますか、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 詳しくは、「[ストーリーボードの概要](storyboards-overview.md)」をご覧ください。  
  
 A<xref:System.Windows.Media.Animation.Storyboard>特殊な種類のコンテナーは、<xref:System.Windows.Media.Animation.Timeline>が含まれているアニメーションのターゲットの情報を提供します。 使用してアニメーション化、 <xref:System.Windows.Media.Animation.Storyboard>、次の 3 つの手順を完了します。  
  
1.  宣言を<xref:System.Windows.Media.Animation.Storyboard>と 1 つまたは複数のアニメーション。  
  
2.  使用して、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>ターゲット オブジェクトを指定するプロパティとそれぞれのアニメーションのプロパティをアタッチします。  
  
3.  (コードのみ)定義、<xref:System.Windows.NameScope>の<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 使用してアニメーション化するオブジェクトの名前を登録<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。  
  
4.  開始、<xref:System.Windows.Media.Animation.Storyboard>します。  
  
 以降、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化するプロパティにアニメーションを適用し、それらを開始します。 開始する 2 つの方法がある、 <xref:System.Windows.Media.Animation.Storyboard>: 使用することができます、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドによって提供される、<xref:System.Windows.Media.Animation.Storyboard>クラス、またはを使用できる、<xref:System.Windows.Media.Animation.BeginStoryboard>アクション。 唯一の方法でアニメーション化する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、<xref:System.Windows.Media.Animation.BeginStoryboard>アクション。 A<xref:System.Windows.Media.Animation.BeginStoryboard>でアクションを使用できます、 <xref:System.Windows.EventTrigger>、プロパティ<xref:System.Windows.Trigger>、または<xref:System.Windows.DataTrigger>します。  
  
 次の表に、さまざまな場所を各<xref:System.Windows.Media.Animation.Storyboard>開始手法がサポートされています: インスタンス単位、スタイル、コントロール テンプレート、およびデータ テンプレート。  
  
|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.EventTrigger>|[はい]|はい|はい|[はい]|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> プロパティと、 <xref:System.Windows.Trigger>|いいえ|[はい]|はい|[はい]|[プロパティ値が変化したときにアニメーションをトリガーする](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.DataTrigger>|いいえ|[はい]|はい|[はい]|[方法: データが変更されたときにアニメーションをトリガーします。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|[はい]|×|×|いいえ|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 詳細については<xref:System.Windows.Media.Animation.Storyboard>、オブジェクトを参照してください、[ストーリー ボードの概要](storyboards-overview.md)します。  
  
## <a name="local-animations"></a>ローカル アニメーション  
 ローカル アニメーションは、いずれかの依存関係プロパティをアニメーション化する便利な手段を提供<xref:System.Windows.Media.Animation.Animatable>オブジェクト。 プロパティに適用するアニメーションが 1 つだけであり、アニメーションを開始後に対話的に制御する必要がない場合は、ローカル アニメーションを使用します。 異なり、<xref:System.Windows.Media.Animation.Storyboard>アニメーション、ローカル アニメーションに関連付けられていないオブジェクトのアニメーションできます、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 定義することも必要はありません、<xref:System.Windows.NameScope>この種類のアニメーション。  
  
 ローカル アニメーションはコードだけで使用できます。スタイル、コントロール テンプレート、またはデータ テンプレート内では定義できません。 ローカル アニメーションは、開始後に対話的に制御できません。  
  
 ローカル アニメーションを使用してアニメーション化するには、次の手順を実行します。  
  
1.  作成、<xref:System.Windows.Media.Animation.AnimationTimeline>オブジェクト。  
  
2.  使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>を適用するアニメーション化するオブジェクトのメソッド、<xref:System.Windows.Media.Animation.AnimationTimeline>を指定するプロパティ。  
  
 次の例の幅と背景色をアニメーション化する方法を示しています、<xref:System.Windows.Controls.Button>します。  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>クロック アニメーション  
 使用<xref:System.Windows.Media.MediaPlayer.Clock%2A>オブジェクトを使用せずにアニメーション化するときに、<xref:System.Windows.Media.Animation.Storyboard>複雑なタイミング ツリーを作成または起動後に、アニメーションを対話的に制御したいとします。 Clock オブジェクトを使用するには任意の依存関係プロパティをアニメーション化<xref:System.Windows.Media.Animation.Animatable>オブジェクト。  
  
 使用することはできません<xref:System.Windows.Media.Animation.Clock>テンプレート、またはデータ テンプレートに、直接、スタイルのアニメーション化するコントロールにオブジェクト。 (実際にアニメーションとタイミング システムを使用して<xref:System.Windows.Media.Animation.Clock>それでは、スタイル、コントロール テンプレート、およびデータのテンプレートが、アニメーション化するオブジェクトを作成する必要があります<xref:System.Windows.Media.Animation.Clock>からオブジェクトを<xref:System.Windows.Media.Animation.Storyboard>します。 間のリレーションシップの詳細については<xref:System.Windows.Media.Animation.Storyboard>オブジェクトと<xref:System.Windows.Media.Animation.Clock>、オブジェクトを参照してください、[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md))。  
  
 1 つを適用する<xref:System.Windows.Media.Animation.Clock>プロパティには、次の手順を完了します。  
  
1.  作成、<xref:System.Windows.Media.Animation.AnimationTimeline>オブジェクト。  
  
2.  使用して、<xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A>のメソッド、<xref:System.Windows.Media.Animation.AnimationTimeline>を作成する、<xref:System.Windows.Media.Animation.AnimationClock>します。  
  
3.  使用して、<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>を適用するアニメーション化するオブジェクトのメソッド、<xref:System.Windows.Media.Animation.AnimationClock>を指定するプロパティ。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Media.Animation.AnimationClock>同様の 2 つのプロパティに適用されます。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 タイミング ツリーを作成し、これを使用してプロパティをアニメーション化するには、次の手順を実行します。  
  
1.  使用<xref:System.Windows.Media.Animation.ParallelTimeline>と<xref:System.Windows.Media.Animation.AnimationTimeline>タイミング ツリーを作成するオブジェクト。  
  
2.  使用して、<xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A>ルートの<xref:System.Windows.Media.Animation.ParallelTimeline>を作成する、<xref:System.Windows.Media.Animation.ClockGroup>します。  
  
3.  反復処理、<xref:System.Windows.Media.Animation.ClockGroup.Children%2A>の<xref:System.Windows.Media.Animation.ClockGroup>し、その子を適用<xref:System.Windows.Media.Animation.Clock>オブジェクト。 各<xref:System.Windows.Media.Animation.AnimationClock>子を使用して、<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>を適用するアニメーション化するオブジェクトのメソッド、<xref:System.Windows.Media.Animation.AnimationClock>プロパティを指定します。  
  
 Clock オブジェクトについて詳しくは、「[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)」をご覧ください。  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>フレーム単位アニメーション:アニメーションとタイミング システムをバイパスします。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要があるときは、この方法を使います。 この方法の 1 つのシナリオは、アニメーションの各ステップで、オブジェクトの最後の一連のやり取りに基づいてオブジェクトの再計算が必要になる物理アニメーションです。  
  
 フレーム単位アニメーションは、スタイル、コントロール テンプレート、またはデータ テンプレート内で定義できません。  
  
 登録のフレームに、アニメーション化する、<xref:System.Windows.Media.CompositionTarget.Rendering>をアニメーション化するオブジェクトを含むオブジェクトのイベント。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームの表現時間を取得する、<xref:System.EventArgs>これに関連付けられているイベントとしてキャストできる<xref:System.Windows.Media.RenderingEventArgs>、提供、<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>現在のフレームを取得するのに使用できるプロパティの表示時間。  
  
 詳細については、次を参照してください。、<xref:System.Windows.Media.CompositionTarget.Rendering>ページ。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [依存関係プロパティの概要](../advanced/dependency-properties-overview.md)

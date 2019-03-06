---
title: アニメーションとタイミング システムの概要
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: 36a71213b2c96d2ea1aa7597216f420f47493f43
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360512"
---
# <a name="animation-and-timing-system-overview"></a>アニメーションとタイミング システムの概要
このトピックでは、タイミング システムが、アニメーションを使用する方法について説明します<xref:System.Windows.Media.Animation.Timeline>、および<xref:System.Windows.Media.Animation.Clock>プロパティをアニメーション化するクラス。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、「[アニメーションの概要](animation-overview.md)」で説明されているように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーションを使ってプロパティをアニメーション化できる必要があります。 依存関係プロパティの理解も役に立ちます。詳しくは、「[依存関係プロパティの概要](../advanced/dependency-properties-overview.md)」をご覧ください。  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>タイムラインとクロック  
 [アニメーションの概要](animation-overview.md)方法の説明、<xref:System.Windows.Media.Animation.Timeline>表します時刻、およびアニメーションのセグメントの種類は、<xref:System.Windows.Media.Animation.Timeline>出力値を生成します。 単独で、 <xref:System.Windows.Media.Animation.Timeline>、以外の何も実行時間のセグメントを記述するだけです。 タイムラインの<xref:System.Windows.Media.Animation.Clock>実際の処理を行うオブジェクト。 同様に、アニメーションは実際にアニメーション化するプロパティ。 アニメーション クラスは、出力値の計算方法について説明しますが、<xref:System.Windows.Media.Animation.Clock>アニメーションの出力を駆動し、それをプロパティに適用するアニメーション用に作成されました。  
  
 A<xref:System.Windows.Media.Animation.Clock>は特殊な種類の実行時のタイミングに関連する状態を保持するオブジェクトの<xref:System.Windows.Media.Animation.Timeline>します。 アニメーションとタイミング システムに不可欠な情報の 3 つのビットを提供します。 <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>、 <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>、および<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>します。 A<xref:System.Windows.Media.Animation.Clock>で記述されるタイミング動作を使用して、現在の時刻、進行状況、および状態を判断します。 その<xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>など。  
  
 ほとんどの場合、<xref:System.Windows.Media.Animation.Clock>タイムラインに対して自動的に作成されます。 使用してアニメーション化するときに、<xref:System.Windows.Media.Animation.Storyboard>または<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッド、クロックが自動的に、タイムラインとアニメーションの作成し、対象のプロパティに適用します。 作成することも、<xref:System.Windows.Media.Animation.Clock>を使用して明示的に、<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>のメソッド、<xref:System.Windows.Media.Animation.Timeline>します。 <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType>メソッドの適切な型のクロックを作成する、<xref:System.Windows.Media.Animation.Timeline>でが呼び出されます。 場合、<xref:System.Windows.Media.Animation.Timeline>子のタイムラインを含む作成<xref:System.Windows.Media.Animation.Clock>もそれらのオブジェクト。 結果の<xref:System.Windows.Media.Animation.Clock>の構造と一致するツリー オブジェクトの配置、<xref:System.Windows.Media.Animation.Timeline>オブジェクトのツリーから作成されます。  
  
 異なる型のタイムラインに対して異なる型のクロックがあります。 次の表は、 <xref:System.Windows.Media.Animation.Clock> 、別の一部に対応する型<xref:System.Windows.Media.Animation.Timeline>型。  
  
|タイムラインの型|クロックの型|クロックの目的|  
|-------------------|----------------|-------------------|  
|アニメーション (から継承<xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|依存関係プロパティの出力値を生成します。|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|メディア ファイルを処理します。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|グループ化してその子の制御<xref:System.Windows.Media.Animation.Clock>オブジェクト|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|グループ化してその子の制御<xref:System.Windows.Media.Animation.Clock>オブジェクト|  
  
 適用することはできます<xref:System.Windows.Media.Animation.AnimationClock>オブジェクトを使用して互換性のある依存関係プロパティを作成する、<xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A>メソッド。  
  
 多数の類似のオブジェクトをアニメーション化など、負荷の高いシナリオで管理独自<xref:System.Windows.Media.Animation.Clock>使用はパフォーマンス上の利点を提供できます。  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>クロックとタイム マネージャー  
 内のオブジェクトをアニメーション化するときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、管理するタイム マネージャーは、<xref:System.Windows.Media.MediaPlayer.Clock%2A>タイムラインに対して作成されたオブジェクト。 タイム マネージャーは <xref:System.Windows.Media.MediaPlayer.Clock%2A> オブジェクトのツリーのルートで、そのツリー内の時間の流れを制御します。  タイム マネージャーは各 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに自動的に作成され、アプリケーション開発者には表示されません。 タイム マネージャーは 1 秒間に何度も "タイマーを刻み" ます。1 秒ごとに刻まれるタイマーの実際の数は、使用可能なシステム リソースによって異なります。 これらのタイマー刻みのそれぞれの中に、タイム マネージャーはすべての状態を計算します<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>タイミング ツリー内のオブジェクト。  
  
 次の図は、タイム マネージャー間のリレーションシップと<xref:System.Windows.Media.Animation.AnimationClock>、およびアニメーション化された依存関係プロパティ。  
  
 ![タイミング システム コンポーネント](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
プロパティのアニメーション化  
  
 時刻が更新されますが、タイム マネージャー、タイマーを刻むときにすべて<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>アプリケーションにします。 場合、<xref:System.Windows.Media.Animation.Clock>は、<xref:System.Windows.Media.Animation.AnimationClock>を使用して、<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>のメソッド、<xref:System.Windows.Media.Animation.AnimationTimeline>から作成された、現在の計算の出力値。 <xref:System.Windows.Media.Animation.AnimationClock>提供、<xref:System.Windows.Media.Animation.AnimationTimeline>現在の現地時刻、これは、プロパティの基本値では通常、入力の値と既定の終了値。 アニメーション化された値を取得するプロパティを使用して、<xref:System.Windows.DependencyObject.GetValue%2A>の出力を取得するメソッドまたはその CLR アクセサーでは、その<xref:System.Windows.Media.Animation.AnimationClock>します。  
  
#### <a name="clock-groups"></a>クロック グループ  
 前のセクションでは、さまざまな種類の方法が説明されている<xref:System.Windows.Media.Animation.Clock>タイムラインのさまざまな種類のオブジェクト。 次の図は、タイム マネージャー間のリレーションシップを<xref:System.Windows.Media.Animation.ClockGroup>、 <xref:System.Windows.Media.Animation.AnimationClock>、およびアニメーション化された依存関係プロパティ。 A<xref:System.Windows.Media.Animation.ClockGroup>など、他のタイムラインをグループ化するタイムラインに対して作成、<xref:System.Windows.Media.Animation.Storyboard>クラスは、アニメーションやその他のタイムラインをグループ化します。  
  
 ![タイミング システム コンポーネント](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>コンポジション  
 複数のクロックを 1 つのプロパティと関連付けることができます。その場合、各クロックは前のクロックの出力値を基本値として使います。 次の図は 3 つ<xref:System.Windows.Media.Animation.AnimationClock>同じプロパティに適用されるオブジェクト。 Clock1 は、アニメーション化されたプロパティの基本値を入力として使って、出力を生成します。 Clock2 は、Clock1 の出力を入力として受け取り、それを使って出力を生成します。 Clock3 は、Clock2 の出力を入力として受け取り、それを使って出力を生成します。 複数のクロックが同じプロパティに同時に影響を与える場合、それらはコンポジション チェーン内にあると言います。  
  
 ![タイミング システム コンポーネント](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
コンポジション チェーン  
  
 入力と出力の間でリレーションシップを作成するが、 <xref:System.Windows.Media.Animation.AnimationClock> 、コンポジション チェーン内でオブジェクトをそれらのタイミング動作が影響を受けません。<xref:System.Windows.Media.Animation.Clock>オブジェクト (を含む<xref:System.Windows.Media.Animation.AnimationClock>オブジェクト)、親の階層型依存関係のある<xref:System.Windows.Media.Animation.Clock>オブジェクト。  
  
 同じプロパティには、複数のクロックを適用するには、使用、 <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>適用するときに、 <xref:System.Windows.Media.Animation.Storyboard>、アニメーション、または<xref:System.Windows.Media.Animation.AnimationClock>します。  
  
#### <a name="ticks-and-event-consolidation"></a>ティックとイベントの統合  
 出力値を計算するだけでなく、タイム マネージャーはティックのたびに他の処理を行います。つまり、クロックの状態を判断し、必要に応じてイベントを発生させます。  
  
 ティックは頻繁に発生しますが、各ティックの間には多くのことが起こる可能性があります。 たとえば、<xref:System.Windows.Media.Animation.Clock>停止、開始、およびその場合、もう一度停止可能性があります、<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>値は 3 回変更があります。 理論的には、<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>イベントは、単一のティックで複数回発生可能性があります。 ただし、タイミング エンジンは、イベントを統合できるように、<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>ティックあたり最大で 1 回はイベントを発生させることができます。 これは、すべてのタイミング イベントの場合は true: の各型の最大で 1 つのイベントが発生した、指定された<xref:System.Windows.Media.Animation.Clock>オブジェクト。  
  
 ときに、<xref:System.Windows.Media.Animation.Clock>状態を切り替え、元の状態にティック間を返します (からの変更など<xref:System.Windows.Media.Animation.ClockState.Active>に<xref:System.Windows.Media.Animation.ClockState.Stopped>に戻すと<xref:System.Windows.Media.Animation.ClockState.Active>)、関連付けられたイベントが引き続き発生します。  
  
 タイミング イベントについて詳しくは、「[タイミング イベントの概要](timing-events-overview.md)」をご覧ください。  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>プロパティの現在値と基本値  
 アニメーション化可能なプロパティは、基本値と現在値の 2 つの値を持つことができます。 CLR アクセサーを使用してプロパティを設定すると、または<xref:System.Windows.DependencyObject.SetValue%2A>メソッド、その基本値を設定します。 プロパティがアニメーション化されない場合は、基本値と現在値は同じです。  
  
 プロパティをアニメーション化すると、<xref:System.Windows.Media.Animation.AnimationClock>プロパティの設定*現在*値。 CLR アクセサーを使用して、プロパティの値を取得または<xref:System.Windows.DependencyObject.GetValue%2A>メソッドの出力を返します、<xref:System.Windows.Media.Animation.AnimationClock>ときに、<xref:System.Windows.Media.Animation.AnimationClock>は<xref:System.Windows.Media.Animation.ClockState.Active>または<xref:System.Windows.Media.Animation.ClockState.Filling>します。 使用してプロパティの基本値を取得することができます、<xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A>メソッド。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [タイミング イベントの概要](timing-events-overview.md)
- [タイミング動作の概要](timing-behaviors-overview.md)

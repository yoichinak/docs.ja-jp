---
title: アニメーションとタイミング システムの概要
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187716"
---
# <a name="animation-and-timing-system-overview"></a>アニメーションとタイミング システムの概要
このトピックでは、タイミング システムでアニメーション、<xref:System.Windows.Media.Animation.Timeline>および クラス<xref:System.Windows.Media.Animation.Clock>を使用してプロパティをアニメーション化する方法について説明します。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、「[アニメーションの概要](animation-overview.md)」で説明されているように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーションを使ってプロパティをアニメーション化できる必要があります。 依存関係プロパティの理解も役に立ちます。詳しくは、「[依存関係プロパティの概要](../advanced/dependency-properties-overview.md)」をご覧ください。  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>タイムラインとクロック  
 [アニメーションの概要](animation-overview.md)では、a<xref:System.Windows.Media.Animation.Timeline>が時間のセグメントを表す方法を説明し、<xref:System.Windows.Media.Animation.Timeline>アニメーションは出力値を生成するタイプです。 それ自体では、<xref:System.Windows.Media.Animation.Timeline>時間のセグメントを記述する以外に何もしません。 実際の作業を行うタイムライン<xref:System.Windows.Media.Animation.Clock>のオブジェクトです。 同様に、アニメーションは実際にはプロパティをアニメーション化しません: アニメーション クラスは出力値の計算方法を記述しますが、アニメーション出力<xref:System.Windows.Media.Animation.Clock>を駆動してプロパティに適用するのはアニメーション用に作成されたものです。  
  
 A<xref:System.Windows.Media.Animation.Clock>は、タイミング関連の実行時状態を保持する特殊なタイプのオブジェクトです<xref:System.Windows.Media.Animation.Timeline>。 アニメーションおよびタイミング システムに不可欠な 3 ビットの情報<xref:System.Windows.Media.Animation.Clock.CurrentTime%2A><xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>を提供します。 <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> A<xref:System.Windows.Media.Animation.Clock>は、 <xref:System.Windows.Media.Animation.Timeline>、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 、、などで説明されているタイミング動作を使用して、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>現在<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>の時刻、進行状況、および状態を判断します。  
  
 ほとんどの場合、タイムラインに<xref:System.Windows.Media.Animation.Clock>対して は自動的に作成されます。 <xref:System.Windows.Media.Animation.Storyboard>または メソッドを使用してアニメーションを作成すると、タイムラインとアニメーションに対してクロックが自動的に作成され、対象のプロパティに適用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>されます。 の メソッドを<xref:System.Windows.Media.Animation.Clock>使用して明示的に<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>作成することもできます。 <xref:System.Windows.Media.Animation.Timeline> この<xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType>メソッドは、呼び出されるに適した<xref:System.Windows.Media.Animation.Timeline>型のクロックを作成します。 子タイムライン<xref:System.Windows.Media.Animation.Timeline>が含まれている場合は、子<xref:System.Windows.Media.Animation.Clock>タイムラインのオブジェクトも作成されます。 生成された<xref:System.Windows.Media.Animation.Clock>オブジェクトは、作成元のオブジェクトツリーの構造に<xref:System.Windows.Media.Animation.Timeline>一致するツリーに配置されます。  
  
 異なる型のタイムラインに対して異なる型のクロックがあります。 次の表は、<xref:System.Windows.Media.Animation.Clock>いくつかの異なる<xref:System.Windows.Media.Animation.Timeline>型に対応する型を示しています。  
  
|タイムラインの型|クロックの型|クロックの目的|  
|-------------------|----------------|-------------------|  
|アニメーション (継承元<xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|依存関係プロパティの出力値を生成します。|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|メディア ファイルを処理します。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|子<xref:System.Windows.Media.Animation.Clock>オブジェクトをグループ化および制御する|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|子<xref:System.Windows.Media.Animation.Clock>オブジェクトをグループ化および制御する|  
  
 このメソッドを使用<xref:System.Windows.Media.Animation.AnimationClock>して、作成したオブジェクトを互換性のある依存関係プロパティ<xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A>に適用できます。  
  
 多数の類似オブジェクトをアニメーション化するなど、パフォーマンスを重視するシナリオでは、独自<xref:System.Windows.Media.Animation.Clock>の使用を管理するとパフォーマンス上の利点が得られます。  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>クロックとタイム マネージャー  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]オブジェクトをアニメーション化する場合、タイムライン用に作成されたオブジェクトを<xref:System.Windows.Media.MediaPlayer.Clock%2A>管理するのは、時間マネージャです。 タイム マネージャーは <xref:System.Windows.Media.MediaPlayer.Clock%2A> オブジェクトのツリーのルートで、そのツリー内の時間の流れを制御します。  タイム マネージャーは各 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに自動的に作成され、アプリケーション開発者には表示されません。 タイム マネージャーは 1 秒間に何度も "タイマーを刻み" ます。1 秒ごとに刻まれるタイマーの実際の数は、使用可能なシステム リソースによって異なります。 これらのティックの各々の間に、時間マネージャはタイミングツリー内のすべての<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>オブジェクトの状態を計算します。  
  
 次の図は、時間マネージャーと の関係と<xref:System.Windows.Media.Animation.AnimationClock>、アニメーション化された依存関係プロパティを示しています。  
  
 ![タイミング システムのコンポーネント](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
プロパティのアニメーション化  
  
 時間マネージャがチェックすると、アプリケーション<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>内のすべての時間が更新されます。 <xref:System.Windows.Media.Animation.Clock>が<xref:System.Windows.Media.Animation.AnimationClock>の場合は、作成元<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>の メソッド<xref:System.Windows.Media.Animation.AnimationTimeline>を使用して現在の出力値を計算します。 は<xref:System.Windows.Media.Animation.AnimationClock>、現在<xref:System.Windows.Media.Animation.AnimationTimeline>のローカル時間、通常はプロパティの基本値である入力値、およびデフォルトの宛先値を提供します。 メソッドまたはその CLR アクセサーを使用して、アニメーション<xref:System.Windows.DependencyObject.GetValue%2A>化されたプロパティの値を取得すると、その<xref:System.Windows.Media.Animation.AnimationClock>出力が取得されます。  
  
#### <a name="clock-groups"></a>クロック グループ  
 前のセクションでは、さまざまな種類のタイムラインに<xref:System.Windows.Media.Animation.Clock>対して、さまざまな種類のオブジェクトがどのように存在するかを説明しました。 次の図は、時間マネージャ<xref:System.Windows.Media.Animation.ClockGroup>、、、a 、および<xref:System.Windows.Media.Animation.AnimationClock>アニメーション化された依存関係プロパティの関係を示しています。 A<xref:System.Windows.Media.Animation.ClockGroup>は、アニメーションやその他のタイムラインをグループ化するクラスなど<xref:System.Windows.Media.Animation.Storyboard>、他のタイムラインをグループ化するタイムラインに対して作成されます。  
  
 ![タイミング システムのコンポーネント](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>構成  
 複数のクロックを 1 つのプロパティと関連付けることができます。その場合、各クロックは前のクロックの出力値を基本値として使います。 次の図は、<xref:System.Windows.Media.Animation.AnimationClock>同じプロパティに適用される 3 つのオブジェクトを示しています。 Clock1 は、アニメーション化されたプロパティの基本値を入力として使って、出力を生成します。 Clock2 は、Clock1 の出力を入力として受け取り、それを使って出力を生成します。 Clock3 は、Clock2 の出力を入力として受け取り、それを使って出力を生成します。 複数のクロックが同じプロパティに同時に影響を与える場合、それらはコンポジション チェーン内にあると言います。  
  
 ![タイミング システムのコンポーネント](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
コンポジション チェーン  
  
 コンポジションチェーン内の<xref:System.Windows.Media.Animation.AnimationClock>オブジェクトの入出力間でリレーションシップが作成されますが、タイミングの動作は影響を受けません。<xref:System.Windows.Media.Animation.Clock>オブジェクト (<xref:System.Windows.Media.Animation.AnimationClock>オブジェクトを含む) は、親<xref:System.Windows.Media.Animation.Clock>オブジェクトに対して階層的な依存関係を持ちます。  
  
 同じプロパティに複数のクロックを適用するには、<xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior><xref:System.Windows.Media.Animation.Storyboard>アニメーションまたは を適用するときに を<xref:System.Windows.Media.Animation.AnimationClock>使用します。  
  
#### <a name="ticks-and-event-consolidation"></a>ティックとイベントの統合  
 出力値を計算するだけでなく、タイム マネージャーはティックのたびに他の処理を行います。つまり、クロックの状態を判断し、必要に応じてイベントを発生させます。  
  
 ティックは頻繁に発生しますが、各ティックの間には多くのことが起こる可能性があります。 たとえば、a<xref:System.Windows.Media.Animation.Clock>を停止、開始、および停止した場合、その<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>値は 3 回変更されます。 理論的には、イベント<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>は 1 つのティックで複数回発生する可能性があります。ただし、タイミング エンジンはイベントを統合するため、イベント<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>は 1 ティックあたりせいぜい 1 回発生できます。 これはすべてのタイミングイベントに当てはまります: 各タイプのイベントは、指定された<xref:System.Windows.Media.Animation.Clock>オブジェクトに対して 1 つでも発生します。  
  
 切り替えが状態を切り替えて、ティック間の元の状態に戻<xref:System.Windows.Media.Animation.ClockState.Active>っても<xref:System.Windows.Media.Animation.ClockState.Stopped>(変更された<xref:System.Windows.Media.Animation.ClockState.Active>状態から戻り値へ)、関連付けられたイベントは引き続き発生します。 <xref:System.Windows.Media.Animation.Clock>  
  
 タイミング イベントについて詳しくは、「[タイミング イベントの概要](timing-events-overview.md)」をご覧ください。  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>プロパティの現在値と基本値  
 アニメーション化可能なプロパティは、基本値と現在値の 2 つの値を持つことができます。 CLR アクセサーまたはメソッドを使用してプロパティ<xref:System.Windows.DependencyObject.SetValue%2A>を設定する場合は、その基本値を設定します。 プロパティがアニメーション化されない場合は、基本値と現在値は同じです。  
  
 プロパティをアニメーション化すると、プロパティの<xref:System.Windows.Media.Animation.AnimationClock>*現在*の値が設定されます。 CLR アクセサーまたはメソッドを使用してプロパティの値を<xref:System.Windows.DependencyObject.GetValue%2A>取得すると<xref:System.Windows.Media.Animation.AnimationClock>、 または<xref:System.Windows.Media.Animation.AnimationClock><xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.ClockState.Filling>がの場合の出力が返されます。 メソッドを使用して、プロパティの基本値を<xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A>取得できます。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [タイミング イベントの概要](timing-events-overview.md)
- [タイミング動作の概要](timing-behaviors-overview.md)

---
title: タイミング イベントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: ee45441e9ad09c60d8b61ecce4ef08b0027ce29e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145411"
---
# <a name="timing-events-overview"></a>タイミング イベントの概要
このトピックでは、使用可能な 5 つのタイミング イベント<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>オブジェクトの使用方法について説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、アニメーションの作成方法と使用方法について理解している必要があります。 アニメーションの使用を開始するには、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 でプロパティをアニメーション化する方法は複数あります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
- **ストーリーボード オブジェクト**(マークアップとコード) を<xref:System.Windows.Media.Animation.Storyboard>使用する: オブジェクトを使用して、アニメーションを 1 つまたは複数のオブジェクトに配置および配布できます。 例については、「[ストーリーボードを使用してプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)」を参照してください。  
  
- **ローカル アニメーションを使用**する(コードのみ):<xref:System.Windows.Media.Animation.AnimationTimeline>オブジェクトをアニメーション化するプロパティに直接適用できます。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
- **クロックを使用する**(コードのみ): クロックを明示的に作成し、アニメーション クロックを自分で均等配置することができます。  例については、「[アニメーション時計を使用してプロパティをアニメーション化する](how-to-animate-a-property-by-using-an-animationclock.md)」を参照してください。  
  
 マークアップやコードで使用できるため、この概要の例ではオブジェクトを使用<xref:System.Windows.Media.Animation.Storyboard>します。 ただし、説明されている概念は、プロパティをアニメーション化するためのその他の方法にも適用できます。  
  
### <a name="what-is-a-clock"></a>クロックとは  
 タイムラインは、時間のセグメントについて説明する以外は、それ自身が実際に何かを行うものではありません。 実際の作業を行うタイムライン<xref:System.Windows.Media.Animation.Clock>のオブジェクトで、タイムラインのタイミング関連の実行時状態を維持します。 多くの場合(ストーリー ボードを使用する場合など)には、タイムラインに対してクロックが自動的に作成されます。 メソッドを<xref:System.Windows.Media.Animation.Clock>使用<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>して明示的に作成することもできます。 オブジェクトの<xref:System.Windows.Media.Animation.Clock>詳細については、「[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)」を参照してください。  
  
## <a name="why-use-events"></a>イベントを使用する理由  
 1 つの例外 (最後のティックに配置されたシーク) を除いて、すべての対話型タイミング操作は非同期です。 これらがいつ実行されるかを正確に知る方法はありません。 これは、タイミング操作に依存する他のコードが存在する場合に、問題となることがあります。 たとえば、四角形をアニメーション化するタイムラインを停止する必要があるとします。 そしてタイムラインを停止した後に、四角形の色を変更するとします。  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 上記の例では、ストーリー ボードが停止する前に、2 行目のコードが実行される可能性があります。 これは、停止が非同期の操作であるためです。 タイムラインやクロックに停止を指示すると、タイミング エンジンの次のティックまで処理されない「停止要求」が作成されます。  
  
 タイムラインの完了後にコマンドを実行するには、タイミング イベントを使用します。 次の例では、ストーリー ボードが停止した後に四角形の色が変更されるよう、イベント ハンドラーが使用されています。  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 より完全な例については、「[時計の状態が変化したときに通知を受け取る](how-to-receive-notification-when-clock-state-changes.md)」を参照してください。  
  
## <a name="public-events"></a>パブリック イベント  
 クラス<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>クラスは、5 つのタイミング イベントを提供します。 次の表は、これらのイベントと、それらをトリガーする条件を示したものです。  
  
|Event|対話型操作のトリガー|その他のトリガー|  
|-----------|--------------------------------------|--------------------|  
|**完了**|塗りつぶしまでスキップ|時計が完了する。|  
|**CurrentGlobalSpeedInvalidated**|一時停止、再開、シーク、速度比を設定、塗りつぶしまでスキップ、停止|クロックが反転、加速、開始、または停止する。|  
|**CurrentStateInvalidated**|開始、塗りつぶしまでスキップ、停止|クロックが開始、停止、または塗りつぶされる。|  
|**CurrentTimeInvalidated**|開始、シーク、塗りつぶしまでスキップ、停止|クロックが進行する。|  
|**RemoveRequested**|[削除]||  
  
## <a name="ticking-and-event-consolidation"></a>ティッキングとイベントの統合  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]オブジェクトをアニメーション化する場合、アニメーションを管理するタイミング エンジンです。 タイミング エンジンは、時間の進行状況を追跡し、それぞれのアニメーションの状態を計算します。 これにより、多数の評価パスが瞬時に作成されます。 これらの評価パスは「ティック」と呼ばれます。  
  
 ティックは頻繁に発生しますが、各ティックの間には多くのことが起こる可能性があります。 たとえば、タイムラインが停止され、開始され、再度停止された場合、その現行状態は 3 回変更されることになります。 理論上、イベントは 1 つのティックで複数回発生することができますが、タイミング エンジンではイベントが統合されるため、各イベントの発生回数はティックあたり最大で 1回となります。  
  
## <a name="registering-for-events"></a>イベントの登録  
 タイミング イベントを登録する方法は 2 つあります。 タイムラインに登録する方法と、タイムラインから作成されたクロックに登録する方法です。 クロックに直接登録する方法は非常に分かりやすいですが、これはコードからのみ実行できます。 タイムラインに登録する場合は、マークアップまたはコードからイベントを登録できます。 次のセクションでは、クロック イベントをタイムラインに登録する方法について説明します。  
  
<a name="registeringforclockeventswithatimeline"></a>
## <a name="registering-for-clock-events-with-a-timeline"></a>クロック イベントをタイムラインに登録する  
 タイムラインの<xref:System.Windows.Media.Animation.Timeline.Completed>、 、、、、、、<xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated><xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>および<xref:System.Windows.Media.Animation.Timeline.RemoveRequested>イベントはタイムラインに関連付けられているように見えますが、これらのイベントに登録すると、<xref:System.Windows.Media.Animation.Clock>実際にはイベント ハンドラがタイムライン用に作成されたイベント ハンドラに関連付けられます。  
  
 たとえば、タイムラインでイベント<xref:System.Windows.Media.Animation.Timeline.Completed>に登録すると、実際には、タイムライン用に作成された各クロックの<xref:System.Windows.Media.Animation.Clock.Completed>イベントに登録するようにシステムに指示されます。 コードでは、このタイムライン用に 作成<xref:System.Windows.Media.Animation.Clock>する前に、このイベントに登録する必要があります。それ以外の場合は、通知を受け取りません。 この処理は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で自動的に実行されます。パーサー<xref:System.Windows.Media.Animation.Clock>は、作成される前にイベントに自動的に登録します。  
  
## <a name="see-also"></a>関連項目

- [アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)
- [アニメーションの概要](animation-overview.md)
- [タイミング動作の概要](timing-behaviors-overview.md)

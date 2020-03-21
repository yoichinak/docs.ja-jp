---
title: '方法 : アニメーションを反復する'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141550"
---
# <a name="how-to-repeat-an-animation"></a>方法 : アニメーションを反復する
この例では、アニメーションの繰<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>り返し<xref:System.Windows.Media.Animation.Timeline>動作を制御するために、プロパティを使用する方法を示します。  
  
## <a name="example"></a>例  
 アニメーション<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>が単純な<xref:System.Windows.Media.Animation.Timeline>継続時間を繰り返す回数をコントロールするプロパティです。 を使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>すると、特定の<xref:System.Windows.Media.Animation.Timeline>回数 (反復回数) または指定した期間の繰り返しを指定できます。 どちらの場合も、アニメーションは要求されたカウントまたは継続時間を満たすために必要な数の開始から終了までの実行を実行します。  
  
 デフォルトでは、タイムラインの繰り返し回数は 1.0 で、1 回再生され、繰り返しは行いません。 ただし、 の<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>プロパティを<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>に設定すると、タイムラインは無期限に繰り返されます。  
  
 プロパティを使用してアニメーションの<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>繰り返し動作を制御する方法を次の例に示します。 この例では、異なる<xref:System.Windows.FrameworkElement.Width%2A>種類の繰り返し動作を使用して、各四角形を使用して 5 つの四角形のプロパティをアニメーション化します。  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 完全なサンプルについては、「[アニメーションタイミング動作のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [反復サイクル中にアニメーション値を累積する](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [タイムラインを自動的に反転するかどうかを指定する](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [アニメーションおよびタイミングに関する「方法」トピック](animation-and-timing-how-to-topics.md)
- [アニメーションの概要](animation-overview.md)
- [アニメーションのタイミング動作のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)

---
title: '方法: アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1d6a3ec38a6488d997ce5a4734cc095446354070
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358133"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>方法: アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する
この例は、指定する方法を示します、 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 、非アクティブの<xref:System.Windows.Media.Animation.Timeline>アニメーション プロパティの。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>のプロパティを<xref:System.Windows.Media.Animation.Timeline>されていないときにアニメーション化されたプロパティの値に動作を決定します、アニメーション化は、ときに、<xref:System.Windows.Media.Animation.Timeline>がその親がアクティブでない<xref:System.Windows.Media.Animation.Timeline>アクティブまたは保留期間。 たとえばはアニメーション化されたプロパティのまま、最後に、アニメーションが終了またはその後の値がアニメーションの開始前に、の値に戻すか。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>をアニメーション化する、<xref:System.Windows.FrameworkElement.Width%2A>の 2 つの四角形。 各四角形を使用して、異なる<xref:System.Windows.Media.Animation.Timeline>オブジェクト。  
  
 1 つ<xref:System.Windows.Media.Animation.Timeline>が、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.Stop>、そのアニメーション化されていないに戻すに四角形の幅を停止するときの値、<xref:System.Windows.Media.Animation.Timeline>が終了します。 他の<xref:System.Windows.Media.Animation.Timeline>が、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>、これにより、幅、末端を維持するときの値、<xref:System.Windows.Media.Animation.Timeline>が終了します。  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 サンプル全体については、[アニメーション サンプル ギャラリー](https://go.microsoft.com/fwlink/?LinkID=159969)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [アニメーションの概要](animation-overview.md)
- [アニメーションとタイミングに関するトピック](animation-and-timing-how-to-topics.md)

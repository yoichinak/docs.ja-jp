---
title: '方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141174"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する
次の<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>例は、アニメーション化されたプロパティの非<xref:System.Windows.Media.Animation.Timeline>アクティブの を指定する方法を示しています。  
  
## <a name="example"></a>例  
 a<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A><xref:System.Windows.Media.Animation.Timeline>のプロパティは、アニメーション化されていない場合、つまり、アニメーション化されていない場合、つまり、アクティブでないが親<xref:System.Windows.Media.Animation.Timeline><xref:System.Windows.Media.Animation.Timeline>がアクティブまたは保持期間内にある場合に、アニメーション化されたプロパティの値に対して何が起こるかを決定します。 たとえば、アニメーションプロパティは、アニメーションの終了後も終了値に留まるのか、アニメーションが開始される前の値に戻るのか。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>を使用して<xref:System.Windows.FrameworkElement.Width%2A>2 つの四角形のアニメーションを作成しています。 各四角形は、<xref:System.Windows.Media.Animation.Timeline>異なるオブジェクトを使用します。  
  
 1 つは<xref:System.Windows.Media.Animation.Timeline><xref:System.Windows.Media.Animation.FillBehavior.Stop>に設定されており、終了すると、四角形の幅がアニメーション化されていない値に戻ります<xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> もう<xref:System.Windows.Media.Animation.Timeline>1<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>つは<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>、 のが含まれており、終了すると幅は終了値<xref:System.Windows.Media.Animation.Timeline>に留まる。  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 完全なサンプルについては、「[アニメーションの例ギャラリー](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [アニメーションの概要](animation-overview.md)
- [アニメーションおよびタイミングに関する「方法」トピック](animation-and-timing-how-to-topics.md)

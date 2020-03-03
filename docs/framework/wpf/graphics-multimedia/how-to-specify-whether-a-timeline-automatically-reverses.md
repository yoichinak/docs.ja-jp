---
title: '方法: タイムラインを自動的に反転するかどうかを指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024665"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>方法: タイムラインを自動的に反転するかどうかを指定する
タイムラインの<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティは、順方向の反復が完了した後は、逆方向に再生があるかどうかを決定します。 次の例では、複数のアニメーションと同じ期間とターゲットの値ではなく、異なる<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定します。 示すためにどのように<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティの動作が異なる<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>を繰り返す一部のアニメーションの設定が設定されます。 最後のアニメーション表示方法、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティの入れ子になったタイムラインに動作します。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]

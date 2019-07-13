---
title: '方法: 子タイムラインを使用してアニメーションを簡素化する'
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 21a297208be045eea79d6f5ca6c8eac016d26345
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804014"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>方法: 子タイムラインを使用してアニメーションを簡素化する
この例は、子を使用してアニメーションを簡素化する方法を示しています。<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクト。 A<xref:System.Windows.Media.Animation.Storyboard>の種類は、<xref:System.Windows.Media.Animation.Timeline>が含まれているタイムラインのターゲットの情報を提供します。 使用して、<xref:System.Windows.Media.Animation.Storyboard>をタイムラインのターゲット オブジェクトとプロパティの情報などの情報を提供します。  
  
 アニメーションを開始するには、1 つまたは複数を使用して、<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクトの入れ子になった子要素として、<xref:System.Windows.Media.Animation.Storyboard>します。 これら<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクトは、他のアニメーションを含めることができ、そのためよりカプセル化できる複雑なアニメーションのタイミング シーケンス。 アニメーション化する場合など、<xref:System.Windows.Controls.TextBlock>と同じで複数のシェイプ<xref:System.Windows.Media.Animation.Storyboard>のアニメーションを分離することができます、<xref:System.Windows.Controls.TextBlock>と図形は、それぞれを個別の<xref:System.Windows.Media.Animation.ParallelTimeline>します。 ため、各<xref:System.Windows.Media.Animation.ParallelTimeline>独自<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>とのすべての子要素、<xref:System.Windows.Media.Animation.ParallelTimeline>これに対して開始<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>タイミングが適切にカプセル化します。  
  
 次の例では、2 つのテキストをアニメーション化 (<xref:System.Windows.Controls.TextBlock>オブジェクト) から同じ<xref:System.Windows.Media.Animation.Storyboard>します。 A<xref:System.Windows.Media.Animation.ParallelTimeline>のいずれかのアニメーションをカプセル化、<xref:System.Windows.Controls.TextBlock>オブジェクト。  
  
 **パフォーマンスに注意してください。** 入れ子にすることが<xref:System.Windows.Media.Animation.Storyboard>、互いの内部でタイムライン<xref:System.Windows.Media.Animation.ParallelTimeline>はオーバーヘッドが少ないを必要なため、入れ子に適してします。 (、<xref:System.Windows.Media.Animation.Storyboard>クラスから継承、<xref:System.Windows.Media.Animation.ParallelTimeline>クラスです)。  
  
## <a name="example"></a>例  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [ストーリーボード アニメーション間で HandoffBehavior を指定する](how-to-specify-handoffbehavior-between-storyboard-animations.md)

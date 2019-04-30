---
title: '方法: クロックの状態が変化したときに通知を受け取る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: dc3fffb88ce59ceb908d6febd2f078820513b641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942138"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a>方法: クロックの状態が変化したときに通知を受け取る
クロックの<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>イベントが発生したときにその<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>はクロックが開始または停止するなど、無効になります。 このイベントを使用して直接登録できます、 <xref:System.Windows.Media.Animation.Clock>、またはを使用して登録することができます、<xref:System.Windows.Media.Animation.Timeline>します。  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard>と 2 つ<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトが 2 つの四角形の幅をアニメーション化するために使用します。 <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>クロックの状態の変更をリッスンするイベントを使用します。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 次の図は、親タイムラインとしてアニメーションの異なる状態を入力します (*ストーリー ボード*) が進行します。  
  
 ![2 つのアニメーションとストーリー ボードの状態をクロック](./media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 次の表は、位置、時刻を示します*Animation1*の<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>イベントが発生します。  
  
||||||||  
|-|-|-|-|-|-|-|  
|時間 (秒)|1|10|19|21|30|39|  
|状態|アクティブ|アクティブ|停止|アクティブ|アクティブ|停止|  
  
 次の表は、位置、時刻を示します*Animation2*の<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>イベントが発生します。  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|時間 (秒)|1|9|11|19|21|29|31|39|  
|状態|アクティブ|いっぱいになります。|アクティブ|停止|アクティブ|いっぱいになります。|アクティブ|停止|  
  
 注意*Animation1*の<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>場合でも、その状態のまま、10 秒間にイベントが発生した<xref:System.Windows.Media.Animation.ClockState.Active>します。 変更が、10 秒で状態が変更されたためにです<xref:System.Windows.Media.Animation.ClockState.Active>に<xref:System.Windows.Media.Animation.ClockState.Filling>に戻ると<xref:System.Windows.Media.Animation.ClockState.Active>同じティックでします。

---
title: '方法: ストーリーボード アニメーション間で HandoffBehavior を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083882"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>方法: ストーリーボード アニメーション間で HandoffBehavior を指定する
この例では、ストーリー ボード アニメーション間のハンドオフ動作を指定する方法を示します。 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>プロパティの<xref:System.Windows.Media.Animation.BeginStoryboard>新しいアニメーションを指定します。 プロパティに既に適用されている既存の対話します。  
  
## <a name="example"></a>例  
 次の例では、2 つのボタン上にマウス カーソルを移動すると拡大、カーソルがすぐに移動すると、縮小を作成します。 ボタンの上にマウス カーソルをすばやく削除して場合、は、1 つ目が終了する前に、2 番目のアニメーションが適用されます。 間の差が表示されるこのような 2 つのアニメーションが重なっている場合は、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>値<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>と<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>します。 値<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>の値の中にアニメーション間で遷移をスムーズに重なり合うアニメーションを組み合わせて<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>新しいアニメーションをすぐに重複する前のアニメーションを置き換えます。  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [アニメーションの概要](animation-overview.md)
- [アニメーションおよびタイミングに関する「方法」トピック](animation-and-timing-how-to-topics.md)

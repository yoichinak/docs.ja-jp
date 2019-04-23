---
title: '方法: アニメーションの継続時間を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198791"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>方法: アニメーションの継続時間を設定する
A<xref:System.Windows.Media.Animation.Timeline>表す時間のセグメントとそのセグメントの長さはタイムラインのによって決まります<xref:System.Windows.Duration>します。 ときに、<xref:System.Windows.Media.Animation.Timeline>が最後に達すると、その継続時間の再生を停止します。 場合、<xref:System.Windows.Media.Animation.Timeline>が子タイムラインも再生を停止します。 アニメーションの場合は、<xref:System.Windows.Duration>アニメーションにかかる時間の遷移の終了値をその開始値から指定します。  
  
 指定することができます、 <xref:System.Windows.Duration> 、有限の特定の時間または特殊な値を持つ<xref:System.Windows.Duration.Automatic%2A>または<xref:System.Windows.Duration.Forever%2A>します。 アニメーションが定義されている、有限の長さを持つ必要がありますので、アニメーションの継続時間は、時刻の値をある常に必要があります、それ以外の場合、アニメーションには、ターゲット値の間に移行する方法が不明です。 コンテナー タイムライン (<xref:System.Windows.Media.Animation.TimelineGroup>オブジェクト) など<xref:System.Windows.Media.Animation.Storyboard>と<xref:System.Windows.Media.Animation.ParallelTimeline>の既定の時間が指定されて<xref:System.Windows.Duration.Automatic%2A>、つまり、これらは、最後の子が停止したときに自動的に終了します。  
  
 次の例、幅、高さ、および塗りつぶしの色で、<xref:System.Windows.Shapes.Rectangle>がアニメーション化されます。 期間は、結果として認識されるアニメーションの速度を制御して、コンテナー タイムラインの存続期間を持つ子タイムラインの期間のオーバーライドを含むアニメーション効果アニメーションとコンテナーのタイムラインに設定されます。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Duration>
- [アニメーションの概要](animation-overview.md)

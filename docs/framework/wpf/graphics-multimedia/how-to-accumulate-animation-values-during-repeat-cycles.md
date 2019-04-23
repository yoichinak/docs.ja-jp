---
title: '方法: 反復サイクル中にアニメーション値を累積する'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 4b739883322751e2df86e13bfd07249abdb10a08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146017"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>方法: 反復サイクル中にアニメーション値を累積する
この例は、使用する方法を示します、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>プロパティを反復サイクル中にアニメーション値を累積します。  
  
## <a name="example"></a>例  
 使用して、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>反復サイクル中、アニメーションの底の値を累積するプロパティ。 9 回繰り返すアニメーションを設定する場合など (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ="9 x") 10 から 15 までアニメーション化するプロパティを設定して (から 10 を = = 15)、プロパティは、15 ~ 20 2 つ目のサイクル中に、最初のサイクル中に 10 から 15 までアニメーション化、20 ~ 25 と 3 番目のサイクル中にから。 そのため、各アニメーション サイクルは、その基本値として前のアニメーション サイクルからの終了値を使用します。  
  
 使用することができます、`IsCumulative`最も基本的なアニメーションとほとんどのキー フレーム アニメーションのプロパティ。 詳細については、次を参照してください。[アニメーションの概要](animation-overview.md)と[キー フレーム アニメーションの概要](key-frame-animations-overview.md)します。  
  
 次の例では、次の 4 つの四角形の幅をアニメーション化してこの動作を示します。 例:  
  
-   最初の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimation>設定と、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>プロパティを`true`します。  
  
-   2 番目の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimation>設定と、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>プロパティの既定値を`false`します。  
  
-   含む 3 番目の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>設定と、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>プロパティを`true`します。  
  
-   含む最後の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>設定と、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>プロパティを`false`します。  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの出力値をアニメーションの開始値に追加する](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [アニメーションを反復する](how-to-repeat-an-animation.md)
- [アニメーションの概要](animation-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [方法トピック](animation-and-timing-how-to-topics.md)

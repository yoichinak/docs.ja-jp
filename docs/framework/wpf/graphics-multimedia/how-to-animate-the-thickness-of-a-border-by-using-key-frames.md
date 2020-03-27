---
title: '方法 : キー フレームを使用して境界線の太さをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344694"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>方法 : キー フレームを使用して境界線の太さをアニメーション化する
この例では、 のプロパティをアニメーション<xref:System.Windows.Controls.Control.BorderThickness%2A>化する方法<xref:System.Windows.Controls.Border>を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>クラスを使用して、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティを<xref:System.Windows.Controls.Border>アニメーション化します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の半秒の間に、クラスのインスタンス<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>を使用して、徐々に境界線の厚さを増やします。 この例では<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>、値間のスムーズな線形増加を作成するために使用します。  
  
2. 次の半分の秒の終わりに、クラスのインスタンスを<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>使用して、境界線の厚さを突然増加させます。 派生したような離散的な<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>キー フレームは、値の間に突然ジャンプを作成します。  
  
3. 最後の 2 秒間に、クラスのインスタンス<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>を使用して境界線の厚さを小さくします。 スプライン キー フレームは、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>プロパティの値<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>に従って値間の可変遷移を作成します。 このキー フレームでは、アニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
- [BorderThickness 値をアニメーション化する](../controls/how-to-animate-a-borderthickness-value.md)

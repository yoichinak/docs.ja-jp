---
title: '方法: キー フレームを使用して境界線の太さをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 101fd077bf125faadbd9a0186c2282e4b20ee78f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699033"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>方法: キー フレームを使用して境界線の太さをアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティを<xref:System.Windows.Controls.Border>します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティを<xref:System.Windows.Controls.Border>します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の 0.5 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>の境界線の太さを徐々 に増加するクラス。 この例では<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>値の間の滑らかな線形増加を作成します。  
  
2. インスタンスを使用している 0.5 秒は、次の最後に、<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>クラスを境界線の太さを突然太きます。 派生したもののような不連続キーフレーム<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>されている値の間に急なジャンプを作成、アニメーションの動きはぎくしゃくします。  
  
3. 最後の 2 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>の境界線の太さを小さくクラス。 派生したもののようなスプライン キーフレーム<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>の値に基づいて値の間に可変遷移を作成、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>プロパティ。 このキー フレームでは、アニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
- [BorderThickness 値をアニメーション化する](../controls/how-to-animate-a-borderthickness-value.md)

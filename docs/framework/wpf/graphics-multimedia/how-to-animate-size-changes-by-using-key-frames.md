---
title: '方法 : キー フレームを使用してサイズの変更をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344647"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>方法 : キー フレームを使用してサイズの変更をアニメーション化する
この例では、キー フレームを使用してサイズの変更をアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>クラスを使用して、<xref:System.Windows.Media.ArcSegment.Size%2A>のプロパティを<xref:System.Windows.Media.ArcSegment>アニメーション化します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. アニメーションの前半の 2 秒間に、クラスのインスタンスを<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>使用して、円弧のサイズを徐々に大きくします。線形キー フレーム<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>のような値間のスムーズな直線遷移を作成します。  
  
2. 次の半分の秒の終わりに、クラスのインスタンスを<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>使用して、突然アークのサイズを大きくします。値の間に<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>突然ジャンプを作成するような離散的なキー フレーム、つまりサイズの変更が突然発生し、微妙ではありません。  
  
3. 最後の 2 秒間に、クラスのインスタンス<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>を使用して、アークのサイズを大きくします。スプライン キー<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>フレームのような値の間に、プロパティの値に従<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>った可変的な遷移を作成します。 この例では、円弧のサイズは最初はゆっくり大きくなりますが、時間セグメントの終点に向かって急激に大きくなります。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

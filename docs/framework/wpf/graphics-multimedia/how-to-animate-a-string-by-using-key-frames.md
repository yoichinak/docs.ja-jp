---
title: '方法 : キー フレームを使用して文字列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344670"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>方法 : キー フレームを使用して文字列をアニメーション化する
この例では、キー フレームを使用して、コントロールの<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティである文字列を<xref:System.Windows.Controls.Button>アニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>クラスを使用して、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティを<xref:System.Windows.Controls.Button>アニメーション化します。  
  
 この例のすべてのキー フレームは<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>、キー フレームを使用して作成される文字列アニメーションは個別のキー フレームしか使用できないため、クラスのインスタンスを使用します。 値の間に<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>突然ジャンプを作成するような離散的なキー フレーム、つまりアニメーションの変更はすばやく発生し、微妙ではありません。  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

---
title: '方法: キー フレームを使用して文字列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 70c5766da2ea91f519756cb47b20d688b33253e0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356234"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>方法: キー フレームを使用して文字列をアニメーション化する
この例があり、この例では、文字列をアニメーション化する方法を示しています、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティを<xref:System.Windows.Controls.Button>キー フレームを使用して、コントロール。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティを<xref:System.Windows.Controls.Button>します。  
  
 この例ではすべてのキー フレームのインスタンスを使用して、<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>クラスをキー フレームで作成される文字列のアニメーションは不連続のキー フレームのみを使用できます。 などの不連続のキーフレーム<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>されている値の間に急なジャンプを作成、変更、アニメーションに迅速に実行およびはなく。  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

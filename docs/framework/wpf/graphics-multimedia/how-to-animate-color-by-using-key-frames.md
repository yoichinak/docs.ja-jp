---
title: '方法: キー フレームを使用して色をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: e579c4beb757ccf58eb1b9ca1f3852a5b96cac1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326087"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>方法: キー フレームを使用して色をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Media.SolidColorBrush.Color%2A>のプロパティを<xref:System.Windows.Media.SolidColorBrush>します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の 2 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearColorKeyFrame>緑から赤に色を徐々 に変化するクラス。 などの線形キーフレーム<xref:System.Windows.Media.Animation.LinearColorKeyFrame>値の間の滑らかな線形トランジションを作成します。  
  
2. インスタンスを使用して、[次へ] の末尾の 0.5 秒、<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>クラスをすばやく色を赤から黄色に変更します。 などの不連続のキーフレーム<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>、つまり値の間での急激な変化を作成、アニメーションのこの部分で色の変更は、短時間で発生しはありません。  
  
3. 最後の 2 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.SplineColorKeyFrame>クラスをもう一度、色を変更する — 現時点黄色から緑色にします。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineColorKeyFrame>の値に基づいて値の間に可変遷移を作成、<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>プロパティ。 この例では、色の変化は最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

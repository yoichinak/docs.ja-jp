---
title: '方法 : キー フレームを使用して点をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344877"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>方法 : キー フレームを使用して点をアニメーション化する
この例では、クラスを<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>使用して アニメーションを作成する<xref:System.Windows.Point>方法を示します。  
  
## <a name="example"></a>例  
 次の例では、三角形のパスに沿って楕円を移動します。 この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>クラスを使用して、<xref:System.Windows.Media.EllipseGeometry.Center%2A>のプロパティを<xref:System.Windows.Media.EllipseGeometry>アニメーション化します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の 2 番目の間に、クラス<xref:System.Windows.Media.Animation.LinearPointKeyFrame>のインスタンスを使用して、開始位置から一定の速度でパスに沿って楕円を移動します。 線形キー フレーム<xref:System.Windows.Media.Animation.LinearPointKeyFrame>のような値間のスムーズな線形補間を作成します。  
  
2. 次の半分の秒の終わりの間に、<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>クラスのインスタンスを使用して、パスに沿って楕円を次の位置に突然移動します。 値の間に<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然ジャンプを作成するような離散的なキー フレーム。  
  
3. 最後の 2 秒間に、クラスのインスタンス<xref:System.Windows.Media.Animation.SplinePointKeyFrame>を使用して楕円を開始位置に戻します。 スプライン キー<xref:System.Windows.Media.Animation.SplinePointKeyFrame>フレームのような値の間に、プロパティの値に従<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>った可変的な遷移を作成します。 この例では、アニメーションは最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
 他のアニメーションの例との一貫性を保つために、この例<xref:System.Windows.Media.Animation.Storyboard>のコード バージョン<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>ではオブジェクトを使用して を適用します。 ただし、コード内で 1 つのアニメーションを適用する場合は、 メソッドを<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>使用する代わりに、<xref:System.Windows.Media.Animation.Storyboard>このメソッドを使用する方が簡単です。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

---
title: '方法: キー フレームを使用して点をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: 4eeb7aa271883e1c76d5cac77f49accbdff39aea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357236"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>方法: キー フレームを使用して点をアニメーション化する
この例は、使用する方法を示します、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Point>します。  
  
## <a name="example"></a>例  
 次の例では、三角形のパスに沿って楕円を移動します。 この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Media.EllipseGeometry.Center%2A>のプロパティ、<xref:System.Windows.Media.EllipseGeometry>します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 0.5 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearPointKeyFrame>一定の速度で開始位置からパスに沿って楕円を移動するクラス。 などの線形キーフレーム<xref:System.Windows.Media.Animation.LinearPointKeyFrame>滑らかな線形補間値を作成します。  
  
2.  インスタンスを使用して、[次へ] の末尾の 0.5 秒、<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>クラスに次の位置に突然パスに沿って楕円を移動します。 などの不連続のキーフレーム<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>値の間に急なジャンプを作成します。  
  
3.  最後の 2 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.SplinePointKeyFrame>楕円を開始位置に移動するクラス。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplinePointKeyFrame>の値に基づいて値の間に可変遷移を作成、<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>プロパティ。 この例では、アニメーションは最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
 この例のコードを使用して、他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>を適用するオブジェクト、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>します。 ただし、コード内で 1 つのアニメーションを適用する場合は使いやすく、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>します。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

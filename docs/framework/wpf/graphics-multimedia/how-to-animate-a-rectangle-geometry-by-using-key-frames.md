---
title: '方法: キー フレームを使用して四角形のジオメトリをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311345"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>方法: キー フレームを使用して四角形のジオメトリをアニメーション化する
この例は、アニメーション化する方法を示しています。、<xref:System.Windows.Media.RectangleGeometry.Rect%2A>のプロパティを<xref:System.Windows.Media.RectangleGeometry>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Media.RectangleGeometry.Rect%2A>のプロパティを<xref:System.Windows.Media.RectangleGeometry>します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の 2 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearRectKeyFrame>位置、幅、および四角形の高さを徐々 に変化をアニメーション化するクラス。 などの線形キーフレーム<xref:System.Windows.Media.Animation.LinearRectKeyFrame>値の間の滑らかな線形トランジションを作成します。  
  
2. インスタンスを使用して、[次へ] の末尾の 0.5 秒、<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>クラスを四角形の高さを突然低きます。 などの不連続のキーフレーム<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>されている値の間での急激な変化を作成、高さの減少は短時間で発生しはありません。  
  
3. 最後の 2 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.SplineRectKeyFrame>四角形を元の位置とサイズに変更するクラス。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineRectKeyFrame>の値に基づいて値の間に可変遷移を作成、<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>プロパティ。 この例では、変化は最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)

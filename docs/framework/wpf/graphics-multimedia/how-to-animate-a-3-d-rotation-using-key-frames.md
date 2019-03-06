---
title: '方法: キー フレームを使用して 3-D 回転をアニメーション化します。'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 90e982838cb5d5b4488185c041e946c15d1e61e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369137"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>方法: キー フレームを使用して 3-D 回転をアニメーション化します。
次の例では、 <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> 「補助」の結果としてその軸の回転をアニメーション化中に回転 3D オブジェクトを作成するために使用します。 このアニメーションは、次のキー フレームを使用します。  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> 作成する滑らかな線形補間値の間に使用されます。  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> (補間) の値の間で突然「ジャンプ」の作成に使用されます。  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> によって値の間に可変遷移を作成するために使用、<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>プロパティ。 次の例で、アニメーションのこの部分は低速と始まりますが、時間セグメントの末尾に向かって、急激に速くなります。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- [3-D グラフィックスの概要](3-d-graphics-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [ストーリーボードを使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation を使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [四元数を使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [キー フレーム (QuaternionAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)

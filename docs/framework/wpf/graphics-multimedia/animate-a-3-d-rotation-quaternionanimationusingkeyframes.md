---
title: '方法 : キー フレームを使用して 3D 回転をアニメーション化する (クォータニオンアニメーションを使用するキーフレーム)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112298"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>方法 : キー フレームを使用して 3D 回転をアニメーション化する (クォータニオンアニメーションを使用するキーフレーム)
次の例では、3D<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>オブジェクトを回転させるために使用します。 このアニメーションでは、次のキー フレームを使用します。  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>は、値間の滑らかな直線補間を作成するために使用されます。  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>は、値間に突然の「ジャンプ」を作成するために使用されます(補間なし)。  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>は、プロパティに応じて値間の変数遷移<xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>を作成するために使用されます。 次の例では、アニメーションのこの部分は低速から始まりますが、時間セグメントの終わりに向かって、指数関数的に高速化します。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [ストーリーボードを使用して 3D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [回転 3D アニメーションを使用して 3D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [四元数を使用して 3D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [キー フレームを使用して 3D 回転をアニメーション化する (回転 3D アニメーションを使用してキー フレーム)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)

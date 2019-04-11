---
title: '方法: キー フレームを使用してカメラの位置および方向をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 44464cc314d649516998338e36c1b523101ac4e2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346081"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>方法: キー フレームを使用してカメラの位置および方向をアニメーション化する
次の例では、<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>の位置をアニメーション化するために使用する<xref:System.Windows.Media.Media3D.PerspectiveCamera>3D シーンでします。 さらに、 <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> 3D シーンでカメラが指す方向をアニメーション化するために使用します。 どちらのアニメーションは、一連のアニメーション効果を作成するいくつかのキー フレームを使用します。  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>する滑らかな線形補間値の間での作成に使用します。  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>値 (補間) の間で突然「ジャンプ」の作成に使用します。  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>に応じて値の間に可変遷移を作成するために使用、<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>プロパティ。 次の例では、アニメーションは低速と始まりますが、時間セグメントの末尾に向かって、急激に速くなります。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [3D シーンでカメラの位置および方向をアニメーション化する](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)

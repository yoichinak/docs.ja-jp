---
title: '方法: ストーリーボードを使用して 3-D 回転をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146199"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>方法: ストーリーボードを使用して 3-D 回転をアニメーション化する
次の例では、回転、「ぐらつく」アニメーション化して、3 D オブジェクトを作成する方法を示しています、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>と<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>のプロパティ、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>オブジェクト。 これは、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>オブジェクトは、3 D オブジェクトの回転変換を指定し、希望の回転の効果を作成するためのプロパティをアニメーション化します。 ストーリー ボード内<xref:System.Windows.Media.Animation.DoubleAnimation>をアニメーション化するために使用、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>プロパティ<xref:System.Windows.Media.Animation.Vector3DAnimation>をアニメーション化するために使用、<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>プロパティ。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [Rotation3DAnimation を使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [キー フレーム (Rotation3DAnimationUsingKeyFrames) を使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)

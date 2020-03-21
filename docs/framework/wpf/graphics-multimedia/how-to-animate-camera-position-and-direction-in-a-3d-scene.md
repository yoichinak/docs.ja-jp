---
title: '方法 : 3D シーンでカメラの位置および方向をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112213"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>方法 : 3D シーンでカメラの位置および方向をアニメーション化する
次の例は、カメラの位置をアニメートし、3D シーンで向いている方向をアニメートする方法を示しています。 これは、 の<xref:System.Windows.Media.Animation.Point3DAnimation>プロパティ<xref:System.Windows.Media.Animation.Vector3DAnimation>と プロパティをそれぞれ<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>を<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>アニメーション化することによって行われます<xref:System.Windows.Media.Media3D.PerspectiveCamera>。 このようなアニメーションを使用して、イベントに応答してシーンの見物人のビューを変更できます。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [キー フレームを使用してカメラの位置および方向をアニメーション化する](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)

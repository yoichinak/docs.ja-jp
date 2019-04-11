---
title: '方法: 3D シーンでカメラの位置および方向をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: b64263a495ffe845a76317aad8f5b4a14e11b31e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146004"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>方法: 3D シーンでカメラの位置および方向をアニメーション化する
次の例では、カメラの位置をアニメーション化してが、3 D シーンで向いている方向をアニメーション化する方法を示します。 使用してこれは、<xref:System.Windows.Media.Animation.Point3DAnimation>と<xref:System.Windows.Media.Animation.Vector3DAnimation>をアニメーション化する、<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>と<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>それぞれのプロパティ、<xref:System.Windows.Media.Media3D.PerspectiveCamera>します。 このようなアニメーションを使用すると、イベントへの応答でのシーンの観察者のビューを変更するのに可能性があります。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [キー フレームを使用してカメラの位置および方向をアニメーション化する](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)

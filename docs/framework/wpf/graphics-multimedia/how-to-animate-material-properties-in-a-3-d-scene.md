---
title: '方法: 3-D シーンで素材プロパティをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 58e880a2828d21ee76f7fac6bdcf313e8454e65b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090902"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a>方法: 3-D シーンで素材プロパティをアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.Brush.Opacity%2A>のプロパティ、<xref:System.Windows.Media.Media3D.Material>に適用される、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]モデル。  
  
 次のコード例を定義、<xref:System.Windows.Media.LinearGradientBrush>として使用される、 <xref:System.Windows.Media.Media3D.Material> 3 D オブジェクトに適用します。  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <xref:System.Windows.Media.Brush.Opacity%2A>プロパティのこの<xref:System.Windows.Media.LinearGradientBrush>は、次のコード例を使用してアニメーション化します。  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [3-D シーンを作成する](how-to-create-a-3-d-scene.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)

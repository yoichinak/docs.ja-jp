---
title: '方法: 3-D モデルに描画を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: cfd133b04e0c04b4a502d2466e67685700e3f408
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368914"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>方法: 3-D モデルに描画を適用する
この例は、使用する方法を示します、<xref:System.Windows.Media.DrawingBrush>として、<xref:System.Windows.Media.Media3D.Material>に適用される、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]モデル。  
  
 次のコード定義を<xref:System.Windows.Media.DrawingGroup>の内容として、<xref:System.Windows.Media.DrawingBrush>します。  <xref:System.Windows.Media.DrawingBrush>として設定されて、<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>のプロパティ、<xref:System.Windows.Media.Media3D.DiffuseMaterial>に適用される、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。  
  
 **注:** 多くの場合、複雑なオブジェクトと次の図のような値を再利用できるし、コードを簡略化するリソースとして定義する必要があります。 参照してください[XAML リソース](../advanced/xaml-resources.md)詳細についてはします。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- [XAML リソース](../advanced/xaml-resources.md)
- [3-D シーンを作成する](how-to-create-a-3-d-scene.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)

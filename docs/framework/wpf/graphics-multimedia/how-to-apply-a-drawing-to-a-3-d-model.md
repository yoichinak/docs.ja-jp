---
title: '方法: 3D モデルに図面を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112181"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>方法: 3D モデルに図面を適用する

この例では、3D<xref:System.Windows.Media.DrawingBrush>モデルに<xref:System.Windows.Media.Media3D.Material>適用された a を使用する方法を示します。

次のコードでは、<xref:System.Windows.Media.DrawingGroup>の内容として<xref:System.Windows.Media.DrawingBrush>を定義します。  <xref:System.Windows.Media.DrawingBrush>は、3D<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>平面に適用<xref:System.Windows.Media.Media3D.DiffuseMaterial>されるプロパティとして設定されます。

> [!NOTE]
> 多くの場合、以下の図のような複雑なオブジェクトや値を、再利用してコードを単純化できるリソースとして定義することが望ましい場合があります。 詳細については[、「XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)」を参照してください。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>例

次のコードは、サンプル全体を示しています。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>関連項目

- [XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [3D シーンを作成する](how-to-create-a-3-d-scene.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)

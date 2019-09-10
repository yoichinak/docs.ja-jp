---
title: '方法: 3-D モデルに描画を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855875"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>方法: 3-D モデルに描画を適用する

この例では、を<xref:System.Windows.Media.DrawingBrush> 3-d モデルに適用された<xref:System.Windows.Media.Media3D.Material>として使用する方法を示します。

次のコードでは<xref:System.Windows.Media.DrawingGroup> 、を<xref:System.Windows.Media.DrawingBrush>のコンテンツとして定義しています。  は、3-d 平面に<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> <xref:System.Windows.Media.Media3D.DiffuseMaterial>適用されるのプロパティとして設定されます。<xref:System.Windows.Media.DrawingBrush>

> [!NOTE]
> 多くの場合、次の図のような複雑なオブジェクトと値をリソースとして定義することをお勧めします。これは、コードを再利用し、簡略化することができます。 詳細については、「 [XAML リソース](../advanced/xaml-resources.md)」を参照してください。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>例

次のコードは、サンプル全体を示しています。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>関連項目

- [XAML リソース](../advanced/xaml-resources.md)
- [3-D シーンを作成する](how-to-create-a-3-d-scene.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)

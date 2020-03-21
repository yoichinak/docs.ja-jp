---
title: '方法: 3D オブジェクトの前面と背面にマテリアルを適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112142"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>方法: 3D オブジェクトの前面と背面にマテリアルを適用する
次の例は、3D<xref:System.Windows.Media.Media3D.Material>オブジェクトの前面と背面に a を適用し、オブジェクトをアニメートしてオブジェクトの両側を表示する方法を示しています。 a<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A><xref:System.Windows.Media.Media3D.GeometryModel3D>のプロパティはオブジェクトの前面に赤<xref:System.Windows.Media.Brush>を適用するために使用され、の<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>プロパティ<xref:System.Windows.Media.Media3D.GeometryModel3D>はオブジェクトの背面に青<xref:System.Windows.Media.Brush>を適用するために使用されます。 以下のコードは、オブジェクトへのマテリアルの適用を示しています。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>例  
 次のコードは、サンプル全体を示しています。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [3D シーンを作成する](how-to-create-a-3-d-scene.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)
- [3D シーンでのマテリアル プロパティのアニメーション化](how-to-animate-material-properties-in-a-3-d-scene.md)
- [3D オブジェクトにエミセッシブ マテリアルを適用する](how-to-apply-emissive-material-to-a-3-d-object.md)

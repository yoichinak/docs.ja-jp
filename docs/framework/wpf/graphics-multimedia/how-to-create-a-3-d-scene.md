---
title: '方法: 3-D シーンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: a431b78993d197dac99f0b6e365823acb295f0b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611646"
---
# <a name="how-to-create-a-3-d-scene"></a>方法: 3-D シーンを作成する
この例では、回転紙のフラットなシートのような 3-D オブジェクトを作成する方法を示します。 A<xref:System.Windows.Controls.Viewport3D>次のコンポーネントと共にこのシンプルな 3-D シーンを作成に使用されます。  
  
- 使用して、カメラを作成、<xref:System.Windows.Media.Media3D.PerspectiveCamera>します。 カメラでは、表示可能な 3-D シーンの部分を指定します。  
  
- 使用して 3-D オブジェクト (枚の用紙) の形状を指定するメッシュが作成、<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>プロパティの<xref:System.Windows.Media.Media3D.GeometryModel3D>します。  
  
- 使用して、オブジェクト (このサンプルでの線形グラデーション) の表面に表示される素材が指定されて、<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>プロパティの<xref:System.Windows.Media.Media3D.GeometryModel3D>します。  
  
- オブジェクトを使用して、洗練するため、ライトが作成された<xref:System.Windows.Media.Media3D.DirectionalLight>します。  
  
## <a name="example"></a>例  
 次のコードでは、XAML で 3-D シーンを作成する方法を示します。  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>例  
 次のコードでは、手続き型コードで同じ 3-D シーンを作成する方法を示します。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [3-D グラフィックスの概要](3-d-graphics-overview.md)

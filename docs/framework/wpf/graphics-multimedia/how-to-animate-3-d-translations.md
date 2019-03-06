---
title: '方法: 3-D 変換をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 0290beac5a92a955b39d0b8fcc24705346c2964a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351919"
---
# <a name="how-to-animate-3-d-translations"></a>方法: 3-D 変換をアニメーション化する
このトピックでは、移動変換をアニメーション化する方法を示します、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]モデル。  
  
 次のコードのアプリケーションを示しています、<xref:System.Windows.Media.Media3D.TranslateTransform3D>オブジェクトを<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>のプロパティを<xref:System.Windows.Media.Media3D.GeometryModel3D>します。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>プロパティのこの<xref:System.Windows.Media.Media3D.TranslateTransform3D>オブジェクトは次のコードを使用してアニメーション化します。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [3-D シーンを作成する](how-to-create-a-3-d-scene.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)
- [変換の概要](transforms-overview.md)

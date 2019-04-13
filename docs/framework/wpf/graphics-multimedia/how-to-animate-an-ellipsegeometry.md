---
title: '方法: EllipseGeometry をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], EllipseGeometry objects [WPF]
- EllipseGeometry objects [WPF], animating
- graphics [WPF], animation
ms.assetid: 767b9b6e-9cb7-482e-b6c2-fee7750c3995
ms.openlocfilehash: 0f8174a2144435c9ad65904ee587355e8b38e935
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126010"
---
# <a name="how-to-animate-an-ellipsegeometry"></a>方法: EllipseGeometry をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.Geometry>内、<xref:System.Windows.Shapes.Path>要素。 次の例では、<xref:System.Windows.Media.Animation.PointAnimation>をアニメーション化するために使用、<xref:System.Windows.Media.EllipseGeometry.Center%2A>の<xref:System.Windows.Media.EllipseGeometry>します。  
  
## <a name="example"></a>例  
 [!code-xaml[animatepath_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip_XAML/CS/EllipseGeometryExample.xaml#1)]  
  
 [!code-csharp[animatepath_snip#101](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip/CSharp/EllipseGeometryExample.cs#101)]  
  
 [!code-vb[animatepath_snip#201](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animatepath_snip/VisualBasic/EllipseGeometryExample.vb#201)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [ジオメトリの概要](geometry-overview.md)

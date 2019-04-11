---
title: '方法: 3 次ベジエ曲線を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 36544abc774b7fe82c2ff47483cfedd6fb13e344
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115571"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>方法: 3 次ベジエ曲線を作成する
この例では、3 次ベジエ曲線を作成する方法を示します。 3 次ベジエ曲線を作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.BezierSegment>クラス。  結果のジオメトリを表示するには使用、<xref:System.Windows.Shapes.Path>要素と共に使用または、<xref:System.Windows.Media.GeometryDrawing>または<xref:System.Windows.Media.DrawingContext>します。 次の例についてから 3 次ベジエ曲線を描画 (10, 100) に (300, 100)。 曲線がの制御点 (100, 0) と (200、200)。  
  
## <a name="example"></a>例  
 [xaml]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]マークアップの省略構文を使用してパスを記述することがあります。  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、オブジェクト タグを使用して 3 次ベジエ曲線を描画することもできます。 次の例は、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例と同じです。  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [楕円の円弧を作成する](how-to-create-an-elliptical-arc.md)
- [PathGeometry で LineSegment を作成する](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [3 次ベジエ曲線を作成する](how-to-create-a-cubic-bezier-curve.md)
- [2 次ベジエ曲線を作成する](how-to-create-a-quadratic-bezier-curve.md)

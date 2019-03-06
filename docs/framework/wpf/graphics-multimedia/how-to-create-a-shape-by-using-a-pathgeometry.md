---
title: '方法: PathGeometry を使用して図形を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: ce84f2509116207afa200ddf83dcdc1f8101da13
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356223"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>方法: PathGeometry を使用して図形を作成する
この例を使用して図形を作成する方法を示しています、<xref:System.Windows.Media.PathGeometry>クラス。 <xref:System.Windows.Media.PathGeometry> オブジェクトが 1 つまたは複数で構成される<xref:System.Windows.Media.PathFigure>オブジェクト。 各<xref:System.Windows.Media.PathFigure>異なる"図"または図形を表します。 各<xref:System.Windows.Media.PathFigure>自体は 1 つ以上ので構成されます<xref:System.Windows.Media.PathSegment>それぞれ図や図形の接続されている部分を表すオブジェクトします。 セグメントの種類<xref:System.Windows.Media.LineSegment>、 <xref:System.Windows.Media.ArcSegment>、および<xref:System.Windows.Media.BezierSegment>します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.PathGeometry>三角形が作成されます。 <xref:System.Windows.Media.PathGeometry>を使用して表示される、<xref:System.Windows.Shapes.Path>要素。  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 前の例で作成した図を次に示します。  
  
 ![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
PathGeometry で作成された三角形  
  
 前の例では、比較的単純な図形、三角形を作成する方法を示しました。 A<xref:System.Windows.Media.PathGeometry>円弧、曲線などのより複雑な図形を作成できます。 例については、次を参照してください。[楕円の円弧を作成する](how-to-create-an-elliptical-arc.md)、 [3 次ベジエ曲線を作成](how-to-create-a-cubic-bezier-curve.md)、および[2 次ベジエ曲線を作成する](how-to-create-a-quadratic-bezier-curve.md)します。  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [ジオメトリの概要](geometry-overview.md)
- [ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)

---
title: '方法: RectangleGeometry を使用して四角形を定義する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 146ca7017ee38ad5c1065e59662ac441e7bfbfe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075797"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>方法: RectangleGeometry を使用して四角形を定義する
この例は、使用する方法を説明します、<xref:System.Windows.Media.RectangleGeometry>を四角形を表すクラス。  
  
## <a name="example"></a>例  
 次の例を作成してレンダリングする方法を示しています、<xref:System.Windows.Media.RectangleGeometry>します。  相対的な位置と四角形のディメンションがによって定義、<xref:System.Windows.Rect>構造体。 相対位置は`50,50`高さと幅はどちらも、`25`正方形を作成します。 四角形の内部を塗りつぶす、<xref:System.Windows.Media.Brushes.LemonChiffon%2A>でペイント ブラシとアウトライン、<xref:System.Windows.Media.Brushes.Black%2A>ストロークの太さを`1`します。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 この例を<xref:System.Windows.Shapes.Path>レンダリングする要素、<xref:System.Windows.Media.RectangleGeometry>を使用する他の多くの方法はあります<xref:System.Windows.Media.RectangleGeometry>オブジェクト。 たとえば、<xref:System.Windows.Media.RectangleGeometry>を指定するために使用する、<xref:System.Windows.UIElement.Clip%2A>の<xref:System.Windows.UIElement>または<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>の<xref:System.Windows.Media.GeometryDrawing>。  
  
 その他の単純なジオメトリ クラス<xref:System.Windows.Media.LineGeometry>と<xref:System.Windows.Media.EllipseGeometry>します。 複雑なものと同様にこれらのジオメトリを作成することもを使用して、<xref:System.Windows.Media.PathGeometry>または<xref:System.Windows.Media.StreamGeometry>します。  
  
## <a name="see-also"></a>関連項目

- [ジオメトリの概要](geometry-overview.md)
- [複合図形を作成する](how-to-create-a-composite-shape.md)
- [PathGeometry を使用して図形を作成する](how-to-create-a-shape-by-using-a-pathgeometry.md)

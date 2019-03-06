---
title: '方法: GeometryDrawing を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 6eb604a8446000ef308c2b5a99480fb6a476c949
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373817"
---
# <a name="how-to-create-a-geometrydrawing"></a>方法: GeometryDrawing を作成する
この例は、作成および表示する方法を示しています、<xref:System.Windows.Media.GeometryDrawing>します。 A<xref:System.Windows.Media.GeometryDrawing>塗りつぶしをアウトラインと関連付けることによって図形を作成することができます、<xref:System.Windows.Media.Pen>と<xref:System.Windows.Media.Brush>で、<xref:System.Windows.Media.Geometry>します。 <xref:System.Windows.Media.GeometryDrawing.Geometry%2A>図形の構造体について説明します、<xref:System.Windows.Media.GeometryDrawing.Brush%2A>図形の塗りつぶし、について説明しますと、<xref:System.Windows.Media.GeometryDrawing.Pen%2A>図形のアウトラインをについて説明します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.GeometryDrawing>図形を表示するためにします。 図形は、<xref:System.Windows.Media.GeometryGroup>と 2 つ<xref:System.Windows.Media.EllipseGeometry>オブジェクト。 図形の内部を塗りつぶす、<xref:System.Windows.Media.LinearGradientBrush>アウトラインの描画に使用して、 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>します。 <xref:System.Windows.Media.GeometryDrawing>を使用して表示される、<xref:System.Windows.Media.ImageDrawing>と<xref:System.Windows.Controls.Image>要素。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 次の図は、その結果<xref:System.Windows.Media.GeometryDrawing>します。  
  
 ![2 つの楕円の GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 複雑な図面を作成するには、1 つの複合描画を使用してに複数の描画オブジェクトを結合できます、<xref:System.Windows.Media.DrawingGroup>します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.DrawingGroup>
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [ジオメトリの概要](geometry-overview.md)
- [複合描画を作成する](how-to-create-a-composite-drawing.md)

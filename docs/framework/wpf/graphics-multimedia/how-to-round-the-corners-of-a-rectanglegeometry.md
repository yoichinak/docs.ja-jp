---
title: '方法: RectangleGeometry の角に丸みを付ける'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089134"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>方法: RectangleGeometry の角に丸みを付ける
角を丸める、<xref:System.Windows.Media.RectangleGeometry>に設定して、その<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>と<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>プロパティを 0 より大きい値です。 値が大きいほど、四角形の角はの角。  
  
## <a name="example"></a>例  
 次の例をいくつか示します<xref:System.Windows.Media.RectangleGeometry>オブジェクトが異なる<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>と<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>設定します。 <xref:System.Windows.Media.RectangleGeometry>を使用してオブジェクトが表示される<xref:System.Windows.Shapes.Path>要素。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![別の RadiusX 長方形&#47;RadiusY 設定](./media/graphicsmm-rounded.png "graphicsmm_rounded")  
角の丸い四角形  
  
## <a name="see-also"></a>関連項目

- [ジオメトリの概要](geometry-overview.md)
- [複合図形を作成する](how-to-create-a-composite-shape.md)
- [PathGeometry を使用して図形を作成する](how-to-create-a-shape-by-using-a-pathgeometry.md)

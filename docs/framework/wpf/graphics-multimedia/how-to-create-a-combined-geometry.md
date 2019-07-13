---
title: '方法: 結合したジオメトリを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910095"
---
# <a name="how-to-create-a-combined-geometry"></a>方法: 結合したジオメトリを作成する
この例では、ジオメトリを結合する方法を示します。 2 つのジオメトリを結合するを使用して、<xref:System.Windows.Media.CombinedGeometry>オブジェクト。 設定の<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>結合、および設定する 2 つのジオメトリとプロパティ、 <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> 、ジオメトリをまとめて結合が方法を決定するプロパティを`Union`、 `Intersect`、 `Exclude`、または`Xor`.  
  
 2 つ以上のジオメトリから複合ジオメトリを作成するには、使用、<xref:System.Windows.Media.GeometryGroup>します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.CombinedGeometry>のジオメトリの結合モードで定義されて`Exclude`します。  両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>、 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 50 と <xref:system.windows.media.combinedgeometry.geometry2%2a> が、同じ半径の円として定義されます。  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![結果を除外組み合わせモード](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
結合したジオメトリの除外  
  
 次のマークアップで、<xref:System.Windows.Media.CombinedGeometry>の結合モードで定義されて`Intersect`します。  両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>、 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 50 と <xref:system.windows.media.combinedgeometry.geometry2%2a> が、同じ半径の円として定義されます。  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![交差の結果の結合モード](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
結合したジオメトリを交差します。  
  
 次のマークアップで、<xref:System.Windows.Media.CombinedGeometry>の結合モードで定義されて`Union`します。  両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>、 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 50 と <xref:system.windows.media.combinedgeometry.geometry2%2a> が、同じ半径の円として定義されます。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![和集合結合モードの結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
結合された Geometry の和集合  
  
 次のマークアップで、<xref:System.Windows.Media.CombinedGeometry>の結合モードで定義されて`Xor`します。  両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>、 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 50 と <xref:system.windows.media.combinedgeometry.geometry2%2a> が、同じ半径の円として定義されます。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 結合モードの結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
結合したジオメトリの Xor

---
title: '方法: 複合図形を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: de9f7972c7a51ea623c3630fe62bb48f6109317e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052899"
---
# <a name="how-to-create-a-composite-shape"></a>方法: 複合図形を作成する
この例を使用して複合図形を作成する方法を示しています。<xref:System.Windows.Media.Geometry>オブジェクトとそれらを表示を使用して、<xref:System.Windows.Shapes.Path>要素。 次の例では、 <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.EllipseGeometry>と<xref:System.Windows.Media.RectangleGeometry>を併用、<xref:System.Windows.Media.GeometryGroup>複合図形を作成します。 ジオメトリを使用して描画し、<xref:System.Windows.Shapes.Path>要素。  
  
## <a name="example"></a>例  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 前の例で作成した図を次に示します。  
  
 ![GeometryGroup を使用して作成された複合ジオメトリ](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
複合ジオメトリ  
  
 使用して多角形と曲線のセグメントを持つ図形などのより複雑な図形を作成することがあります、<xref:System.Windows.Media.PathGeometry>します。 使用して図形を作成する方法を示す例については、<xref:System.Windows.Media.PathGeometry>を参照してください[PathGeometry を使用して図形を作成](how-to-create-a-shape-by-using-a-pathgeometry.md)です。  この例を使用して、画面に図形をレンダリングしますが、<xref:System.Windows.Shapes.Path>要素、<xref:System.Windows.Media.Geometry>オブジェクトがの内容を記述することも可能性があります、<xref:System.Windows.Media.GeometryDrawing>または<xref:System.Windows.Media.DrawingContext>します。 また、クリップのヒット テストも使用可能性があります。  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](https://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。

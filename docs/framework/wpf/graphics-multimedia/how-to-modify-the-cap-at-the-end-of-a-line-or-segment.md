---
title: '方法: 直線または線分の終点のキャップを変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916130"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>方法: 直線または線分の終点のキャップを変更する
この例は、開い<xref:System.Windows.Shapes.Shape>ている要素の先頭または末尾にある図形を変更する方法を示しています。 開い<xref:System.Windows.Shapes.Shape>ているの先頭でキャップを変更するには、 <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>そのプロパティを使用します。 開い<xref:System.Windows.Shapes.Shape>ているの端にあるキャップを変更するには<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> 、そのプロパティを使用します。 使用可能なラインキャップを表示するに<xref:System.Windows.Media.PenLineCap>は、列挙体を参照してください。  
  
> [!NOTE]
> このプロパティは<xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Polyline>、、、または開い<xref:System.Windows.Shapes.Path>ている要素など、開いている図形にのみ影響します。  
  
 次の例では<xref:System.Windows.Shapes.Polyline> 、4つの要素を描画し、それぞれの端に異なる形状のセットを使用します。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 この例は、大規模なサンプルに含まれています。完全なサンプルについては、「 [Shape Elements sample](https://go.microsoft.com/fwlink/?LinkID=160037)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>

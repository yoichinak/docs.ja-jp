---
title: '方法: ポリライン要素を使用してポリラインを描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934957"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>方法: ポリライン要素を使用してポリラインを描画する
この例では、 <xref:System.Windows.Shapes.Polyline>要素を使用して、接続された一連の線であるポリラインを描画する方法を示します。  
  
 ポリラインを描画するには、 <xref:System.Windows.Shapes.Polyline>要素を作成し<xref:System.Windows.Shapes.Polyline.Points%2A> 、そのプロパティを使用して図形の頂点を指定します。 最後に、プロパティ<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティを使用して、線の輪郭を記述します。これは、ストロークのない線が非表示になっているためです。  
  
> [!NOTE]
> 要素は閉じた図形<xref:System.Windows.Shapes.Shape.Fill%2A>ではないため、図形のアウトラインを意図的に閉じた場合でも、プロパティは効果がありません。 <xref:System.Windows.Shapes.Polyline> を使用して<xref:System.Windows.Shapes.Shape.Fill%2A>閉じた図形を作成するには、要素を<xref:System.Windows.Shapes.Polygon>使用します。  
  
 次の例では<xref:System.Windows.Shapes.Polyline> 、内に<xref:System.Windows.Controls.Canvas>2 つの要素を描画します。  
  
## <a name="example"></a>例  
 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]は、ポイントの有効な構文は、コンマで区切られた x 座標と y 座標のペアのスペースで区切られたリストです。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 この例では、 <xref:System.Windows.Controls.Canvas>を使用して、ポリラインを格納していますが、テキスト以外のコンテンツをサポート<xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control>するポリライン要素 (および他のすべての図形要素) を使用することもできます。  
  
 この例は、大規模なサンプルに含まれています。完全なサンプルについては、「 [Shape Elements sample](https://go.microsoft.com/fwlink/?LinkID=160037)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [図形要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)

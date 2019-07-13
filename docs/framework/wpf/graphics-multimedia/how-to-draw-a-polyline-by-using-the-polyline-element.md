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
ms.openlocfilehash: 4f55ecc206be0ef4947923047e796c36131c70ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003211"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>方法: ポリライン要素を使用してポリラインを描画する
この例を使用して一連の接続線、多角形を描画する方法を示しています、<xref:System.Windows.Shapes.Polyline>要素。  
  
 ポリラインを描画するために作成、<xref:System.Windows.Shapes.Polyline>要素と使用してその<xref:System.Windows.Shapes.Polyline.Points%2A>図形の頂点を指定するプロパティ。 最後に、使用して、<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>線なしの行が表示されないため、ポリラインを記述するプロパティが説明します。  
  
> [!NOTE]
>  <xref:System.Windows.Shapes.Polyline>要素は、閉じた図形ではありません、<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティも何も起こりません、図形の輪郭を意図的に閉じた場合でもです。 閉じた図形を作成する、<xref:System.Windows.Shapes.Shape.Fill%2A>を使用して、<xref:System.Windows.Shapes.Polygon>要素。  
  
 次の例では、2 つの描画<xref:System.Windows.Shapes.Polyline>内の要素を<xref:System.Windows.Controls.Canvas>します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ポイントの有効な構文がコンマで区切られた x 座標と y 座標のペアのスペースで区切られた一覧を示します。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 この例を使用しますが、<xref:System.Windows.Controls.Canvas>ポリラインを格納する際ポリライン要素 (およびその他のすべての図形要素) のいずれか<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。  
  
 この例より大きなサンプルの一部です。サンプル全体については、次を参照してください。 [Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
